---
node: tests_test_doctor_run
title: "_run()"
community: "Doctor CLI Tests"
source_file: "tests/test_doctor.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# _run()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Doctor CLI Tests · **Fichier:** `tests/test_doctor.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_doctor.py]] `[EXTRACTED]` (L14)
- —references→ [[CompletedProcess]] `[EXTRACTED]` (L14)
- —references→ [[Path]] `[EXTRACTED]` (L14)
- ←calls— [[test_doctor_fails_on_invalid_manifest()]] `[EXTRACTED]` (L86)
- ←calls— [[test_doctor_json_clean_install()]] `[EXTRACTED]` (L57)
- ←calls— [[test_doctor_strict_turns_warnings_into_nonzero_exit()]] `[EXTRACTED]` (L100)
- ←calls— [[test_doctor_warns_without_agent_installs_but_exits_zero()]] `[EXTRACTED]` (L71)
<!-- graphify:end -->

## Définition

`_run(home: Path, *args: str) -> subprocess.CompletedProcess[str]` copie l’environnement, remplace `HOME` par le répertoire de test, puis exécute `python -m obsidian_wiki.cli` avec les arguments reçus en capturant stdout et stderr en texte.

Ce helper isole les tests d’intégration de la commande `doctor` de la configuration réelle de l’utilisateur et leur permet d’asserter le code de sortie ainsi que la réponse JSON. ^[inferred]
