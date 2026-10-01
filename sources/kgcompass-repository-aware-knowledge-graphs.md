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
tags:
  - knowledge-graphs
  - issue-trackers
  - bug-localization
  - swe-bench
  - coding-agents
---

# KGCompass

**Prefer the paper and code.** Closest published system to linking **issues/PRs ↔ code entities** in one KG for repository-level repair on SWE-bench Lite.

## Key points

- **KG schema.** Nodes: issues, PRs, files, classes, functions. Edges: AST containment/calls/imports/attrs + regex-extracted mentions from issue/PR text to code nodes. Time-safe: only artifacts before the target issue’s `created_at`.
- **Use.** Score functions by embedding + string similarity × path-length decay; hybrid top-15 KG + up to 5 LLM locations → path-guided patch prompts → test ranking.
- **Reported (SWE-bench Lite, paper).** With Claude-4 Sonnet: 58.3% Resolved, 83.6% file / 56.0% function Acc, ~$0.2/bug; large lifts vs pure-LLM baselines. Among successfully localized bugs, **89.7%** need multi-hop paths (only ~10% are 1-hop from the issue). Intermediate path nodes are mostly files/functions; ~12% are issues/PRs.
- **Explicit contrast to RepoGraph.** Authors argue prior code-only graphs underuse repository artifacts; KGCompass adds issue/PR nodes and path-guided repair.

## Relevance to thesis

Strong evidence that **issue↔code multi-hop graphs** beat text-only localization for agents. Gap vs thesis idea: linking is for *fault location and patches*, not for extracting a shared architectural vocabulary (constraints, decisions) for human–agent dialogue. Mention extraction is regex/template-based, not full SoftNER-style NER.

## Links

- arXiv: https://arxiv.org/abs/2503.21710 · [HTML](https://arxiv.org/html/2503.21710v1) · [PDF](https://arxiv.org/pdf/2503.21710)
- Code: https://github.com/GLEAM-Lab/KGCompass
