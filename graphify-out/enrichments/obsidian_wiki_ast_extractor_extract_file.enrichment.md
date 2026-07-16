---
node: obsidian_wiki_ast_extractor_extract_file
title: "extract_file()"
community: "AST Extraction"
source_file: "obsidian_wiki/ast_extractor.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# extract_file()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** AST Extraction · **Fichier:** `obsidian_wiki/ast_extractor.py` · **Degré:** 18

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[ast_extractor.py]] `[EXTRACTED]` (L260)
- —calls→ [[Node]] `[EXTRACTED]` (L275)
- —calls→ [[Edge]] `[EXTRACTED]` (L291)
- —references→ [[Graph]] `[EXTRACTED]` (L260)
- —calls→ [[_file_id()]] `[EXTRACTED]` (L288)
- ←calls— [[extract()]] `[EXTRACTED]` (L384)
- ←calls— [[extract_directory()]] `[EXTRACTED]` (L364)
- —references→ [[Path]] `[EXTRACTED]` (L260)
- ←rationale_for— [[Extract nodes and edges from a single code file.]] `[EXTRACTED]` (L261)
- ←imports— [[test_ast_extractor.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_file_node_present()]] `[EXTRACTED]` (L97)
- ←calls— [[.test_javascript_class_and_function()]] `[EXTRACTED]` (L85)
- ←calls— [[.test_javascript_inheritance()]] `[EXTRACTED]` (L91)
- ←calls— [[.test_python_classes()]] `[EXTRACTED]` (L62)
- ←calls— [[.test_python_functions()]] `[EXTRACTED]` (L68)
- ←calls— [[.test_python_imports()]] `[EXTRACTED]` (L73)
- ←calls— [[.test_python_inheritance_edge()]] `[EXTRACTED]` (L79)
- ←calls— [[.test_unknown_extension_returns_empty()]] `[EXTRACTED]` (L104)
<!-- graphify:end -->

## Définition

`extract_file(path: Path, root: Path | None = None) -> Graph` sélectionne la spécification de langage à partir de l’extension, puis renvoie un graphe vide si l’extension est inconnue ou si la lecture UTF-8 du fichier échoue. Il crée un nœud de type `file`, parcourt le contenu ligne par ligne et applique les expressions régulières du langage pour produire les nœuds de classes, fonctions et imports ainsi que les arêtes `defines`, `imports` et `inherits`. Les fonctions privées ou dunder dont le nom commence par `_` sont exclues.

Cette fonction est le cœur de l’extraction AST locale : `extract()` lui délègue les chemins de fichiers et `extract_directory()` fusionne ses résultats pour chaque fichier découvert. ^[inferred] Son graphe constitue donc l’unité élémentaire sur laquelle reposent l’agrégation par répertoire et la sérialisation finale. ^[inferred]

Malgré son nom d’extracteur AST, cette implémentation est une analyse ligne par ligne fondée sur des expressions régulières ; les constructions multilignes ou les syntaxes absentes des motifs peuvent lui échapper. ^[inferred]

## Voir aussi

- [[extract()]]
- [[extract_directory()]]
- [[test_ast_extractor.py]]
