---
node: skills_skill_creator_scripts_improve_description_improve_description
title: "improve_description()"
community: "Loop Report Generation"
source_file: ".skills/skill-creator/scripts/improve_description.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.0
---

# improve_description()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Loop Report Generation · **Fichier:** `.skills/skill-creator/scripts/improve_description.py` · **Degré:** 6

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[improve_description.py]] `[EXTRACTED]` (L50)
- —calls→ [[_call_claude()]] `[EXTRACTED]` (L144)
- —references→ [[Path]] `[EXTRACTED]` (L50)
- ←calls— [[main()]] `[EXTRACTED]` (L220)
- ←rationale_for— [[Call Claude to improve the description based on eval results.]] `[EXTRACTED]` (L61)
- ←calls— [[run_loop()]] `[INFERRED]` (L199)
<!-- graphify:end -->

## Définition

`improve_description(skill_name, skill_content, current_description, eval_results, history, model, test_results=None, log_dir=None, iteration=None) -> str` construit un prompt à partir des déclenchements manqués, faux déclenchements, scores et tentatives antérieures, puis appelle Claude pour produire une nouvelle description. Elle extrait la réponse balisée, redemande une version raccourcie au-delà de 1 024 caractères et peut journaliser le transcript JSON de l’itération.

Appelée par `run_loop()`, elle transforme les échecs mesurés par l’évaluation en description candidate pour l’itération suivante. ^[inferred]

## Voir aussi

- [[run_loop()]]
- [[run_eval()]]
