---
node: tests_test_ast_extractor_testextractfile
title: "TestExtractFile"
community: "AST Extraction"
source_file: "tests/test_ast_extractor.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# TestExtractFile

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** AST Extraction · **Fichier:** `tests/test_ast_extractor.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_ast_extractor.py]] `[EXTRACTED]` (L60)
- —method→ [[.test_file_node_present()]] `[EXTRACTED]` (L96)
- —method→ [[.test_javascript_class_and_function()]] `[EXTRACTED]` (L84)
- —method→ [[.test_javascript_inheritance()]] `[EXTRACTED]` (L90)
- —method→ [[.test_python_classes()]] `[EXTRACTED]` (L61)
- —method→ [[.test_python_functions()]] `[EXTRACTED]` (L67)
- —method→ [[.test_python_imports()]] `[EXTRACTED]` (L72)
- —method→ [[.test_python_inheritance_edge()]] `[EXTRACTED]` (L78)
- —method→ [[.test_unknown_extension_returns_empty()]] `[EXTRACTED]` (L101)
<!-- graphify:end -->

## Définition

`TestExtractFile` est une classe de tests pytest qui appelle `extract_file()` sur des fixtures Python et JavaScript. Ses huit méthodes vérifient l’extraction des classes, fonctions et imports, les arêtes d’héritage, la présence unique du nœud fichier et le retour d’un graphe vide pour une extension inconnue.

Elle fixe le contrat observable de l’extraction unitaire multi-langage du module `ast_extractor.py`. ^[inferred]

## Voir aussi

- [[ast_extractor.py]]
