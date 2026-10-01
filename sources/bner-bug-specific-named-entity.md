---
title: "Recognizing software bug-specific named entity in software bug repository (BNER)"
type: source
url: https://doi.org/10.1145/3196321.3196335
authors:
  - Cheng Zhou
  - Bin Li
  - Xiaobing Sun
  - Hongjing Guo
year: 2018
venue: ICPC 2018
added: 2026-10-01
tags:
  - named-entity-recognition
  - bug-reports
  - mozilla
  - eclipse
---

# BNER (ICPC 2018)

**Prefer the paper.** First dedicated bug-report NER: free-form Bugzilla-style text (code, abbreviations, SE vocab) on Mozilla and Eclipse corpora; CRF + word embeddings (BNER).

## Key points

- **Text.** Bug repository reports (Mozilla, Eclipse)—not Stack Overflow.
- **Entities.** Bug-specific named entities (paper taxonomy includes Component, GUIClass, Method, Variable, Parameter, Version, and related bug-report entities).
- **Method.** CRF with word embeddings; baseline corpora + cross-project NER evaluation.
- **Follow-ups.** DBNER (JSS 2020) upgrades to attention BiLSTM-CRF; ASE 2022 Li et al. add joint entity+relation extraction on bug reports.

## Relevance to thesis

Closest classical peer-reviewed **bug-tracker NER** line (Yangzhou U.). Entity schema is bug/fix-oriented (components, methods, symptoms), not architectural vocabulary—but text source matches issue-tracker prose.

## Links

- ACM: https://doi.org/10.1145/3196321.3196335
- Conference: https://conf.researchr.org/details/icpc-2018/icpc-2018-Technical-Research/4/Recognizing-Software-Bug-Specific-Named-Entity-in-Software-Bug-Repository
