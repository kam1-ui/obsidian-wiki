---
node: skills_skill_creator_scripts_aggregate_benchmark_generate_benchmark
title: "generate_benchmark()"
community: "Benchmark Aggregation"
source_file: ".skills/skill-creator/scripts/aggregate_benchmark.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# generate_benchmark()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Benchmark Aggregation · **Fichier:** `.skills/skill-creator/scripts/aggregate_benchmark.py` · **Degré:** 6

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[aggregate_benchmark.py]] `[EXTRACTED]` (L227)
- —calls→ [[load_run_results()]] `[EXTRACTED]` (L231)
- —references→ [[Path]] `[EXTRACTED]` (L227)
- —calls→ [[aggregate_results()]] `[EXTRACTED]` (L232)
- ←calls— [[main()]] `[EXTRACTED]` (L370)
- ←rationale_for— [[Generate complete benchmark.json from run results.]] `[EXTRACTED]` (L228)
<!-- graphify:end -->

## Définition

`generate_benchmark(benchmark_dir: Path, skill_name: str = "", skill_path: str = "") -> dict` charge les résultats individuels, calcule leur résumé agrégé et transforme chaque exécution en entrée normalisée contenant métriques, attentes et notes. Elle produit un dictionnaire de benchmark avec métadonnées horodatées en UTC, identifiants d’évaluations, liste des runs, synthèse statistique et liste de notes vide.

Dans [[aggregate_benchmark.py]], elle fait la jonction entre les données de grading dispersées et les représentations JSON et Markdown consommables par l’analyse ou la consultation humaine. ^[inferred]

## Voir aussi

- [[aggregate_benchmark.py]]
