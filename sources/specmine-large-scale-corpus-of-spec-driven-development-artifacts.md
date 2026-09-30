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

# SpecMine: A Large-Scale Corpus of Spec-Driven Development Artifacts

## Summary

Preprint for **SpecMine**, one of the two MSR 2027 Mining Challenge datasets. Spec-Driven Development (SDD) uses structured natural-language specifications (often drafted by AI tools and curated by developers) to drive AI coding agents. The authors release a July 2026 snapshot capturing SDD artefacts from public GitHub through a broad census of `spec.md`/`specs.md` files (470,795 files, 73,030 repositories, 17 named tools), a separate Kiro census (98,574 requirements/design/tasks artefacts, 12,910 repositories), a curated layer of 5,992 spec-touching pull requests across 581 repositories, and a census-wide traceability index of 2,421,323 typed spec-to-code references. Each spec is enriched with repository metadata, full commit history, and 39 parsed structural features.

## Key points

- **Authors / affiliation:** Shyam Agarwal, Anmol Singhal, Travis Breaux, Bogdan Vasilescu (Carnegie Mellon University).
- **Versions:** arXiv:2608.25202; submitted 25 Aug 2026 (v1), revised 1 Sep 2026 (v3). Describes SpecMine **v1.0** (July 2026 snapshot).
- **Four corpus parts:** (1) broad `spec.md`/`specs.md` census with tool attribution; (2) Kiro `.kiro/specs/` census; (3) PR sweep for 11 tools on ≥10-star repos (5,992 spec-touching PRs); (4) typed reference / traceability index.
- **Scale highlights:** 780,335 spec-file commits; 468,307 files with structural features; 81.2% of sampled spec-touching PRs also modify code; ~14.7 GB curated uncompressed size.
- **Access tiers:** Zenodo full dump; Hugging Face Parquet mirror; GitHub schema/loaders/500-repo sample.
- **License:** SpecMine compilation CC BY 4.0; underlying content follows each repo’s license.
- **Challenge role:** SpecMine is one of the two official MSR 2027 Mining Challenge datasets (with GitSkills); see [[msr-2027-mining-challenge]].

## Dataset links (from the preprint § Data Availability)

- **Zenodo (full dataset):** DOI `10.5281/zenodo.22102779` — https://doi.org/10.5281/zenodo.22102779
- **Hugging Face (Parquet mirror):** https://huggingface.co/datasets/ShyAgarwal/specmine
- **GitHub (schema, loaders, notebook, 500-repo sample):** https://github.com/shyamagarwal13/specmine-official

## Relevance to thesis

Core primary source for studying how specifications are written, attributed to SDD tools, evolve, and connect to implementation in the age of coding agents. Directly supports MSR Mining Challenge participation and exploratory connections to iterative agent evaluation (e.g. SlopCodeBench evolving specs) and issue-/spec-tracker grounding of agent workflows.

## Quotes / excerpts

> "We present SpecMine, a corpus that captures SDD in public GitHub repositories through two censuses: a broad census of spec.md/specs.md files covering most tools (470,795 files across 73,030 repositories, attributed to 17 named tools), and a Kiro census of its distinct requirements/design/tasks layout (98,574 files across 12,910 repositories)."

> "SpecMine lets the community study, for the first time, how software is specified in the age of AI agents."

> "How a spec actually becomes code is not directly observable... Co-change is common in the sample (81.2% of spec-touching PRs also modify code...), so it is a reasonable place to start, but it is an assumption, not ground truth."

## Links

- abs: https://arxiv.org/abs/2608.25202
- pdf: https://arxiv.org/pdf/2608.25202
- Zenodo: https://doi.org/10.5281/zenodo.22102779
- Hugging Face: https://huggingface.co/datasets/ShyAgarwal/specmine
- GitHub: https://github.com/shyamagarwal13/specmine-official
- MSR 2027 Mining Challenge: https://2027.msrconf.org/track/msr-2027-mining-challenge
- related note: [[msr-2027-mining-challenge]]
