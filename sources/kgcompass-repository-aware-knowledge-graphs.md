---
title: "KGCompass: Repository-Aware Knowledge Graphs for Software Repair"
type: source
url: https://arxiv.org/abs/2503.21710
authors:
  - Boyang Yang
  - Jiadong Ren
  - Shunfu Jin
  - Yang Liu
  - Feng Liu
  - Bach Le
  - Haoye Tian
year: 2025
arxiv_id: "2503.21710"
added: 2026-10-01
updated: 2026-10-01
tags:
  - knowledge-graphs
  - issue-trackers
  - bug-localization
  - swe-bench
  - coding-agents
  - entity-extraction
---

# KGCompass

**Prefer the paper and code.** Closest published system to linking **issues/PRs ↔ code entities** in one KG for repository-level repair on SWE-bench Lite.

- arXiv: https://arxiv.org/abs/2503.21710 · [HTML v2](https://arxiv.org/html/2503.21710v2) · [PDF](https://arxiv.org/pdf/2503.21710)
- Code (official): https://github.com/GLEAM-Lab/KGCompass
- Mirror/demo: https://github.com/scalytics/KGCompass

## Deep-dive: KG construction (paper §3.1 + GLEAM-Lab code)

### 1. Graph schema (concrete Neo4j)

**Node labels in code** (`kgcompass/knowledge_graph.py`):

| Label | Role | Key properties |
| --- | --- | --- |
| `:Issue` | Issues **and** PRs (unified); special `id='root'` for the target bug report | `id`, `title`, `content`, `created_at`, `state`, `is_pr`, `type`, `name`, `embedding` |
| `:File` | Source file | `path` |
| `:Directory` | Path hierarchy | `path` |
| `:Class` | AST class | `name`, `file_path`, `start_line`, `end_line`, `source_code`, `doc_string`, `embedding`, `short_name` |
| `:Method` | AST function/method (also globals/vars in some paths) | `name`, `signature`, `file_path`, `start_line`, `end_line`, `source_code`, `doc_string`, `embedding` |
| `:Commit` | Referenced/historical commits | `id` (+ message usage when linking) |
| `:Experience` | Prior repair-experience snippets from commit messages | `id`, text fields |
| `:Documentation` | Selected doc files linked into the graph | `id` |

Paper high-level phrasing: repository artifacts = issues/PRs; code entities = files, classes, functions. Code additionally has Directory/Commit/Experience/Documentation. **No separate `:Comment` or `:PullRequest` labels** — PRs are `:Issue` with `is_pr=true`.

**Edges:** almost all are a single Neo4j type `[:RELATED]` with a string `description` and numeric `weight`. Bidirectional pairs observed in code:

- Containment: `contains directory/file/class/method` ↔ `contained in …`
- Issue↔artifact: `points to issue/file/method/class/commit/…` ↔ `referenced by issue` / `supports issue` / …
- Code refs: `calls method` ↔ `called by method`
- Commit edits: `modified file/method` ↔ `modified by commit`
- Experience/docs: `mentions file` ↔ `mentioned by …`

Paper also states AST yields “import and attribute references”; in released code, **imports are used to resolve call targets** (`MethodCallVisitor`), and the persisted code→code edge description found is **`calls method`**, not separate `imports`/`attribute` edge strings.

### 2. How issues / PRs / comments are ingested

1. Target bug text → root `:Issue {id:'root'}` with full `title`+`content` and **jina-embeddings-v2-base-code** embedding of `title\ncontent`.
2. Related GitHub issues/PRs fetched (PyGithub / search; Django also via Trac). Time-safe filter: only artifacts with `created_at` before instance `created_at` (paper: removed **24.0%** of initially mined artifacts).
3. Each issue/PR stored as one `:Issue` node with **full title+body text** (`content`) **and** an embedding — not links-only.
4. **Comments:** paper §3.1 says regex runs on “issue descriptions, comments, and pull request elements”. **Current GLEAM-Lab code explicitly excludes discussion comments** (`fl.py`: “Discussion comments are excluded for all issue/PR artifacts… Even pre-cutoff comments can contain maintainer-provided localization hints”). No Comment nodes.
5. **PRs:** same `:Issue` node; additionally, PR file diffs map changed line ranges → enclosing class/method via AST and create **strong** `points to method/class/file` links.

### 3. Named entities from issue text?

**Not SoftNER / LLM NER / classical NER.** Template **regex** extractors link textual mentions to existing code nodes:

- File paths: patterns like `` `path.py` `` / relative `.py` paths (`TextAnalyzer`, `get_python_files_from_content`)
- Issue/PR numbers: `#(\d+)`, GitHub/Django URLs
- Symbols: Sphinx roles `:func:`…``, backticks, dotted names, `foo()`, stack-trace file/line/in-method patterns, snippet AST refs (`get_reference_functions_from_text`, `SPHINX_SYMBOL_RE`, etc.)
- Resolved against repo filesystem / qualified-name→path heuristics / KG file search; then `link_issue_to_file` / `link_method_to_issue` / `link_class_to_issue`

So “entities” extracted are **code identifiers and tracker IDs**, not architectural types (component, decision, constraint, …).

### 4. Code entity extraction

- **Python (primary / SWE-bench):** stdlib **`ast`** (`PythonParser` in `language_factory.py`) — classes, methods, globals; imports via `ast.Import`/`ImportFrom`; calls via `MethodCallVisitor`.
- **Also:** Java (`javalang`), C/C++ (`libclang`) adapters; paper claims language-agnostic core with thin parsers.
- **Not** LSP / tree-sitter in the main Python path.
- Directory tree walk builds Directory→File containment for the whole repo snapshot at `base_commit`.

### 5. Multi-hop path construction / retrieval at inference

1. Project Neo4j GDS graph over RELATED edges with weights.
2. From `root`, run **`gds.allShortestPaths.dijkstra.stream`** (path cost = sum of edge weights).
3. Rank candidates with paper Eq. (1) / code:  
   \(S(f)=\beta^{l(f)}\cdot(\alpha\cdot\cos_{norm}+(1-\alpha)\cdot\mathrm{lev})\), with **`α=VECTOR_SIMILARITY_WEIGHT=0.3`**, **`β=DECAY_FACTOR=0.6`** (`config.py`). Embeddings: jina-embeddings-v2-base-code; Levenshtein via APOC on root text vs method/class `source_code`.
4. Take **top 15 KG** functions + **up to 5 LLM** locations → ≤20 candidates (`CANDIDATE_LOCATIONS_MAX`).
5. Repair prompt includes each candidate’s **`relationship_path`**: typed hop chain issue→…→function (Figure 5 in paper).
6. Empirics (paper RQ-2): of successfully localized GT functions, only **10.3%** are 1-hop; **89.7%** need ≥2 hops. Intermediate nodes: files 72.4%, functions 16.0%, PRs 7.1%, issues 4.5%.

### 6. Limitations relevant to architectural entities

- Schema is **fault-location oriented** (file/class/method + tracker artifacts), not architecture (no component/service/module API, ADR, constraint, interface, or decision nodes).
- Issue↔code linking is **regex mention + PR diff mapping**, not vocabulary/ontology linking or SoftNER-style entity typing.
- **Comments disabled** in current public pipeline → loses threaded design discussion that often carries architectural rationale.
- Call graph is **static, heuristic** (import-resolved AST calls); incomplete for dynamic/architectural “uses”.
- Directory nodes exist but are mostly filesystem scaffolding, not logical architecture.
- Goal is SWE-bench **repair**, not a shared human–agent architectural vocabulary.

## Earlier key points (results)

- Hybrid localization + path-guided patching + test ranking.
- Reported SWE-bench Lite (paper v2, Claude-4 Sonnet): **58.3%** Resolved, **83.6%** file / **56.0%** function Acc, ~**$0.2**/bug; large lifts vs pure-LLM baselines.
- Explicit contrast to RepoGraph: adds issue/PR nodes and path-guided repair.

## Relevance to thesis

Strong evidence that **issue↔code multi-hop graphs** beat text-only localization for agents. Gap vs thesis idea: linking is for *fault location and patches*, not for extracting a shared architectural vocabulary (constraints, decisions) for human–agent dialogue. Mention extraction is regex/template-based, not full SoftNER-style NER. Current code’s **no-comments** policy further weakens capture of architectural rationale in tracker threads.
