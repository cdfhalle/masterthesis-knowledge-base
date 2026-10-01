---
title: "Towards the identification of bug entities and relations in bug reports"
type: source
url: https://doi.org/10.1007/s10515-022-00325-1
authors:
  - Bin Li
  - Ying Wei
  - Xiaobing Sun
  - Lili Bo
  - Dingshan Chen
  - Chuanqi Tao
year: 2022
venue: Automated Software Engineering
added: 2026-10-01
tags:
  - named-entity-recognition
  - relation-extraction
  - bug-reports
---

# Bug entities + relations (ASE journal 2022)

**Prefer the paper.** Joint NER + relation extraction on Bugzilla-style reports (Mozilla/Eclipse). Defines 8 relation types between bug entities; RNN + SDP-RNN; reported F1 ~79.3% entities / ~63.8% relations.

## Key points

- **Text.** Bug reports (Bugzilla Mozilla/Eclipse examples in paper).
- **Method.** RNN for entities; shortest-dependency-path RNN for relations; builds toward structured bug knowledge / linking reports.
- **Predecessor.** Chen et al., IBF 2019 workshop short paper on automatic bug entity+relation identification.

## Relevance to thesis

Shows NER is not enough—**relations among issue entities** matter for retrieval/comprehension. Closest published “issue KG fragment” from text alone (before KGCompass’s issue↔code graph).

## Links

- Springer: https://doi.org/10.1007/s10515-022-00325-1
- IBF 2019 precursor: https://doi.org/10.1109/IBF.2019.8665494
