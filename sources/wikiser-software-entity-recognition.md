---
title: "Software Entity Recognition with Noise-Robust Learning (WikiSER)"
type: source
url: https://arxiv.org/abs/2308.10564
authors:
  - Tai Nguyen
  - Yifeng Di
  - Joohan Lee
  - Muhao Chen
  - Tianyi Zhang
year: 2023
arxiv_id: "2308.10564"
venue: ASE 2023
added: 2026-10-01
tags:
  - named-entity-recognition
  - software-entities
  - wikipedia
  - noise-robust-learning
---

# WikiSER (ASE 2023)

**Prefer the paper.** Large software-entity NER resource from Wikipedia (79K entities, 12 types, 1.7M labeled sentences) + self-regularization noise-robust training; beats SoftNER on WikiSER and improves on SO benchmarks.

## Key points

- **Text.** Wikipedia Computing subtree (primary); evaluated also on SoftNER/S-NER Stack Overflow sets. **Not** GitHub issues.
- **Entity types (12).** Algorithm, Application, Architecture, Data structure, Device, Error name, General concept, Language, Library, License, Operating system, Protocol.
- **Method.** Auto-label via Wiki hyperlinks/aliases/categories; BERT + self-regularization (multi-dropout KL agreement).
- **Artifacts.** https://github.com/taidnguyen/software_entity_recognition · HF models `taidng/wikiser-bert-*`

## Relevance to thesis

Strong software-product NER lexicon (Architecture here = hardware/microarchitecture, **not** software architecture decisions). Useful transfer candidate / type inventory; gap remains issue-tracker adaptation.

## Links

- arXiv: https://arxiv.org/abs/2308.10564 · [PDF](https://arxiv.org/pdf/2308.10564)
- PDF (author): https://tianyi-zhang.github.io/files/ase2023-wikiser.pdf
- Code: https://github.com/taidnguyen/software_entity_recognition
