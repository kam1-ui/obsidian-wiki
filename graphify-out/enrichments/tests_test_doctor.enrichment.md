---
node: tests_test_doctor
title: "test_doctor.py"
community: "Doctor CLI Tests"
source_file: "tests/test_doctor.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# test_doctor.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Doctor CLI Tests · **Fichier:** `tests/test_doctor.py` · **Degré:** 11

### Connexions (EXTRACTED — depuis graph.json)
- —imports_from→ [[cli.py]] `[EXTRACTED]` (L11)
- —imports→ [[list_skills()]] `[EXTRACTED]` (L11)
- —contains→ [[_install_all_skills()]] `[EXTRACTED]` (L41)
- —contains→ [[_make_vault()]] `[EXTRACTED]` (L34)
- —contains→ [[_run()]] `[EXTRACTED]` (L14)
- —contains→ [[test_doctor_fails_on_invalid_manifest()]] `[EXTRACTED]` (L79)
- —contains→ [[test_doctor_json_clean_install()]] `[EXTRACTED]` (L50)
- —contains→ [[test_doctor_strict_turns_warnings_into_nonzero_exit()]] `[EXTRACTED]` (L94)
- —contains→ [[test_doctor_warns_without_agent_installs_but_exits_zero()]] `[EXTRACTED]` (L65)
- —contains→ [[_write_config()]] `[EXTRACTED]` (L25)
- ←rationale_for— [[Tests for the doctor CLI command.]] `[EXTRACTED]` (L1)
<!-- graphify:end -->

## Définition

Ce module de tests crée des répertoires HOME et des vaults temporaires, écrit leur configuration et peut y installer toutes les compétences retournées par `list_skills()`. Il exécute ensuite `python -m obsidian_wiki.cli doctor --json` dans un sous-processus et vérifie les statuts et codes de sortie pour une installation saine, des compétences agent absentes, un manifeste JSON invalide et le mode strict.

Il constitue le point de validation d'intégration du diagnostic `doctor`, car il couvre ensemble la configuration, la structure minimale du vault, le manifeste et les installations de compétences. ^[inferred]
