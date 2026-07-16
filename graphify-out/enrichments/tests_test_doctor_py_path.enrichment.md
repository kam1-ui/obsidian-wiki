---
node: tests_test_doctor_py_path
title: "Path"
community: "Doctor CLI Tests"
source_file: ""
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.0
  inferred: 1.0
  ambiguous: 0.0
---

# Path

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Doctor CLI Tests · **Fichier:** `?` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←references— [[_run()]] `[EXTRACTED]` (L14)
- ←references— [[_install_all_skills()]] `[EXTRACTED]` (L41)
- ←references— [[_make_vault()]] `[EXTRACTED]` (L34)
- ←references— [[test_doctor_fails_on_invalid_manifest()]] `[EXTRACTED]` (L79)
- ←references— [[test_doctor_json_clean_install()]] `[EXTRACTED]` (L50)
- ←references— [[test_doctor_strict_turns_warnings_into_nonzero_exit()]] `[EXTRACTED]` (L94)
- ←references— [[test_doctor_warns_without_agent_installs_but_exits_zero()]] `[EXTRACTED]` (L65)
- ←references— [[_write_config()]] `[EXTRACTED]` (L25)
<!-- graphify:end -->

## Définition

Représente la classe `pathlib.Path` de la bibliothèque standard Python, utilisée pour manipuler et configurer de manière robuste les chemins de fichiers (tels que la racine du vault ou le dossier HOME utilisateur) au cours des tests unitaires du module Doctor CLI.^[inferred]

## Voir aussi

- [[tests_test_doctor|test_doctor.py]]
- [[tests_test_doctor_run|_run()]]

