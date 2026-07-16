---
node: obsidian_wiki_cli_run_doctor
title: "run_doctor()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.65
  inferred: 0.35
  ambiguous: 0.0
---

# run_doctor()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 10

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L381)
- —calls→ [[Path]] `[EXTRACTED]` (L432)
- —calls→ [[bootstrap_dir()]] `[EXTRACTED]` (L397)
- —calls→ [[list_skills()]] `[EXTRACTED]` (L385)
- —calls→ [[_read_config()]] `[EXTRACTED]` (L406)
- —calls→ [[_doctor_add()]] `[EXTRACTED]` (L386)
- —calls→ [[_doctor_status()]] `[EXTRACTED]` (L566)
- —calls→ [[_required_vault_paths()]] `[EXTRACTED]` (L462)
- —calls→ [[_doctor_project_check()]] `[EXTRACTED]` (L548)
- ←calls— [[cmd_doctor()]] `[EXTRACTED]` (L720)
<!-- graphify:end -->

## Définition

`run_doctor(*, vault_override: str | None = None, project_dir: str | None = None) -> dict[str, object]` agrège des vérifications de santé dans une liste `checks`. La fonction vérifie les skills groupées, les assets de bootstrap, la config globale, le chemin du vault, la version de setup, les fichiers coeur du vault, la validité de `.manifest.json`, les installations globales d'agents et, si demandé, le bootstrap d'un projet.

Ce nœud est central parce qu'il traverse plusieurs sous-systèmes de la CLI sans les modifier : inventaire des skills, résolution de configuration, inspection du vault et état des installations agent. ^[inferred] Il produit le rapport structuré consommé par `cmd_doctor()`, qui se charge ensuite de l'affichage ou du JSON et du code de sortie. ^[inferred]

La fonction tolère plusieurs états incomplets en `warn` plutôt qu'en échec, notamment les fichiers coeur de vault manquants ou les installations agent partielles. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cli_list_skills|list_skills()]]
