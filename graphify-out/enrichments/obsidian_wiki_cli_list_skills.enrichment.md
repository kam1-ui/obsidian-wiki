---
node: obsidian_wiki_cli_list_skills
title: "list_skills()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# list_skills()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L65)
- —calls→ [[skills_dir()]] `[EXTRACTED]` (L66)
- ←calls— [[_check_stale()]] `[EXTRACTED]` (L316)
- ←calls— [[cmd_info()]] `[EXTRACTED]` (L817)
- ←calls— [[cmd_list()]] `[EXTRACTED]` (L811)
- ←calls— [[cmd_setup()]] `[EXTRACTED]` (L605)
- ←calls— [[run_doctor()]] `[EXTRACTED]` (L385)
- ←imports— [[test_doctor.py]] `[EXTRACTED]` (L11)
- ←calls— [[_install_all_skills()]] `[EXTRACTED]` (L44)
<!-- graphify:end -->

## Définition

`list_skills() -> list[str]` retourne les noms triés des sous-répertoires présents dans `skills_dir()`.

Ce petit wrapper est un point d'inventaire partagé : il alimente la commande `list`, l'écran `info`, `cmd_setup()`, `run_doctor()` et les tests qui simulent une installation complète de skills. ^[inferred] Sa centralité vient de sa position entre la découverte physique des skills groupées et les commandes qui doivent compter, afficher ou installer cet ensemble. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cli_cmd_setup|cmd_setup()]]
- [[obsidian_wiki_cli_run_doctor|run_doctor()]]
