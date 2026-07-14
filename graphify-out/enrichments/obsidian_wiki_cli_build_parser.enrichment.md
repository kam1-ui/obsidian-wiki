---
node: obsidian_wiki_cli_build_parser
title: "build_parser()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.6
  inferred: 0.4
  ambiguous: 0.0
---

# build_parser()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 17

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L850)
- —indirect_call→ [[cmd_setup()]] `[INFERRED]` (L860)
- —indirect_call→ [[cmd_graph_query()]] `[INFERRED]` (L877)
- —indirect_call→ [[cmd_batch_plan()]] `[INFERRED]` (L890)
- —indirect_call→ [[cmd_graph_analyse()]] `[INFERRED]` (L899)
- —indirect_call→ [[cmd_cache_check()]] `[INFERRED]` (L908)
- —indirect_call→ [[cmd_cache_update()]] `[INFERRED]` (L917)
- —indirect_call→ [[cmd_cache_hash()]] `[INFERRED]` (L924)
- —indirect_call→ [[cmd_ast_extract()]] `[INFERRED]` (L932)
- —indirect_call→ [[cmd_doctor()]] `[INFERRED]` (L943)
- —indirect_call→ [[cmd_lint()]] `[INFERRED]` (L953)
- —indirect_call→ [[cmd_query()]] `[INFERRED]` (L965)
- —indirect_call→ [[cmd_list()]] `[INFERRED]` (L863)
- —indirect_call→ [[cmd_info()]] `[INFERRED]` (L866)
- —references→ [[ArgumentParser]] `[EXTRACTED]` (L850)
- —calls→ [[_add_setup_args()]] `[EXTRACTED]` (L859)
- ←calls— [[main()]] `[EXTRACTED]` (L994)
<!-- graphify:end -->

## Définition

`build_parser()` construit et retourne un `argparse.ArgumentParser` nommé `obsidian-wiki`, avec l'option de version globale et un sous-parseur par commande CLI. La fonction enregistre notamment `setup`, `list`, `info`, `graph-query`, `batch-plan`, `graph-analyse`, `cache-check`, `cache-update`, `cache-hash`, `ast-extract`, `doctor`, `lint` et `query`, puis associe chaque sous-commande à sa fonction via `set_defaults(func=...)`.

Dans le graphe, ce nœud est le routeur central de la couche CLI : il relie l'entrée `main()` aux commandes concrètes et concentre la déclaration des arguments utilisateurs. ^[inferred] Sa centralité vient du fait que les arêtes vers les commandes sont indirectes : le parser ne les appelle pas immédiatement, mais il choisit la fonction qui sera exécutée après `parse_args()`. ^[inferred]

Le comportement "sans sous-commande = setup" n'est pas implémenté dans `build_parser()` mais dans `main()`, qui réécrit `argv` avant le parsing. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cli_cmd_setup|cmd_setup()]]
- [[obsidian_wiki_cli_run_doctor|run_doctor()]]
