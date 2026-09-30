---
title: "Re-specification at every step as a SlopCodeBench intervention"
type: finding
status: proposed
related_sources:
  - "[[slopcodebench-coding-agents-degrade-long-horizon]]"
  - "[[specmine-large-scale-corpus-of-spec-driven-development-artifacts]]"
added: 2026-09-30
tags:
  - swe-agents
  - benchmarks
  - iterative-coding
  - specifications
  - experiment
---

# Re-specification at every step as a SlopCodeBench intervention

## Claim

A useful intervention to test is requiring an agent to write or update an OpenSpec-style spec file before every planned change. Re-specifying intent, constraints, and acceptance criteria at each checkpoint may reduce long-horizon erosion and improve strict solve rates.

## Experiment sketch

Compare standard SlopCodeBench prompting with a treatment that requires a versioned spec before each change and evaluates spec–code consistency. Track strict checkpoint pass rate, end-to-end solves, structural erosion, verbosity, cost, and spec churn; use [[specmine-large-scale-corpus-of-spec-driven-development-artifacts]] for realistic specification patterns and evolution signals.

## Caveats

The extra writing may increase cost or verbosity, and a spec can become performative. Keep task exposure, model, tools, and budgets fixed; score both code outcomes and whether specs predict or constrain the resulting changes. See [[slopcodebench-coding-agents-degrade-long-horizon]].
