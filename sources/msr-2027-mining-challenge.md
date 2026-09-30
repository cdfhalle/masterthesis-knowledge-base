---
title: "MSR 2027 Mining Challenge"
type: source
url: https://2027.msrconf.org/track/msr-2027-mining-challenge
authors:
  - MSR 2027 Organizing Committee
year: 2027
added: 2026-09-30
tags:
  - msr
  - mining-challenge
  - specmine
  - gitskills
  - datasets
  - spec-driven-development
  - coding-agents
---

# MSR 2027 Mining Challenge

## Summary

Official call for the **MSR 2027 Mining Challenge** (24th International Conference on Mining Software Repositories, Dublin, Ireland, co-located with ICSE 2027). The challenge features **two community datasets** of natural-language artefacts that AI coding agents produce and consume: **GitSkills** (agent skills) and **SpecMine** (spec-driven development artefacts). Participants may use either dataset or combine both. Accepted challenge papers are published as short papers in IEEE Xplore (4 pages + 1 page of references).

## Key points

- **Venue:** MSR 2027, Dublin; submission via HotCRP (`https://msr2027-challenge.hotcrp.com/`).
- **Deadlines (AoE):** Abstract Dec 18, 2026; Paper Dec 23, 2026; Notification Jan 19, 2027; Camera-ready Jan 26, 2027.
- **SpecMine (this vault’s focus):** first large-scale open corpus of SDD artefacts mined from GitHub — 470,795 `spec.md`/`specs.md` files across 73,030 repositories (17 named tools), plus a Kiro census of 98,574 requirements/design/tasks artefacts across 12,910 repositories; collected July 2026; includes commit history, structural features, spec-touching PRs, and a typed spec-to-code traceability index.
- **Suggested SpecMine research directions (from the call):** adoption/diffusion of SDD; anatomy and quality of specs; the spec–code relationship; human–AI collaboration around specs; lifecycle, evolution, and abandonment.
- **Open science:** cite the dataset version used (e.g. July 2026 / Zenodo DOI); disclose analysis code and additional data; best paper award requires preserved archives.

## SpecMine dataset links (from the official challenge page)

- **Preprint:** https://arxiv.org/abs/2608.25202 — *SpecMine: A Large-Scale Corpus of Spec-Driven Development Artifacts*
- **Zenodo (full dataset, citable DOI):** https://doi.org/10.5281/zenodo.22102779 (DOI `10.5281/zenodo.22102779`) — MySQL dump plus CSV/Parquet exports and JSONL of spec contents
- **Hugging Face (per-table Parquet mirror):** https://huggingface.co/datasets/ShyAgarwal/specmine
- **GitHub (schema, loaders, notebook, 500-repo sample):** https://github.com/shyamagarwal13/specmine-official

## Relevance to thesis

Primary entry point for the **MSR SpecMine Challenge** track of work: official challenge framing, recommended research questions, submission rules, and authoritative dataset download locations. Complements [[specmine-large-scale-corpus-of-spec-driven-development-artifacts]] (preprint) and connects to exploratory links from [[slopcodebench-coding-agents-degrade-long-horizon]] / findings on iterative agent failure modes under evolving specs.

## Quotes / excerpts

> "This year’s MSR Mining Challenge invites the global research community to explore this practice using SpecMine, the first large-scale, openly available corpus of spec-driven development artefacts mined from GitHub repositories"

> "Participants may work with either dataset, or combine both in a single submission: GitSkills, a dataset of agent skills, and SpecMine, a corpus of spec-driven development artefacts."

## Links

- challenge (official): https://2027.msrconf.org/track/msr-2027-mining-challenge
- challenge (researchr mirror): https://conf.researchr.org/track/msr-2027/msr-2027-mining-challenge
- SpecMine preprint: https://arxiv.org/abs/2608.25202
- Zenodo: https://doi.org/10.5281/zenodo.22102779
- Hugging Face: https://huggingface.co/datasets/ShyAgarwal/specmine
- GitHub sample/mirror: https://github.com/shyamagarwal13/specmine-official
- HotCRP submissions: https://msr2027-challenge.hotcrp.com/
- related note: [[specmine-large-scale-corpus-of-spec-driven-development-artifacts]]
