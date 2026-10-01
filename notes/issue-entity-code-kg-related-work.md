---
title: "Related work: issue-tracker NER, entity→code linking, and software KGs"
type: note
status: related-work
added: 2026-10-01
updated: 2026-10-01
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

### 1. Software-domain NER (text side) — issue / bug / incident trackers first

**Directly on bug/incident/issue prose**

| Paper | Year | Text | GitHub issues? | Entity focus | Method |
| --- | --- | --- | --- | --- | --- |
| SoftNER / StackOverflowNER [[softner-stackoverflow-ner]] | 2020 | SO + GH readme/**issues** eval | Yes (eval transfer) | 20 code+product types | BERTOverflow + SoftNER |
| DistALANER [[distalaner-oss-named-entity-recognition]] | 2024 | Ubuntu bugs; Linux CQAs | No | 9 ops/bug types | Distant+active → BERT-CRF |
| BNER [[bner-bug-specific-named-entity]] | 2018 | Mozilla/Eclipse Bugzilla | No | Bug-specific (Component, Method, Version, …) | CRF + embeddings |
| DBNER [[dbner-bug-specific-ner-dnn]] | 2020 | Bug reports (multi-project) | No | Same BNER line | Attn BiLSTM-CRF |
| Bug entities+relations [[bug-entities-relations-ase-2022]] | 2022 | Mozilla/Eclipse bugs | No | Entities + 8 relation types | RNN / SDP-RNN |
| SoftNER *cloud incidents* [[softner-cloud-incidents-kg]] | 2021 | MS IcM incident reports | No | Open ops entities (IDs, IPs, problem type, …) | Unsup bootstrap + multi-task BiLSTM-CRF → KG |

**Software NER (adjacent corpora; transfer candidates)**

- **WikiSER** [[wikiser-software-entity-recognition]] (ASE 2023): Wikipedia Computing → 12 types / 79K entities; noise-robust BERT; eval also on SoftNER/S-NER SO sets. *Not* issue text.
- **S-NER** Ye et al. SANER 2016: 5 types on Stack Overflow social content (foundational).
- **T-FREX** [[t-frex-app-review-feature-ner]] (SANER 2024): app-review *features* as NER spans.
- **RENE** (ICSME 2020): requirement-entity extraction (LSTM-CRF + transfer) on industrial requirements—not trackers.
- **Hidden Entity Detection from GitHub** (arXiv:2501.04455, DL4KG): LLM few-shot for dataset/software **URLs in READMEs**—not issue NER.

**Takeaway:** NER for *code-ish tokens, packages, ops IDs, and product entities* on bug/incident text is established; schemas rarely target architectural concepts (boundaries, constraints, decisions, invariants). True **GitHub Issues/PR description** gold NER beyond SoftNER’s transfer eval remains thin.

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
- InfoZilla (MSR 2008): extracts *structure* (patches, stacks, code blocks) from bug reports—not typed NER.

## Gaps vs the thesis idea

| Desired | What literature mostly does |
| --- | --- |
| Entities = components, constraints, decisions, actors | Entities = APIs, files, packages, error codes, code tokens, cloud resource IDs |
| Shared language for *user + agent* architectural talk | Graphs mainly shrink agent search / boost Resolve% |
| Map discussion entities → stable code anchors + rationale | Map bug text → buggy file/function for patching |
| Evaluate ambiguity reduction / decision quality | Evaluate localization Acc / SWE-bench Pass |
| GitHub issues + discussions + PR descriptions as corpus | SO posts, Ubuntu/Bugzilla bugs, IcM incidents, or issue *as query only* |

Closest existing stack to build on: SoftNER/DistALANER/BNER-style extraction **plus** SoftNER-incidents open-schema bootstrap **plus** KGCompass-style issue/PR↔code edges **plus** RepoGraph/LocAgent structural graphs—then reorient evaluation toward architectural grounding ([[issue-tracker-grounding-for-architectural-reasoning]]).

## Ranked NER hits for issue-tracker text (2015–2026)

1. SoftNER → GitHub issues/readme transfer (ACL 2020)
2. DistALANER Ubuntu bugs (ECML-PKDD 2024)
3. BNER / DBNER Bugzilla NER (ICPC 2018 / JSS 2020)
4. Bug entities+relations (ASE 2022; IBF 2019)
5. SoftNER cloud incidents KG (ICSE-SEIP 2021 / EMSE)
6. WikiSER (ASE 2023) — transfer candidate, not issues
7. S-NER (SANER 2016) — SO foundation
8. T-FREX app-review feature NER (SANER 2024) — SE-adjacent
9. RENE requirements entities (ICSME 2020) — SE-adjacent
10. Hidden Entity Detection GitHub READMEs (2024/25) — URLs, not issue NER

**Not NER (do not overclaim):** KGCompass regex mention linking; InfoZilla structural extractors; medium/blog GitHub-issue NER demos without peer-reviewed corpora.
