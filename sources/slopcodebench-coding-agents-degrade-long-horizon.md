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

# SlopCodeBench: Benchmarking How Coding Agents Degrade Over Long-Horizon Iterative Tasks

## Summary

Software development is iterative, yet agentic coding benchmarks hide design issues through their single-shot setup. Recent iterative benchmarks attempt to remedy this but heavily constrain an agent's design decision space, making it impossible to faithfully measure how their decisions shape future extensions. The authors introduce **SlopCodeBench** (SCBench): 36 problems and 196 checkpoints where agents repeatedly extend their own solutions. Evolving specifications demand architectural decisions but leave internal structure to the agent. They measure **structural erosion** (concentrated complexity) and **verbosity** (redundant code). Across 15 coding agents, no agent fully solves any problem end-to-end; the best agent passes 14.8% of checkpoints. Quality degrades across checkpoints (erosion rises in 77% of trajectories; verbosity in 75.5%). Versus 473 open-source Python repos, agent code is 2.3× more verbose and 2.0× more eroded. Explicit quality guidance reduces initial verbosity/erosion by up to a third without slowing degradation rates.

## Key points

- **Failure mode targeted:** single-shot / heavily constrained iterative SWE benchmarks hide whether early design decisions remain extensible under future change—the practical failure when using agents outside benchmarks.
- **Design principles:** no prescribed internal interfaces; no visible test suite; black-box, language-agnostic external contracts (CLI/API only). Agent workspace carries forward; agent pays for its own early choices.
- **Metrics:** structural erosion = share of complexity mass in high-CC functions (CC > 10); verbosity = fraction of LOC that are AST-grep-flagged or structural clones.
- **Results:** SOTA strict solve rate 14.8% (GPT 5.5); no problem fully solved; cost per checkpoint grows ~2.2× while relative lines changed fall; agents accumulate verbosity ~7× and erosion ~5× faster than human git histories.
- **Prompting:** anti-slop / plan-first improve initial quality (up to ~1/3 less verbosity/erosion) but do not stop iterative degradation; average +12.1% cost/checkpoint and slight correctness drop.
- **Artifact:** problems/code/leaderboard at https://www.scbench.ai

## Relevance to thesis

Targets the **actual point of failure when using SWE agents outside of benchmarks**: iterative extension under evolving specs, where local correctness can persist while architecture erodes. Worth exploring whether this connects to:

1. **Agentic reasoning improvements via issue trackers** — e.g., whether structured issue/spec history could constrain or surface design decisions that SlopCodeBench leaves unconstrained, or whether issue-tracker grounding reduces erosion/verbosity under long-horizon edits.
2. **MSR SpecMine Challenge** — e.g., whether mined specs / specification evolution patterns relate to SlopCodeBench's checkpointed evolving requirements, or whether SpecMine-style artifacts could inform better iterative agent evaluation or scaffolding.

These links are **exploratory open questions**, not established claims from the paper.

## Quotes / excerpts

> "Software development is iterative, yet agentic coding benchmarks hide design issues through their single-shot setup."

> "SlopCodeBench provides the first measurement of code degradation under iterative extension, revealing that agents pass checkpoints while producing code that erodes and bloats with each turn."

> "Existing coding-agent benchmarks systematically undermeasure this failure mode, evaluating models once against complete task specifications. They measure whether an agent can produce correct code for the current specification, not whether that code remains extensible under future change."

## Links

- abs: https://arxiv.org/abs/2603.24755
- pdf: https://arxiv.org/pdf/2603.24755
- project: https://www.scbench.ai
