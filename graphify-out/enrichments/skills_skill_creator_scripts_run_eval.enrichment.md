---
node: skills_skill_creator_scripts_run_eval
title: "run_eval.py"
community: "Loop Report Generation"
source_file: ".skills/skill-creator/scripts/run_eval.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# run_eval.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Loop Report Generation · **Fichier:** `.skills/skill-creator/scripts/run_eval.py` · **Degré:** 6

### Connexions (EXTRACTED — depuis graph.json)
- —imports_from→ [[utils.py]] `[EXTRACTED]` (L19)
- —contains→ [[find_project_root()]] `[EXTRACTED]` (L22)
- —contains→ [[main()]] `[EXTRACTED]` (L259)
- —contains→ [[run_eval()]] `[EXTRACTED]` (L184)
- —contains→ [[run_single_query()]] `[EXTRACTED]` (L35)
- ←imports_from— [[run_loop.py]] `[EXTRACTED]` (L20)
<!-- graphify:end -->

## Définition

`run_eval.py` mesure si une description de skill provoque son déclenchement par Claude sur un ensemble de requêtes et émet les résultats en JSON. Le module localise la racine du projet, exécute une requête en créant temporairement une commande Claude, agrège les exécutions parallèles dans `run_eval()` et expose une interface CLI dans `main()`.

Il fournit la couche expérimentale de la boucle d’optimisation : ses observations de déclenchement alimentent directement `run_loop.py`. ^[inferred]

## Voir aussi

- [[run_eval()]]
- [[run_loop.py]]
