---
node: obsidian_wiki_cli_cmd_info
title: "cmd_info()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.8
  inferred: 0.2
  ambiguous: 0.0
---

# cmd_info()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L816)
- —calls→ [[skills_dir()]] `[EXTRACTED]` (L819)
- —calls→ [[bootstrap_dir()]] `[EXTRACTED]` (L820)
- —calls→ [[list_skills()]] `[EXTRACTED]` (L817)
- —calls→ [[_read_config_value()]] `[EXTRACTED]` (L824)
- —calls→ [[_check_stale()]] `[EXTRACTED]` (L845)
- —references→ [[Namespace]] `[EXTRACTED]` (L816)
- ←indirect_call— [[build_parser()]] `[INFERRED]` (L866)
<!-- graphify:end -->

## Définition

`cmd_info(args: argparse.Namespace) -> int` affiche la version d'`obsidian-wiki`, le chemin des skills, le chemin des fichiers bootstrap, l'état du fichier de configuration global, le vault et la version de setup si la config existe, puis le nombre de skills embarqués et le statut d'installation par agent.

Cette commande sert de diagnostic lisible pour l'utilisateur : elle agrège `list_skills()`, `skills_dir()`, `bootstrap_dir()`, `_read_config_value()` et `_check_stale()` afin de montrer à la fois les assets disponibles et les installations agent incomplètes.^[inferred]

## Voir aussi

- [[skills_dir()]]
- [[bootstrap_dir()]]
- [[_check_stale()]]
