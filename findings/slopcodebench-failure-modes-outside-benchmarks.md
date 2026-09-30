---
title: "SlopCodeBench: failure modes outside SWE benchmarks (and open questions)"
type: finding
status: draft
related_sources:
  - "[[slopcodebench-coding-agents-degrade-long-horizon]]"
added: 2026-09-30
tags:
  - swe-agents
  - benchmarks
  - failure-modes
  - open-questions
  - issue-trackers
  - specmine
---

# SlopCodeBench: failure modes outside SWE benchmarks (and open questions)

## Claim

**From the paper (supported):** Agentic coding agents that look competent on single-shot or heavily constrained iterative SWE benchmarks still fail under realistic iterative extension: they rarely solve evolving specs end-to-end, and when they pass checkpoints their own code **structurally erodes** and becomes **more verbose** over time—more so and faster than typical human repository histories. That gap is a concrete failure mode for using SWE agents **outside** benchmark setups.

**Not claimed (exploration only):** Links to issue-tracker–based agentic reasoning, or to the MSR SpecMine Challenge, are open questions for this thesis—not findings asserted by SlopCodeBench.

## Evidence

From [[slopcodebench-coding-agents-degrade-long-horizon]] (arXiv:2603.24755):

- Benchmark forces agents to extend **their own** prior workspace under evolving external contracts (36 problems / 196 checkpoints); no prescribed internals, no visible tests.
- No evaluated agent fully solves any problem; best strict checkpoint pass rate **14.8%**.
- Structural erosion rises in **77%** of trajectories; verbosity in **75.5%**.
- vs 473 Python repos: agent code **2.3×** more verbose, **2.0×** more eroded; per-checkpoint growth ~**7×** / ~**5×** faster than human medians.
- Quality-aware prompts cut initial slop (up to ~⅓) but **do not** slow degradation rates.

## Caveats

- Paper evaluates a **Python track** of a language-agnostic design; harnesses are native CLI agents, not all frameworks.
- Erosion/verbosity are specific operationalizations (CC-mass concentration; AST-grep + clone density)—not full maintainability.
- Human comparison is a sampled commit panel, not matched task trajectories.
- Thesis connections below are **hypotheses / questions**, not paper results.

## Next steps

Open questions to explore (do not treat as claims):

1. **Issue trackers ↔ agentic reasoning:** Could structured issue/spec history (acceptance criteria, linked PRs, design discussions) reduce the unconstrained early decisions that SlopCodeBench shows compounding into erosion/verbosity? Or surface when an architecture must be rewritten before checkpoint failure cascades?
2. **MSR SpecMine Challenge:** Do SpecMine-style mined specifications / evolution patterns align with SlopCodeBench's checkpointed requirement growth? Could SpecMine artifacts supply or evaluate the kind of evolving external contracts SCBench uses?
3. Practical: skim SCBench problem list vs SpecMine outputs; note overlap with issue-driven SWE workflows; decide whether a short lit note or experiment sketch is warranted.
