---
node: skills_skill_creator_eval_viewer_generate_review_find_runs
title: "find_runs()"
community: "Skill Eval Review Viewer"
source_file: ".skills/skill-creator/eval-viewer/generate_review.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# find_runs()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Skill Eval Review Viewer · **Fichier:** `.skills/skill-creator/eval-viewer/generate_review.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[generate_review.py]] `[EXTRACTED]` (L60)
- —references→ [[Path]] `[EXTRACTED]` (L60)
- —calls→ [[_find_runs_recursive()]] `[EXTRACTED]` (L63)
- ←calls— [[load_previous_iteration()]] `[EXTRACTED]` (L235)
- ←calls— [[main()]] `[EXTRACTED]` (L411)
- ←rationale_for— [[Recursively find directories that contain an outputs/ subdirectory.]] `[EXTRACTED]` (L61)
- ←calls— [[.do_GET()]] `[EXTRACTED]` (L335)
<!-- graphify:end -->

## Définition

`find_runs(workspace: Path) -> list[dict]` recherche récursivement les répertoires contenant un sous-répertoire `outputs/`, construit leurs descriptions, puis trie les résultats par `eval_id` et identifiant avant de les retourner.

Cette fonction est le point commun de découverte des runs pour le démarrage du viewer, le rechargement HTTP à chaud et la récupération du contexte d’une itération précédente. ^[inferred]

## Voir aussi

- [[skills_skill_creator_eval_viewer_generate_review_main|main()]]
- [[skills_skill_creator_eval_viewer_generate_review_reviewhandler|ReviewHandler]]
