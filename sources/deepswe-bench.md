---
title: "DeepSWE: Measuring Frontier Coding Agents on Original, Long-Horizon Engineering Tasks"
type: source
url: https://arxiv.org/abs/2607.07946
authors:
  - Wenqi Huang
  - Charley Lee
  - Leonard Tng
  - Serena Ge
  - Datacurve
year: 2026
arxiv_id: "2607.07946"
added: 2026-09-30
tags:
  - swe-agents
  - benchmarks
  - long-horizon
  - contamination
  - verification
---

# DeepSWE Bench

**Prefer the paper / site.** Authored (not mined) long-horizon SWE benchmark from Datacurve; built to separate frontier agents when SWE-Bench-style boards saturate.

## Key points

- **113** original tasks across **91** repos and **5** languages (TS, Go, Python, JS, Rust); solutions never merged upstream → decontamination by construction.
- Short, developer-like prompts (~half SWE-Bench Pro length) but reference solutions touch **~5.5×** more LOC and more files; median repo contributes **1** task.
- Hand-written **functional verifiers** (behavior via public APIs), not inherited PR tests; independent LLM-judge disagreement ~**1.4%** vs ~**32%** on SWE-Bench Pro inherited tests (paper audit).
- Fixed harness: **mini-swe-agent** (+ Pier / Harbor-compatible runner); reports pass@1 / pass@4. v1.1 grades committed patches in clean containers + CTRF reports.
- Live site separates models across a wider score band than public SWE-Bench Pro clusters.

## Figures

Corpus vs Verified / Pro — shorter prompts than Pro, much larger solutions:

![[assets/deepswe-fig2-corpus-stats.png]]

Paper leaderboard snapshot (pass@1 solid, pass@4 faded) — wide spread across frontier configs:

![[assets/deepswe-fig1-leaderboard.png]]

## Relevance

Strong contrast to mined SWE-Bench Pro: contamination story, verifier quality, and prompt realism. Same mini-swe-agent lineage as the Slurm Pro setup.

## Links

- Paper (arXiv): https://arxiv.org/abs/2607.07946 · pdf: https://arxiv.org/pdf/2607.07946 · html: https://arxiv.org/html/2607.07946
- Leaderboard / site: https://deepswe.datacurve.ai/
- Blog (intro): https://deepswe.datacurve.ai/blog/deepswe · v1.1: https://deepswe.datacurve.ai/blog/deepswe-v1-1
- GitHub: https://github.com/datacurve-ai/deep-swe
- Run docs: https://deepswe.datacurve.ai/run
