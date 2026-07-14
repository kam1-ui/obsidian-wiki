---
node: skills_skill_creator_scripts_run_eval_run_eval
title: "run_eval()"
community: "Loop Report Generation"
source_file: ".skills/skill-creator/scripts/run_eval.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# run_eval()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Loop Report Generation · **Fichier:** `.skills/skill-creator/scripts/run_eval.py` · **Degré:** 6

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[run_eval.py]] `[EXTRACTED]` (L184)
- —references→ [[Path]] `[EXTRACTED]` (L184)
- —indirect_call→ [[run_single_query()]] `[INFERRED]` (L203)
- ←calls— [[main()]] `[EXTRACTED]` (L286)
- ←rationale_for— [[Run the full eval set and return results.]] `[EXTRACTED]` (L195)
- ←calls— [[run_loop()]] `[INFERRED]` (L89)
<!-- graphify:end -->

## Définition

`run_eval(eval_set, skill_name, description, num_workers, timeout, project_root, runs_per_query=1, trigger_threshold=0.5, model=None) -> dict` soumet chaque requête, éventuellement plusieurs fois, à `run_single_query()` dans un `ProcessPoolExecutor`. Elle agrège les déclenchements par requête, applique le seuil selon `should_trigger`, puis renvoie les résultats détaillés et un résumé des réussites et échecs.

Elle est le moteur de mesure appelé par `run_loop()` pour noter chaque description candidate avant une éventuelle amélioration. ^[inferred]

## Voir aussi

- [[run_eval.py]]
- [[run_loop()]]
