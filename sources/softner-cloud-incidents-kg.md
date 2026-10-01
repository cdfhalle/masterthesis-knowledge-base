---
title: "SoftNER: Mining Knowledge Graphs From Cloud Incidents"
type: source
url: https://arxiv.org/abs/2101.05961
authors:
  - Manish Shetty
  - Chetan Bansal
  - Sumit Kumar
  - Nikitha Rao
  - Nachiappan Nagappan
year: 2021
arxiv_id: "2101.05961"
venue: ICSE-SEIP 2021 (extended EMSE)
added: 2026-10-01
tags:
  - named-entity-recognition
  - knowledge-graphs
  - incident-management
  - microsoft
---

# SoftNER (cloud incidents) — not ACL SoftNER

**Prefer the paper.** Different system from StackOverflow SoftNER. Unsupervised NER + relation mining on Microsoft cloud **incident reports** (IcM): key-value/table bootstrap → multi-task BiLSTM-CRF (entity type + data type) → NPMI relations → KG. Deployed at Microsoft.

## Key points

- **Text.** Service incident descriptions/titles (verbose unstructured ops reports)—analogous to industrial bug/incident trackers, not GitHub Issues.
- **Entities.** Open inventory discovered from patterns (Problem Type, Exception Message, Resource Id, Tenant Id, VNet Id, IP, Status Code, …); data types GUID/URI/IP/etc.
- **Method.** Pattern bootstrap + label propagation + multi-task BiLSTM-CRF+attention+CRF; PMI-based relations; uses for triage and entity recommendation.
- **Name collision.** Do not confuse with Tabassum et al. ACL 2020 SoftNER.

## Relevance to thesis

Best industrial evidence that **tracker-like prose → typed entities → KG** works and improves triage. Entity types are ops/resource IDs, not SE architectural concepts; unsupervised open schema is a useful design contrast to SoftNER’s fixed 20 types.

## Links

- arXiv: https://arxiv.org/abs/2101.05961 · [PDF](https://arxiv.org/pdf/2101.05961)
- Microsoft Research: https://www.microsoft.com/en-us/research/publication/softner-mining-knowledge-graphs-from-cloud-incidents/
