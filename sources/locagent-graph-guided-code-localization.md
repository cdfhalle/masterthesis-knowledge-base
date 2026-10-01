---
title: "LocAgent: Graph-Guided LLM Agents for Code Localization"
type: source
url: https://arxiv.org/abs/2503.09089
authors:
  - Zhaoling Chen
  - Xiangru Tang
  - Gangda Deng
  - Fang Wu
  - Jialong Wu
  - Zhiwei Jiang
  - Viktor Prasanna
  - Arman Cohan
  - Xingyao Wang
year: 2025
arxiv_id: "2503.09089"
added: 2026-10-01
tags:
  - code-localization
  - knowledge-graphs
  - coding-agents
  - swe-bench
---

# LocAgent

**Prefer the paper and code.** Agent framework that indexes a repo as a **heterogeneous directed graph** (directory/file/class/function; contain/import/invoke/inherit) and exposes unified tools (`SearchEntity`, `TraverseGraph`, `RetrieveEntity`) for multi-hop localization from issue text.

## Key points

- **Motivation.** Issue text often names symptoms, not the true edit sites; multi-hop dependency traversal is required. Sparse hierarchical entity indexes (exact ID, name dict, BM25) keep indexing cheap.
- **Loc-Bench.** New localization benchmark with more feature/security/performance issues and post-cutoff GitHub data (vs SWE-Bench-Lite’s bug-heavy mix).
- **Reported.** Strong file/module/function Acc vs Agentless / SWE-agent / OpenHands / embeddings; fine-tuned Qwen-2.5-32B approaches Claude-3.5 at ~86% lower API cost in their accounting; better localization raises downstream Pass@10 on repair.
- **Comparison table in paper.** Positions vs CodexGraph, RepoGraph, RepoUnderstander, OrcaLoca on relation/node coverage and search strategy.

## Relevance to thesis

Best current reference for **graph-guided agent localization** from natural-language issues. Still treats the issue as a *query*, not as a source of durable named entities for a shared user–agent architectural lexicon. Pair with SoftNER/DistALANER for explicit entity extraction and with KGCompass for issue/PR artifact nodes.

## Links

- arXiv: https://arxiv.org/abs/2503.09089 · [HTML](https://arxiv.org/html/2503.09089v1) · [PDF](https://arxiv.org/pdf/2503.09089)
- Code: https://github.com/gersteinlab/LocAgent
