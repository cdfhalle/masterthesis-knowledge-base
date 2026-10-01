---
title: "Related work: issue-tracker NER, entity→code linking, and software KGs"
type: note
status: related-work
added: 2026-10-01
tags:
  - architectural-reasoning
  - issue-trackers
  - knowledge-graphs
  - named-entity-recognition
  - related-work
---

# Related work: issue entities → code / shared KG

Companion to the idea note [[issue-tracker-entities-and-code-knowledge-graph]]. Goal of that idea: extract named entities from issues/discussions/PRs, map them to code, and/or build a KG so agents and users share a coherent language for architectural reasoning.

## Approach clusters

### 1. Software-domain NER (text side)

- **SoftNER / StackOverflowNER** (ACL 2020): 20 fine-grained software entity types (Class, Function, Library, Variable, Application, …); in-domain BERTOverflow; F1 ~79 on SO, ~61 when applied to GitHub readme/issues. See [[softner-stackoverflow-ner]].
- **DistALANER** (2024): distant+active learning NER for OSS bug reports / CQAs (packages, OS, commands, errors, …); Ubuntu bugs → Linux/Fedora/Ubuntu QA transfer; also shows NER helps relation extraction. See [[distalaner-oss-named-entity-recognition]].
- Earlier: Ye et al. SANER 2016 (S-NER; 5 software entity types on SO). Medium/blog pipelines for GitHub-issue fields exist but are not peer-reviewed corpora.

**Takeaway:** NER for *code-ish tokens and product entities* is established; schemas rarely target architectural concepts (boundaries, constraints, decisions, invariants).

### 2. Issue/PR ↔ code linking & bug localization via graphs

- **KGCompass** (2025): Neo4j KG joining **issues + PRs** with files/classes/functions; regex mention linking + AST edges; multi-hop paths for SWE-bench Lite localization/repair; ~90% of successful localizations need ≥2 hops. Closest prior art to “issue entities → code KG.” See [[kgcompass-repository-aware-knowledge-graphs]].
- **KGBugLocator** (ICPC 2020): code KG + bi-directional attention for IR-based bug localization (file ranking from bug reports).
- **BugRadar** (IST 2023): TriGraph (structure from reports + source) + hyperbolic link prediction for file localization.
- **KEPT** (FSE 2025): KG from project docs + historical code injected into an LLM for bug localization ([ACM](https://dl.acm.org/doi/10.1145/3729356); [code](https://github.com/keptmodel/KEPT)).

**Takeaway:** Linking is optimized for *fault location / repair success*, not for a durable shared vocabulary with users.

### 3. Repo graphs for coding agents (structure side)

- **RepoGraph** (ICLR 2025): line-level def/ref graph; plug-in for Agentless / SWE-agent / etc. on SWE-bench. See [[repograph-repository-level-code-graph]].
- **CodexGraph** (2024): code symbols in Neo4j; Cypher queries by LLM agents ([arXiv](https://arxiv.org/abs/2408.03910)).
- **LocAgent** (2025): heterogeneous code graph (contain/import/invoke/inherit) + agent tools for multi-hop localization; Loc-Bench. See [[locagent-graph-guided-code-localization]].
- Vault-adjacent: [[swe-debate-competitive-multi-agent-debate]] (dependency-graph fault-propagation traces + debate).

**Takeaway:** Strong *code* graphs for agents; issue/discussion entities are usually queries or entry points, not first-class shared terms.

### 4. NL↔code retrieval (linking without explicit NER)

- CodeBERT / related NL-code dual encoders: semantic retrieval (query ↔ snippet), not typed entity linking.
- Heuristic/mention extractors (as in KGCompass regex) bridge text spans to symbols without a full NER schema.

## Gaps vs the thesis idea

| Desired | What literature mostly does |
| --- | --- |
| Entities = components, constraints, decisions, actors | Entities = APIs, files, packages, error codes, code tokens |
| Shared language for *user + agent* architectural talk | Graphs mainly shrink agent search / boost Resolve% |
| Map discussion entities → stable code anchors + rationale | Map bug text → buggy file/function for patching |
| Evaluate ambiguity reduction / decision quality | Evaluate localization Acc / SWE-bench Pass |
| GitHub issues + discussions + PR descriptions as corpus | SO posts, Ubuntu bugs, or issue *as query only* |

Closest existing stack to build on: SoftNER/DistALANER-style extraction **plus** KGCompass-style issue/PR↔code edges **plus** RepoGraph/LocAgent structural graphs—then reorient evaluation toward architectural grounding ([[issue-tracker-grounding-for-architectural-reasoning]]).

## Optional next reads (not filed as sources yet)

- Ye et al., SANER 2016 — Software-specific NER (5 types): https://doi.org/10.1109/SANER.2016.10
- BugRadar — https://doi.org/10.1016/j.infsof.2023.107274
- KEPT (FSE 2025) — https://dl.acm.org/doi/10.1145/3729356
- CodexGraph — https://arxiv.org/abs/2408.03910
