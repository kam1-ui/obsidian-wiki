---
node: skills_skill_creator_scripts_run_loop_run_loop
title: "run_loop()"
community: "Loop Report Generation"
source_file: ".skills/skill-creator/scripts/run_loop.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# run_loop()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Loop Report Generation · **Fichier:** `.skills/skill-creator/scripts/run_loop.py` · **Degré:** 10

### Connexions (EXTRACTED — depuis graph.json)
- —calls→ [[generate_html()]] `[INFERRED]` (L151)
- —calls→ [[improve_description()]] `[INFERRED]` (L199)
- —calls→ [[find_project_root()]] `[INFERRED]` (L63)
- —calls→ [[run_eval()]] `[INFERRED]` (L89)
- ←contains— [[run_loop.py]] `[EXTRACTED]` (L47)
- —calls→ [[split_eval_set()]] `[EXTRACTED]` (L69)
- ←calls— [[main()]] `[EXTRACTED]` (L293)
- ←rationale_for— [[Run the eval + improvement loop.]] `[EXTRACTED]` (L62)
- —references→ [[Path]] `[EXTRACTED]` (L47)
- —calls→ [[parse_skill_md()]] `[INFERRED]` (L64)
<!-- graphify:end -->

## Définition

`run_loop(eval_set, skill_path, description_override, num_workers, timeout, max_iterations, runs_per_query, trigger_threshold, holdout, model, verbose, live_report_path=None, log_dir=None) -> dict` évalue itérativement une description de skill, sépare éventuellement les requêtes en ensembles d’entraînement et de test, conserve l’historique et renvoie la meilleure description. À chaque itération non concluante, elle appelle `improve_description()` avec les résultats d’entraînement et un historique privé des scores de test, tout en pouvant régénérer un rapport HTML intermédiaire.

Cette fonction orchestre les composants de la communauté « Loop Report Generation » : parsing du skill, évaluation parallèle, amélioration par modèle et génération de rapport. ^[inferred]

## Voir aussi

- [[run_loop.py]]
- [[run_eval()]]
- [[parse_skill_md()]]
- [[improve_description()]]
