---
title: "Improving software bug-specific named entity recognition with deep neural network (DBNER)"
type: source
url: https://doi.org/10.1016/j.jss.2020.110572
authors:
  - Cheng Zhou
  - Bin Li
  - Xiaobing Sun
year: 2020
venue: Journal of Systems and Software
added: 2026-10-01
tags:
  - named-entity-recognition
  - bug-reports
  - bilstm-crf
---

# DBNER (JSS 2020)

**Prefer the paper.** Deep upgrade of BNER: attention-based BiLSTM-CRF with word/orthographic/POS/gazetteer features and document-level attention for consistent tags across a bug report.

## Key points

- **Text.** Bug reports (expanded beyond Mozilla/Eclipse; paper reports four projects including Apache/Kernel in evaluations).
- **Method.** Attention BiLSTM-CRF; reported ~91% average F1 in-project and ~84% cross-project (paper figures).
- **Continuity.** Same bug-entity taxonomy line as ICPC 2018 BNER.

## Relevance to thesis

Strongest peer-reviewed **supervised deep NER on bug-tracker text** before DistALANER’s distant-supervision scale-up. Still not GitHub Issues API text, but same genre.

## Links

- ScienceDirect: https://doi.org/10.1016/j.jss.2020.110572
