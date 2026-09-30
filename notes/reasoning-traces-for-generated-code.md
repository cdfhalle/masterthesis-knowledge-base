---
title: "Reasoning traces tied to generated code"
type: note
status: idea
added: 2026-09-30
tags:
  - architectural-reasoning
  - coding-agents
  - specifications
  - idea
---

# Reasoning traces tied to generated code

## Idea

Tie an agent's architectural reasoning directly to the generated code and its requirements. For each function or boundary, record the requirement, invariant, or trade-off that justifies keeping it stable; mark code as changeable when no current requirement depends on it. A later agent can then distinguish intentional structure from accidental implementation detail instead of rewriting both indiscriminately.

## Exploration

Represent the links at function/class or change granularity and test whether a later agent can use them to preserve required behavior while safely simplifying or relocating unconstrained code. Combine issue/PR rationale with specification and acceptance-criteria links: [[architectural-reasoning-for-coding-agents]], [[issue-tracker-grounding-for-architectural-reasoning]], [[slopcodebench-respecification-at-every-step]].

## Caveats

The trace can become stale, decorative, or overconfident. Evaluate trace accuracy, update cost, and whether linked rationale actually changes later edits—not just whether the trace exists.
