# Index

## Sources
- [[slopcodebench-coding-agents-degrade-long-horizon]] — SlopCodeBench (arXiv:2603.24755)
- [[msr-2027-mining-challenge]] — MSR 2027 Mining Challenge (official call; SpecMine + GitSkills)
- [[specmine-large-scale-corpus-of-spec-driven-development-artifacts]] — SpecMine preprint (arXiv:2608.25202); Zenodo / HF / GitHub dataset links
- [[swe-bench-pro]] — SWE-Bench Pro (arXiv:2509.16941); Scale leaderboards; Slurm forks (cdfhalle)
- [[swe-debate-competitive-multi-agent-debate]] — SWE-Debate (arXiv:2507.23348 / ICSE 2026); dependency-graph fault propagation traces + competitive debate
- [[deepswe-bench]] — DeepSWE Bench (arXiv:2607.07946); authored long-horizon SWE
- [[swe-marathon]] — SWE Marathon (arXiv:2606.07682); ultra-long-horizon / Harbor
- [[terminal-bench-4]] — Terminal-Bench 4.0 (tbench.ai; paper arXiv:2601.11868)
- [[ast-grep]] — AST-Grep structural search/rewrite; exploratory possible agent tooling
- [[softner-stackoverflow-ner]] — SoftNER / StackOverflowNER (ACL 2020; arXiv:2005.01634); 20-type software NER
- [[distalaner-oss-named-entity-recognition]] — DistALANER (arXiv:2402.16159); distant+active OSS bug/CQA NER
- [[bner-bug-specific-named-entity]] — BNER (ICPC 2018); Mozilla/Eclipse bug-report NER
- [[dbner-bug-specific-ner-dnn]] — DBNER (JSS 2020); BiLSTM-CRF bug NER
- [[bug-entities-relations-ase-2022]] — Bug entities + relations (ASE journal 2022)
- [[softner-cloud-incidents-kg]] — SoftNER cloud incidents KG (arXiv:2101.05961); IcM NER→KG
- [[wikiser-software-entity-recognition]] — WikiSER (ASE 2023; arXiv:2308.10564); Wikipedia software NER
- [[t-frex-app-review-feature-ner]] — T-FREX (SANER 2024; arXiv:2401.03833); app-review feature NER
- [[kgcompass-repository-aware-knowledge-graphs]] — KGCompass (arXiv:2503.21710); issue/PR↔code KG for SWE repair
- [[repograph-repository-level-code-graph]] — RepoGraph (ICLR 2025; arXiv:2410.14684); line-level repo graph plug-in
- [[locagent-graph-guided-code-localization]] — LocAgent (arXiv:2503.09089); heterogeneous code graph + agent localization

## Notes
- [[reasoning-traces-for-generated-code]] — idea: tie architectural reasoning and requirements directly to generated code
- [[issue-tracker-entities-and-code-knowledge-graph]] — idea: extract issue entities, map to code, shared KG vocabulary
- [[issue-entity-code-kg-related-work]] — related work for issue NER / entity→code / software KGs (2018–2026)

## Topics
- [[architectural-reasoning-for-coding-agents]] — thesis framing: issue-tracker grounding, planning, and specification

## Findings
- [[slopcodebench-failure-modes-outside-benchmarks]] — failure modes outside SWE benchmarks; open questions re SpecMine / issue trackers
- [[slopcodebench-respecification-at-every-step]] — proposed test of OpenSpec-style re-specification at each change
- [[issue-tracker-grounding-for-architectural-reasoning]] — hypothesis for using issue/PR history to improve architectural reasoning
- [[issue-entity-kg-gap-vs-architectural-vocabulary]] — literature: localization KGs exist; shared architectural vocabulary underserved
