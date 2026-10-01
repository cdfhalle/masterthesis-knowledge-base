---
title: "DistALANER: Distantly Supervised Active Learning NER for OSS"
type: source
url: https://arxiv.org/abs/2402.16159
authors:
  - Somnath Banerjee
  - Avik Dutta
  - Aaditya Agrawal
  - Rima Hazra
  - Animesh Mukherjee
year: 2024
arxiv_id: "2402.16159"
added: 2026-10-01
tags:
  - named-entity-recognition
  - bug-reports
  - distant-supervision
  - open-source
---

# DistALANER

**Prefer the paper and code.** NER framework for open-source software text (Ubuntu bug descriptions; Ubuntu/Fedora/Linux CQAs) using dictionary matching, POS heuristics, TagMe expansion, and active learning—then trains CRF/BERT-style taggers.

## Key points

- **Entity types (9).** Package, OS, organization, command, error, file extension, peripheral, software component, architecture—closer to *ops/bug* entities than SoftNER’s inline-code inventory.
- **Distance supervision.** Lookup tables from Ubuntu/Wikipedia/man pages since ~2004; Stage-1 exact match + Stage-2 distillation/expansion with limited human labels (~3.6k mentions over ~170k bugs).
- **Results (paper-reported).** BERT-CRF with human-induced silver data best among tested models; pre-LLM taggers beat zero-shot GPT-3.5/4 / BARD / UniversalNER on their recall/F1 setup; downstream relation extraction improves when using NER encoders.
- **Code.** https://github.com/NeuralSentinel/DistALANER

## Relevance to thesis

Shows how to scale NER on **bug-tracker prose** without full gold annotation—useful if mining GitHub issues at volume. Still not aimed at architectural concepts; evaluation is entity recall / RE, not issue→code linking or agent reasoning.

## Links

- arXiv: https://arxiv.org/abs/2402.16159 · [PDF](https://arxiv.org/pdf/2402.16159) · [HTML](https://arxiv.org/html/2402.16159v5)
- Code: https://github.com/NeuralSentinel/DistALANER
