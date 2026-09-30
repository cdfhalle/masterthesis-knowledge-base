---
title: "SWE-Debate: Competitive Multi-Agent Debate for Software Issue Resolution"
type: source
url: https://arxiv.org/abs/2507.23348
authors:
  - Han Li
  - Yuling Shi
  - Shaoxin Lin
  - Xiaodong Gu
  - Heng Lian
  - Xin Wang
  - Yantao Jia
  - Tao Huang
  - Qianxiang Wang
year: 2025
arxiv_id: "2507.23348"
added: 2026-09-30
tags:
  - swe-agents
  - fault-localization
  - dependency-graphs
  - multi-agent-debate
  - reasoning-traces
---

# SWE-Debate

**Prefer the paper and code.** SWE-Debate (ICSE 2026) treats repository-level issue resolution as graph-guided fault localization followed by competitive multi-agent planning, rather than independent agent exploration alone.

## Key points

- **Dependency graph → propagation traces.** A static graph connects code entities through calls, inheritance, imports, and variable references. Issue-text/entity matching supplies entry points; breadth-first neighbor expansion and depth-limited traversal produce multiple candidate fault-propagation traces.
- **Debate over alternatives.** Agents rank diverse traces, propose modification plans from different perspectives, critique/refine competing plans, and use a discriminator to produce one consolidated plan. The paper uses three debate rounds, six chains, and five specialized agents.
- **Patch generation.** The consolidated plan initializes an MCTS-based editing agent, so the graph/debate stages act as structured localization and architectural planning before code changes.
- **Reported results.** On SWE-Bench-Verified, the paper reports 41.4% Pass@1 (207/500) with DeepSeek-V3-0324; on SWE-Bench-Lite it reports 81.67% file-level Acc@1. Ablations report −10.0 points without multiple-chain generation, −6.0 without the edit plan, and −4.2 without debate.
- **Important qualification.** These are paper-reported results, not a directly verified leaderboard submission. The paper's conclusion says “6.7% improvement,” while its Table 1 same-model comparison is 41.4% vs 38.8% (2.6 percentage points); preserve the table-level comparison when citing it.

## Why it matters for this thesis

The useful idea is not “more agents” by itself: the dependency graph externalizes **where a fault may propagate**, while debate compares competing architectural hypotheses before editing. This is a concrete instance of reasoning traces over code structure. It connects to [[reasoning-traces-for-generated-code]]: a future trace could attach each propagation edge and planned edit to requirements, invariants, issue/PR rationale, or acceptance criteria, making the trace auditable and updateable rather than merely an ephemeral chain. It also directly supports [[architectural-reasoning-for-coding-agents]] by turning issue understanding, dependency structure, and modification trade-offs into explicit intermediate artifacts.

## Limitations / questions

- The evaluation is primarily Python-only SWE-Bench-Verified/SWE-Bench-Lite, and the authors note static graphs can miss dynamic relationships.
- “Diverse agents” are different prompts over DeepSeek-V3-0324, not independently trained or heterogeneous models.
- Graph construction and multi-round debate add cost; longer traces can distract, with the paper reporting a best chain depth of five on its 75-instance SWE-Bench-Verified-S study.
- A thesis extension should test whether linking trace edges to requirements and historical rationale improves edit safety, not just localization accuracy.

## Links

- Paper (arXiv): https://arxiv.org/abs/2507.23348 · [HTML](https://arxiv.org/html/2507.23348v1) · [PDF](https://arxiv.org/pdf/2507.23348)
- Published version (ICSE 2026): https://dl.acm.org/doi/10.1145/3744916.3787810
- Code and data (official): https://github.com/YerbaPage/SWE-Debate
- Benchmark leaderboard/context: https://www.swebench.com/verified
- SWE-Bench benchmark repository: https://github.com/SWE-bench/SWE-bench
