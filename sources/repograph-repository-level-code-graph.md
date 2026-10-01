---
title: "RepoGraph: Repository-level Code Graph for AI Software Engineering"
type: source
url: https://arxiv.org/abs/2410.14684
authors:
  - Siru Ouyang
  - Wenhao Yu
  - Kaixin Ma
  - Zilin Xiao
  - Zhihan Zhang
  - Mengzhao Jia
  - Jiawei Han
  - Hongming Zhang
  - Dong Yu
year: 2025
arxiv_id: "2410.14684"
venue: ICLR 2025
added: 2026-10-01
tags:
  - knowledge-graphs
  - coding-agents
  - swe-bench
  - code-structure
---

# RepoGraph

**Prefer the paper and code.** Plug-in repository graph at **code-line** granularity (definition/reference nodes; invoke/contain edges) for SWE-bench-style agent and procedural repair systems.

## Key points

- **Construction.** Tree-sitter AST over Python files → keep def/ref lines; filter stdlib/third-party noise; organize as graph; retrieve *k*-hop ego-graphs around search terms.
- **Integration.** Procedural: inject subgraph context into localize/edit prompts. Agent: add `search_repograph` action (SWE-agent, AutoCodeRover, Agentless, RAG).
- **Reported.** Average ~+2–2.7 Resolve points across four baselines on SWE-bench Lite (~32.8% relative improvement claimed); Agentless+RepoGraph 29.67% resolve in their GPT-4o setting; also helps CrossCodeEval completion.
- **Scope.** Pure **code** structure—no issue/PR nodes (KGCompass later critiqued this gap).

## Relevance to thesis

Useful substrate for mapping named entities *onto* structural neighborhoods once entities are extracted. Does not itself do issue-tracker NER or user-facing shared language; complements [[kgcompass-repository-aware-knowledge-graphs]] and [[locagent-graph-guided-code-localization]].

## Links

- arXiv: https://arxiv.org/abs/2410.14684 · [HTML](https://arxiv.org/html/2410.14684) · [PDF](https://arxiv.org/pdf/2410.14684)
- ICLR: https://proceedings.iclr.cc/paper_files/paper/2025/hash/4a4a3c197deac042461c677219efd36c-Abstract-Conference.html
- Code: https://github.com/ozyyshr/RepoGraph
