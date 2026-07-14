---
node: skills_skill_creator_scripts_aggregate_benchmark
title: "aggregate_benchmark.py"
community: "Benchmark Aggregation"
source_file: ".skills/skill-creator/scripts/aggregate_benchmark.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# aggregate_benchmark.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Benchmark Aggregation · **Fichier:** `.skills/skill-creator/scripts/aggregate_benchmark.py` · **Degré:** 6

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[aggregate_results()]] `[EXTRACTED]` (L176)
- —contains→ [[calculate_stats()]] `[EXTRACTED]` (L45)
- —contains→ [[generate_benchmark()]] `[EXTRACTED]` (L227)
- —contains→ [[generate_markdown()]] `[EXTRACTED]` (L281)
- —contains→ [[load_run_results()]] `[EXTRACTED]` (L67)
- —contains→ [[main()]] `[EXTRACTED]` (L338)
<!-- graphify:end -->

## Définition

Ce script charge les fichiers `grading.json` depuis deux dispositions de répertoires, calcule moyenne, écart-type, minimum et maximum par configuration, puis construit un benchmark complet et son résumé Markdown. Son interface en ligne de commande accepte le dossier de benchmark, le nom et le chemin du skill ainsi qu’un chemin de sortie, écrit `benchmark.json` et un fichier `.md` homologue, puis affiche les taux de réussite et leur delta.

Il centralise la conversion des résultats bruts d’évaluation en artefacts comparatifs stables, tandis que [[generate_benchmark()]] en constitue l’étape d’assemblage principale. ^[inferred]

## Voir aussi

- [[generate_benchmark()]]
