---
title: "T-FREX: A Transformer-based Feature Extraction Method from Mobile App Reviews"
type: source
url: https://arxiv.org/abs/2401.03833
authors:
  - Quim Motger
  - Alessio Miaschi
  - Felice Dell’Orletta
  - Xavier Franch
  - Jordi Marco
year: 2024
arxiv_id: "2401.03833"
venue: SANER 2024
added: 2026-10-01
tags:
  - named-entity-recognition
  - app-reviews
  - feature-extraction
---

# T-FREX (SANER 2024)

**Prefer the paper.** Casts mobile **app-review feature extraction as NER** (B-/I-/O-feature); fine-tunes BERT/RoBERTa/XLNet; crowdsourced AlternativeTo features transferred into reviews.

## Key points

- **Text.** Google Play–style app reviews (SE-adjacent user feedback), not issue trackers.
- **Entity type.** Single type: feature (functionality/capability spans).
- **Method.** Crowdsourced feature lists → exact-match transfer into review tokens → Transformer token classification; beats SAFE syntactic baseline in-domain.

## Relevance to thesis

Shows NER framing works for another SE free-text genre. Useful citation for “SE feedback text → span NER,” not a GitHub-issue corpus.

## Links

- arXiv: https://arxiv.org/abs/2401.03833
- Code: https://github.com/nlp4se/t-frex (also gessi-chatbots/t-frex)
