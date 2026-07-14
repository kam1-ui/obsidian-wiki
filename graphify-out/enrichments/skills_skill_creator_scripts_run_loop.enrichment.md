---
node: skills_skill_creator_scripts_run_loop
title: "run_loop.py"
community: "Loop Report Generation"
source_file: ".skills/skill-creator/scripts/run_loop.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# run_loop.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Loop Report Generation · **Fichier:** `.skills/skill-creator/scripts/run_loop.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- —imports_from→ [[generate_report.py]] `[EXTRACTED]` (L18)
- —imports_from→ [[improve_description.py]] `[EXTRACTED]` (L19)
- —imports_from→ [[run_eval.py]] `[EXTRACTED]` (L20)
- —imports_from→ [[utils.py]] `[EXTRACTED]` (L21)
- —contains→ [[main()]] `[EXTRACTED]` (L244)
- —contains→ [[run_loop()]] `[EXTRACTED]` (L47)
- —contains→ [[split_eval_set()]] `[EXTRACTED]` (L24)
<!-- graphify:end -->

## Définition

`run_loop.py` est le script qui combine évaluation et amélioration jusqu’à réussite complète ou épuisement du nombre maximal d’itérations. Il importe la génération de rapport, l’amélioration de description, l’évaluation et le parsing de `SKILL.md`, et définit `split_eval_set()`, `run_loop()` et son interface CLI `main()`.

Il sert de point d’orchestration de la communauté « Loop Report Generation » en reliant les mesures de déclenchement aux propositions successives de description et au rapport final. ^[inferred]

## Voir aussi

- [[run_loop()]]
- [[run_eval.py]]
- [[improve_description()]]
- [[parse_skill_md()]]
