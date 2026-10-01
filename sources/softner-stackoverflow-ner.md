---
title: "Code and Named Entity Recognition in StackOverflow (SoftNER)"
type: source
url: https://arxiv.org/abs/2005.01634
authors:
  - Jeniya Tabassum
  - Mounica Maddela
  - Wei Xu
  - Alan Ritter
year: 2020
arxiv_id: "2005.01634"
venue: ACL 2020
added: 2026-10-01
tags:
  - named-entity-recognition
  - software-entities
  - stackoverflow
  - github
---

# SoftNER / StackOverflowNER

**Prefer the paper and code.** Foundational software-domain NER: annotated StackOverflow sentences with 20 fine-grained entity types spanning code tokens and software NL entities; SoftNER + BERTOverflow.

## Key points

- **Corpus.** 15,372 SO sentences (1,237 Q/A threads) labeled with 20 types (Class, Variable, Function, Library, Data Type, Application, Language, File Name, Version, …). Additional GitHub readme/issue evaluation set (~6.5k sentences).
- **Model.** SoftNER combines BERTOverflow (BERT pretrained on 152M SO sentences) with a context-independent code-token classifier and an entity segmenter; attention fusion + linear-CRF.
- **Reported scores.** ~79.10 F1 on SO test; ~61.08 F1 when SO-trained SoftNER is applied to GitHub text (domain drop).
- **Artifacts.** Code, data, guidelines, tokenizer, BERTOverflow: https://github.com/jeniyat/StackOverflowNER/

## Relevance to thesis

Best-known baseline for *extracting software named entities from developer prose*. Directly relevant to NER over issue/PR text, but entity inventory is code/product-centric—not architectural decisions or constraints. SoftNER’s GitHub transfer numbers caution that SO-trained taggers degrade on issue-tracker prose without adaptation.

## Links

- arXiv: https://arxiv.org/abs/2005.01634 · [PDF](https://arxiv.org/pdf/2005.01634) · [HTML](https://ar5iv.labs.arxiv.org/html/2005.01634)
- ACL Anthology: https://aclanthology.org/2020.acl-main.443/
- Code/data: https://github.com/jeniyat/StackOverflowNER/
