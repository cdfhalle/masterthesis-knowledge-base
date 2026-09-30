---
title: "Terminal-Bench 4.0"
type: source
url: https://www.tbench.ai/news/terminal-bench-4-0
authors:
  - Laude Institute / Harbor Framework
  - Mike A. Merrill
  - Alexander G. Shaw
  - et al.
year: 2026
arxiv_id: "2601.11868"
added: 2026-09-30
tags:
  - terminal-agents
  - benchmarks
  - harbor
  - continuous-benchmark
---

# Terminal Bench 4.0

**Prefer the 4.0 announcement + paper.** Continuous CLI/agent benchmark (Harbor + Laude). Paper introduces the Terminal-Bench line (TB 2.0: 89 tasks); **4.0** is a semantic breaking maintenance release of the live dataset.

## Key points

- Agents operate a **real terminal** in Docker/Harbor sandboxes: software, ML, science, ops, security, hardware, media — not only SWE issue patches.
- Each task: instruction + Dockerfile + hidden tests + oracle; agent never sees tests during the run; container state is scored after.
- **4.0** (from 3.0): recalibrated CPU/memory/time (flat **8h** agent timeout), **fixed 19** tasks, **removed 8** (saturated / refusals / public solutions / quality); **66** tasks remain; no new tasks that cycle.
- Semantic versioning: resource + task-set changes ⇒ major bump; re-run trials required. Run: `harbor run -d terminal-bench/terminal-bench@4.0.0`.
- Foundational paper (arXiv:2601.11868) describes TB 2.0 construction, leaderboard protocol, and failure modes; 4.0 inherits Harbor harness + continuous QA.

## Figures

Paper (TB 2.0) resolution rates by model×scaffold — shows spread and scaffold dependence (context for the continuous board):

![[assets/terminal-bench-fig1-resolution-rates.png]]

Task anatomy — instruction + container given to agent; tests / oracle hidden until scoring:

![[assets/terminal-bench-fig2-task-anatomy.png]]

## Relevance

Complement to repo-issue SWE benches: systems / terminal mastery, Harbor shared with SWE-Marathon. Track 4.x as the live yardstick; cite paper for methodology.

## Links

- Paper (arXiv, TB foundations / 2.0): https://arxiv.org/abs/2601.11868 · pdf: https://arxiv.org/pdf/2601.11868
- 4.0 announcement: https://www.tbench.ai/news/terminal-bench-4-0
- Leaderboard / site: https://www.tbench.ai/
- GitHub (current dataset): https://github.com/harbor-framework/terminal-bench
- Run guide: https://www.tbench.ai/run
- Harbor harness: https://github.com/harbor-framework/harbor
