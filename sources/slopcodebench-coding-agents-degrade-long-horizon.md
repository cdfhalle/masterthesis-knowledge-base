---
title: "SlopCodeBench: Benchmarking How Coding Agents Degrade Over Long-Horizon Iterative Tasks"
type: source
url: https://arxiv.org/abs/2603.24755
authors:
  - Gabriel Orlanski
  - Devjeet Roy
  - Alexander Yun
  - Changho Shin
  - Alex Gu
  - Albert Ge
  - Dyah Adila
  - Nicholas Roberts
  - Frederic Sala
  - Aws Albarghouthi
year: 2026
arxiv_id: "2603.24755"
added: 2026-09-30
tags:
  - swe-agents
  - benchmarks
  - code-quality
  - iterative-coding
  - structural-erosion
  - verbosity
---

# SlopCodeBench

**Prefer the paper.** Below: a few anchors + figures only.

## Key points

- Agents must repeatedly extend **their own** workspace under evolving external contracts (36 problems / 196 checkpoints); no prescribed internals, tests hidden.
- No agent solves any problem end-to-end; best strict checkpoint pass **14.8%**. Erosion ↑ in 77% of trajectories; verbosity ↑ in 75.5%.
- vs 473 Python repos: agent code **2.3×** more verbose, **2.0×** more eroded; degrades ~7× / ~5× faster than human histories.
- Quality prompts cut initial slop (up to ~⅓) but **do not** stop iterative degradation.

## Figures

![[assets/slopcodebench-fig1-iterative-evaluation.png]]

![[assets/slopcodebench-fig2-solve-rates-and-cost.png]]

![[assets/slopcodebench-fig3-erosion-verbosity-trends.png]]

![[assets/slopcodebench-fig4-agents-vs-humans.png]]

![[assets/slopcodebench-fig5-prompting-does-not-stop-degradation.png]]

## Relevance

Concrete failure mode for SWE agents **outside** single-shot benchmarks. Open links to explore: issue-/spec-tracker grounding; [[msr-2027-mining-challenge]] / SpecMine evolving specs. See [[slopcodebench-failure-modes-outside-benchmarks]].

## Links

- abs: https://arxiv.org/abs/2603.24755 · pdf: https://arxiv.org/pdf/2603.24755 · project: https://www.scbench.ai
