---
node: obsidian_wiki_cli_cmd_setup
title: "cmd_setup()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.7
  inferred: 0.3
  ambiguous: 0.0
---

# cmd_setup()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L585)
- —calls→ [[Path]] `[EXTRACTED]` (L602)
- —calls→ [[list_skills()]] `[EXTRACTED]` (L605)
- —calls→ [[install_global_skills()]] `[EXTRACTED]` (L599)
- —calls→ [[install_project()]] `[EXTRACTED]` (L603)
- —calls→ [[resolve_vault_path()]] `[EXTRACTED]` (L591)
- —calls→ [[write_config()]] `[EXTRACTED]` (L592)
- ←indirect_call— [[build_parser()]] `[INFERRED]` (L860)
- —references→ [[Namespace]] `[EXTRACTED]` (L585)
<!-- graphify:end -->

## Définition

`cmd_setup(args: argparse.Namespace) -> int` exécute la commande `setup` : il choisit le mode `copy` ou `symlink`, affiche un bandeau, résout le chemin du vault, écrit la config, installe les skills globales sauf en mode `project_only`, installe éventuellement le bootstrap projet, compte les skills disponibles avec `list_skills()`, puis affiche les prochaines étapes et retourne `0`.

Dans la couche CLI, ce nœud est le chemin d'initialisation principal : `build_parser()` l'associe à la sous-commande `setup`, et `main()` redirige aussi l'absence de sous-commande vers `setup`. ^[inferred] Il relie la configuration persistante, l'installation globale et l'installation projet dans une seule action utilisateur. ^[inferred]

Même si aucun chemin de vault n'est résolu, la commande continue après un message demandant de relancer avec `--vault` ou de modifier `~/.obsidian-wiki/config`. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cli_build_parser|build_parser()]]
- [[obsidian_wiki_cli_list_skills|list_skills()]]
