---
title: "SWE-Bench Pro: Can AI Agents Solve Long-Horizon Software Engineering Tasks?"
type: source
url: https://arxiv.org/abs/2509.16941
authors:
  - Xiang Deng
  - Jeff Da
  - Scale AI
year: 2025
arxiv_id: "2509.16941"
added: 2026-09-30
tags:
  - swe-agents
  - benchmarks
  - long-horizon
  - contamination
  - slurm
---

# SWE-Bench Pro

**Prefer the paper / site.** Harder, contamination-resistant successor to SWE-Bench Verified (Scale AI). User reimplemented the eval path for Slurm (see local forks below).

## Key points

- **1,865** human-verified tasks from **41** repos: public **731** (11 copyleft repos) · held-out **858** · commercial **276** (18 startup codebases; results only).
- Long-horizon / multi-file: gold patches avg **~107 LOC** across **~4.1** files (vs ~12 LOC / mostly 1-file on Verified); excludes trivial 1–10 LOC edits.
- Prompts include human-augmented **problem statement + requirements + interface**; graded with fail2pass / pass2pass in Docker envs (Python, JS/TS, Go).
- Frontier Pass@1 stays low on harder splits (paper: often below ~25–45% depending on turn/cost caps); commercial set much harder than public.
- **Local Slurm stack (cdfhalle):** agent harness fork [mini-swe-agent](https://github.com/cdfhalle/mini-swe-agent); issue-/PR-/commit-enriched task data [SWE-bench_Pro_issue_data](https://github.com/cdfhalle/SWE-bench_Pro_issue_data); model serving [hpc-model-hosting](https://github.com/cdfhalle/hpc-model-hosting).

## Figures

Patch size & repo mix vs SWE-Bench Verified — Pro targets larger, more balanced multi-repo work:

![[assets/swebench-pro-fig1-patch-size.png]]

Public-set file-count and task-type mix — many tasks touch 5–9 files; mix of features, bugs, refactor, UI/UX, etc.:

![[assets/swebench-pro-fig2-files-tasktypes.png]]

## Relevance

Primary long-horizon SWE issue→patch yardstick used in the thesis infra (Slurm + mini-swe-agent). Compare with authored / ultra-long alternatives: [[deepswe-bench]], [[swe-marathon]], [[terminal-bench-4]].

## Links

- Paper (arXiv): https://arxiv.org/abs/2509.16941 · pdf: https://arxiv.org/pdf/2509.16941
- Scale Labs paper page: https://labs.scale.com/papers/swe-bench-pro
- Blog: https://scale.com/blog/swe-bench-pro
- Leaderboard (public): https://scale.com/leaderboard/swe_bench_pro_public · commercial: https://labs.scale.com/leaderboard/swe_bench_pro_private · results site: https://scaleapi.github.io/SWE-bench_Pro-os/
- GitHub (official): https://github.com/scaleapi/SWE-bench_Pro-os
- Hugging Face: https://huggingface.co/datasets/ScaleAI/SWE-bench_Pro
- User forks: https://github.com/cdfhalle/mini-swe-agent · https://github.com/cdfhalle/SWE-bench_Pro_issue_data · https://github.com/cdfhalle/hpc-model-hosting
