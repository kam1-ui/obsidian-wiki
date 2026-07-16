---
node: obsidian_wiki_cli_py_path
title: "Path"
community: "CLI Command Layer"
source_file: ""
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.0
  inferred: 1.0
  ambiguous: 0.0
---

# Path

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `?` · **Degré:** 20

### Connexions (EXTRACTED — depuis graph.json)
- ←references— [[_pkg_dir()]] `[EXTRACTED]` (L34)
- ←references— [[bootstrap_dir()]] `[EXTRACTED]` (L49)
- ←calls— [[cmd_ast_extract()]] `[EXTRACTED]` (L706)
- ←calls— [[cmd_batch_plan()]] `[EXTRACTED]` (L637)
- ←calls— [[cmd_cache_check()]] `[EXTRACTED]` (L673)
- ←calls— [[cmd_cache_hash()]] `[EXTRACTED]` (L695)
- ←calls— [[cmd_cache_update()]] `[EXTRACTED]` (L685)
- ←calls— [[cmd_graph_analyse()]] `[EXTRACTED]` (L659)
- ←calls— [[cmd_graph_query()]] `[EXTRACTED]` (L623)
- ←calls— [[cmd_lint()]] `[EXTRACTED]` (L750)
- ←calls— [[cmd_query()]] `[EXTRACTED]` (L794)
- ←calls— [[cmd_setup()]] `[EXTRACTED]` (L602)
- ←references— [[_doctor_project_check()]] `[EXTRACTED]` (L362)
- ←calls— [[_install_hermes_profiles()]] `[EXTRACTED]` (L143)
- ←references— [[install_project()]] `[EXTRACTED]` (L206)
- ←references— [[install_skills()]] `[EXTRACTED]` (L70)
- ←references— [[_required_vault_paths()]] `[EXTRACTED]` (L353)
- ←references— [[_resolve_bootstrap_src()]] `[EXTRACTED]` (L186)
- ←calls— [[run_doctor()]] `[EXTRACTED]` (L432)
- ←references— [[skills_dir()]] `[EXTRACTED]` (L38)
<!-- graphify:end -->

## Définition

Représente la classe standard `pathlib.Path` de Python, intensivement exploitée dans le module CLI pour manipuler, valider et résoudre dynamiquement les chemins d'accès du vault, des configurations et des répertoires du framework. ^[inferred]
