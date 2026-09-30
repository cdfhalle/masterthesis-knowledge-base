---
title: "SWE-Marathon: Can Agents Autonomously Complete Ultra-Long-Horizon Software Work?"
type: source
url: https://arxiv.org/abs/2606.07682
authors:
  - Rishi Desai
  - Jesse Hu
  - Joan Cabezas
  - Abundant et al.
year: 2026
arxiv_id: "2606.07682"
added: 2026-09-30
tags:
  - swe-agents
  - benchmarks
  - ultra-long-horizon
  - reward-hacking
  - harbor
---

# SWE Marathon

**Prefer the paper / site.** Ultra-long-horizon project-scale SWE benchmark (Abundant); Harbor task format; multi-layer verifiers + anti-cheat.

## Key points

- **20** tasks: library reproductions / ports, product clones, ML engineering, algorithmic optimization (e.g. Rust C compiler, K8s-in-Rust, Slack/Mastodon clones, Triton kernels).
- Horizon: logged attempts avg **~27.2M** tokens (tail to hundreds of M); wall-clock limits hours; human expert estimates days–weeks.
- Binary reward (full verifier pass); multi-channel checks (unit/parity/perf/audit + computer-use UX on some clones). Visible feedback ≠ hidden final verifier.
- Frontier configs **<~30–50%** pass@1 depending on leaderboard cut; failures: weak self-check, premature stop, timeouts; **~13.8%** rollouts show reward-hacking *attempts* (paper; layered defenses catch shipped bypasses in audit).
- Eval via Harbor / Modal; commercial CLIs + Terminus 2.

## Figures

Horizon vs other agent/SWE benches — Marathon sits at the extreme human solve-time / token end:

![[assets/swe-marathon-fig1-horizon-comparison.png]]

Pass@1 by agent–model config (paper sweep) — no config clears a high fraction at this horizon:

![[assets/swe-marathon-fig2-pass1.png]]

## Relevance

Upper bound on “sustained autonomous SWE” beyond issue→patch benches ([[swe-bench-pro]], [[deepswe-bench]]). Integrity / reward-hacking angle matters for any long-running Slurm eval.

## Links

- Paper (arXiv): https://arxiv.org/abs/2606.07682 · pdf: https://arxiv.org/pdf/2606.07682 · site PDF: https://www.swe-marathon.org/swe-marathon-paper.pdf
- Leaderboard / site: https://www.swe-marathon.org/
- GitHub: https://github.com/abundant-ai/swe-marathon
