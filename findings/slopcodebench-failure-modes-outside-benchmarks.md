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

# SlopCodeBench: failure modes outside benchmarks

## Claim (from paper)

Agents that look fine on single-shot / constrained SWE benchmarks still fail under iterative extension: rare end-to-end solves; passing checkpoints while **structural erosion** and **verbosity** grow faster than in human repos. That is a real outside-benchmark failure mode. See figures on [[slopcodebench-coding-agents-degrade-long-horizon]].

## Evidence (anchors only)

- 36 problems / 196 checkpoints; best strict pass **14.8%**; no full solves.
- Erosion ↑ 77%, verbosity ↑ 75.5% of trajectories; vs humans **2.3×** / **2.0×** worse; ~7× / ~5× faster growth.
- Quality prompts help the start, not the slope.

## Open questions (not paper claims)

1. Can issue-/spec-tracker history constrain early design choices that compound into erosion?
2. Do SpecMine evolution patterns align with SCBench-style checkpointed requirement growth?

## Caveats

Python-track eval; CC-mass / AST-grep+clone metrics; human panel ≠ matched tasks.
