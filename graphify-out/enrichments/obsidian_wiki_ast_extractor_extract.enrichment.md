---
node: obsidian_wiki_ast_extractor_extract
title: "extract()"
community: "AST Extraction"
source_file: "obsidian_wiki/ast_extractor.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.6
  inferred: 0.4
  ambiguous: 0.0
---

# extract()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** AST Extraction · **Fichier:** `obsidian_wiki/ast_extractor.py` · **Degré:** 14

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[ast_extractor.py]] `[EXTRACTED]` (L379)
- —calls→ [[.to_dict()]] `[EXTRACTED]` (L387)
- —calls→ [[extract_file()]] `[EXTRACTED]` (L384)
- —references→ [[Path]] `[EXTRACTED]` (L379)
- —calls→ [[extract_directory()]] `[EXTRACTED]` (L382)
- ←rationale_for— [[Extract from a file or directory, return serialisable dict.]] `[EXTRACTED]` (L380)
- ←imports— [[cli.py]] `[EXTRACTED]` (L705)
- ←calls— [[cmd_ast_extract()]] `[EXTRACTED]` (L708)
- ←imports— [[test_ast_extractor.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_dir_path()]] `[EXTRACTED]` (L134)
- ←calls— [[.test_file_path()]] `[EXTRACTED]` (L127)
- ←calls— [[.test_god_nodes_is_list()]] `[EXTRACTED]` (L142)
- ←calls— [[.test_missing_path_raises()]] `[EXTRACTED]` (L139)
- ←calls— [[.test_output_is_json_serialisable()]] `[EXTRACTED]` (L146)
<!-- graphify:end -->

## Définition

`extract(path: Path) -> dict` est le point d’entrée qui accepte un chemin de fichier ou de répertoire et renvoie un dictionnaire sérialisable. Il appelle `extract_directory()` pour un répertoire, `extract_file()` pour un fichier et lève `FileNotFoundError` lorsque le chemin n’existe sous aucune de ces formes. Dans les deux cas valides, il convertit le `Graph` obtenu avec `Graph.to_dict()`.

Cette fonction forme la façade commune de l’extracteur pour la CLI et pour les consommateurs qui ne veulent pas manipuler directement les objets `Graph`, `Node` et `Edge`. ^[inferred] Elle centralise aussi le choix fichier/répertoire et garantit une forme de sortie homogène comprenant nœuds, arêtes, god nodes et statistiques. ^[inferred]

## Voir aussi

- [[extract_file()]]
- [[extract_directory()]]
- [[test_ast_extractor.py]]
