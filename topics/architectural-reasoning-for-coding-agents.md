---
title: "Architectural reasoning for coding agents: thesis framing"
type: topic
status: working
added: 2026-09-30
tags:
  - architectural-reasoning
  - coding-agents
  - thesis-framing
---

# Architectural reasoning for coding agents

## Main research question

**How might we improve architectural reasoning such that agents write better code?**

Here, architectural reasoning means recovering and making decisions about structure, boundaries, dependencies, and future change—not only satisfying the next test.

## Directions

1. **Issue-tracker grounding.** Systematic use of discussions, issue descriptions, and PRs may expose the decisions and trade-offs behind a codebase. Hypothesis: grounding an agent in this history improves architectural reasoning. The complementary problem is operational: agents often do not use issue trackers as they should, so this is not purely a training-data problem; retrieval, task workflow, and decision-use matter too. See [[issue-tracker-grounding-for-architectural-reasoning]] and [[slopcodebench-failure-modes-outside-benchmarks]].
2. **Planning and specification.** Architectural reasoning may also improve through more thorough planning or spec-driven development. SlopCodeBench supplies a long-horizon erosion test; SpecMine supplies real specification histories and spec–code links. See [[slopcodebench-respecification-at-every-step]], [[specmine-large-scale-corpus-of-spec-driven-development-artifacts]], and [[slopcodebench-coding-agents-degrade-long-horizon]].

## Framing

Treat issue history and specifications as complementary records of intent: issues/PRs capture negotiated rationale, while specs make intended structure and acceptance criteria explicit. Evaluate both architectural decisions and downstream code quality, not just task completion.

## Related mechanisms

Issue-entity extraction and code KGs: [[issue-tracker-entities-and-code-knowledge-graph]], [[issue-entity-code-kg-related-work]], [[issue-entity-kg-gap-vs-architectural-vocabulary]].

ADR templates as decision schemas: [[architecture-decision-record]].
