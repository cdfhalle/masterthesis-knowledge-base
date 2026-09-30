---
title: "SpecMine: A Large-Scale Corpus of Spec-Driven Development Artifacts"
type: source
url: https://arxiv.org/abs/2608.25202
authors:
  - Shyam Agarwal
  - Anmol Singhal
  - Travis Breaux
  - Bogdan Vasilescu
year: 2026
arxiv_id: "2608.25202"
added: 2026-09-30
tags:
  - msr
  - mining-challenge
  - specmine
  - datasets
  - spec-driven-development
  - coding-agents
  - github-mining
---

# SpecMine

**Prefer the paper.** Official MSR 2027 Mining Challenge dataset (with GitSkills). See [[msr-2027-mining-challenge]].

## Key points

- July 2026 snapshot of SDD artefacts from public GitHub (SpecMine v1.0).
- Broad census: **470,795** `spec.md`/`specs.md` in **73,030** repos (17 tools); Kiro census: **98,574** artefacts / **12,910** repos.
- Curated layer: **5,992** spec-touching PRs (581 repos); traceability index: **2,421,323** typed spec→code refs; 39 structural features; full commit history.
- Access: Zenodo (full) · Hugging Face (Parquet) · GitHub (schema/loaders/500-repo sample). License: compilation CC BY 4.0.

## Figure

![[assets/specmine-fig1-schema-er-diagram.png]]

## Relevance

Primary corpus for how specs are written, attributed, evolve, and link to code under coding agents. Natural partner for SlopCodeBench-style evolving-spec questions.

## Links

- abs: https://arxiv.org/abs/2608.25202 · pdf: https://arxiv.org/pdf/2608.25202
- Zenodo: https://doi.org/10.5281/zenodo.22102779
- HF: https://huggingface.co/datasets/ShyAgarwal/specmine
- GitHub: https://github.com/shyamagarwal13/specmine-official
