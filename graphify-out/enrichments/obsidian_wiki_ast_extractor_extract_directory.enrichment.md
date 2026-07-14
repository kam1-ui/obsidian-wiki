---
node: obsidian_wiki_ast_extractor_extract_directory
title: "extract_directory()"
community: "AST Extraction"
source_file: "obsidian_wiki/ast_extractor.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# extract_directory()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** AST Extraction · **Fichier:** `obsidian_wiki/ast_extractor.py` · **Degré:** 12

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[ast_extractor.py]] `[EXTRACTED]` (L355)
- —references→ [[Graph]] `[EXTRACTED]` (L355)
- —calls→ [[.merge()]] `[EXTRACTED]` (L365)
- —calls→ [[extract_file()]] `[EXTRACTED]` (L364)
- —references→ [[Path]] `[EXTRACTED]` (L355)
- —calls→ [[_walk_code_files()]] `[EXTRACTED]` (L361)
- ←calls— [[extract()]] `[EXTRACTED]` (L382)
- ←rationale_for— [[Extract all code files under *root*, merging into one graph.]] `[EXTRACTED]` (L356)
- ←imports— [[test_ast_extractor.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_files_processed_count()]] `[EXTRACTED]` (L117)
- ←calls— [[.test_multi_language()]] `[EXTRACTED]` (L111)
- ←calls— [[.test_nodes_merged()]] `[EXTRACTED]` (L121)
<!-- graphify:end -->

## Définition

`extract_directory(root: Path, *, max_files: int = 2000) -> Graph` parcourt les fichiers de code sous `root`, extrait chacun avec `extract_file(path, root=root)` et fusionne les graphes obtenus avec `Graph.merge()`. Il s’arrête lorsque `max_files` est atteint et comptabilise chaque fichier parcouru ainsi que sa langue déterminée par extension. Il place ces compteurs dans `graph.stats` sous `files_processed` et `languages` avant de renvoyer le graphe agrégé.

Cette fonction est le pont entre l’extraction unitaire et une représentation unique d’un dépôt ou d’une arborescence complète. ^[inferred] Appelée par `extract()` pour les répertoires, elle rend les résultats de plusieurs fichiers directement sérialisables comme un seul graphe. ^[inferred]

La fusion déduplique les nœuds par identifiant et les arêtes par triplet source-cible-relation ; le résultat dépend donc de la stabilité des identifiants relatifs produits par `extract_file()`. ^[inferred]

## Voir aussi

- [[extract_file()]]
- [[extract()]]
- [[test_ast_extractor.py]]
