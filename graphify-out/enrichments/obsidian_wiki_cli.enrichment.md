---
node: obsidian_wiki_cli
title: "cli.py"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# cli.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 49

### Connexions (EXTRACTED — depuis graph.json)
- ←imports_from— [[__main__.py]] `[EXTRACTED]` (L3)
- —imports→ [[extract()]] `[EXTRACTED]` (L705)
- —imports→ [[plan_batches()]] `[EXTRACTED]` (L636)
- —imports→ [[check_sources()]] `[EXTRACTED]` (L672)
- —imports→ [[update_source()]] `[EXTRACTED]` (L684)
- —imports→ [[hash_file()]] `[EXTRACTED]` (L694)
- —contains→ [[_add_setup_args()]] `[EXTRACTED]` (L970)
- —contains→ [[bootstrap_dir()]] `[EXTRACTED]` (L49)
- —contains→ [[build_parser()]] `[EXTRACTED]` (L850)
- —contains→ [[_check_stale()]] `[EXTRACTED]` (L294)
- —contains→ [[cmd_ast_extract()]] `[EXTRACTED]` (L703)
- —contains→ [[cmd_batch_plan()]] `[EXTRACTED]` (L635)
- —contains→ [[cmd_cache_check()]] `[EXTRACTED]` (L671)
- —contains→ [[cmd_cache_hash()]] `[EXTRACTED]` (L693)
- —contains→ [[cmd_cache_update()]] `[EXTRACTED]` (L683)
- —contains→ [[cmd_doctor()]] `[EXTRACTED]` (L719)
- —contains→ [[cmd_graph_analyse()]] `[EXTRACTED]` (L657)
- —contains→ [[cmd_graph_query()]] `[EXTRACTED]` (L621)
- —contains→ [[cmd_info()]] `[EXTRACTED]` (L816)
- —contains→ [[cmd_lint()]] `[EXTRACTED]` (L742)
- *…29 autres arêtes*
<!-- graphify:end -->

## Définition

`cli.py` est la couche d'entrée de commande du paquet `obsidian-wiki`: il définit `main(argv)`, construit le parseur `argparse` et route les sous-commandes vers des fonctions `cmd_*`. Sans sous-commande, `main` transforme l'appel en `setup`, tandis que `build_parser()` expose notamment `setup`, `list`, `info`, `graph-query`, `batch-plan`, `graph-analyse`, `cache-check`, `cache-update`, `cache-hash`, `ast-extract`, `doctor`, `lint` et `query`.

Ce fichier est central parce qu'il relie l'installation des skills, la configuration globale, les diagnostics, les requêtes graph/RAG, l'analyse du graphe, le lint et le cache d'ingestion à une interface exécutable unique.^[inferred] Son degré élevé vient surtout de sa fonction de façade: les commandes importent tardivement les moteurs spécialisés (`batch`, `cache`, `graph_analysis`, `graphrag`, `lint`, `ast_extractor`) puis normalisent les chemins, les erreurs et la sortie JSON ou texte.^[inferred]

La couche CLI garde peu d'état métier elle-même: elle délègue le calcul aux modules appelés et se limite souvent à valider l'existence des chemins, lire la config et imprimer le résultat.^[inferred] Une limite visible est que plusieurs sous-commandes exigent un vault explicite alors que `lint` et `query` peuvent retomber sur `OBSIDIAN_VAULT_PATH`, ce qui rend le confort d'usage inégal selon la commande.^[inferred]

## Voir aussi

- [[obsidian_wiki_cache_update_source]]
