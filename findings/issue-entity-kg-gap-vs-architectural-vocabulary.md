---
title: "Issue→code KGs optimize localization; architectural shared vocabulary is underserved"
type: finding
status: literature-grounded
related_sources:
  - "[[softner-stackoverflow-ner]]"
  - "[[distalaner-oss-named-entity-recognition]]"
  - "[[kgcompass-repository-aware-knowledge-graphs]]"
  - "[[repograph-repository-level-code-graph]]"
  - "[[locagent-graph-guided-code-localization]]"
added: 2026-10-01
tags:
  - architectural-reasoning
  - issue-trackers
  - knowledge-graphs
  - gap
---

# Issue→code KGs optimize localization; architectural shared vocabulary is underserved

## Claim

Peer-reviewed work from 2018–2026 strongly supports (a) software NER on developer text and (b) graphs that connect issues to code for **localization/repair**, but it does **not** yet treat extracted issue-tracker entities as a durable **shared language** for architectural reasoning between users and coding agents.

## Grounding

- SoftNER and DistALANER establish extractable software entities, yet inventories emphasize APIs/packages/code tokens (and ops entities), not constraints, boundaries, or decisions ([[softner-stackoverflow-ner]], [[distalaner-oss-named-entity-recognition]]).
- KGCompass shows issue/PR↔code multi-hop graphs materially improve SWE-bench localization/repair; ~90% of its successful localizations need ≥2 hops—evidence that structured linking matters—while remaining repair-centric ([[kgcompass-repository-aware-knowledge-graphs]]).
- RepoGraph and LocAgent improve agent navigation over **code** structure; issues are entry queries, not first-class conceptual nodes for human–agent dialogue ([[repograph-repository-level-code-graph]], [[locagent-graph-guided-code-localization]]).

## Implication for thesis

The open wedge for [[issue-tracker-entities-and-code-knowledge-graph]] and [[issue-tracker-grounding-for-architectural-reasoning]] is evaluation and schema: reuse NER + issue↔code KG techniques, but measure whether a shared entity vocabulary reduces architectural ambiguity and preserves intent—not only Resolve%/Acc@k.
