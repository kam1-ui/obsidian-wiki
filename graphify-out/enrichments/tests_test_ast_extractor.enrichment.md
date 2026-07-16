---
node: tests_test_ast_extractor
title: "test_ast_extractor.py"
community: "AST Extraction"
source_file: "tests/test_ast_extractor.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# test_ast_extractor.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** AST Extraction · **Fichier:** `tests/test_ast_extractor.py` · **Degré:** 12

### Connexions (EXTRACTED — depuis graph.json)
- —imports_from→ [[ast_extractor.py]] `[EXTRACTED]` (L10)
- —imports→ [[extract_file()]] `[EXTRACTED]` (L10)
- —imports→ [[extract_directory()]] `[EXTRACTED]` (L10)
- —imports→ [[extract()]] `[EXTRACTED]` (L10)
- —contains→ [[TestCLI]] `[EXTRACTED]` (L150)
- —contains→ [[TestExtractDirectory]] `[EXTRACTED]` (L109)
- —contains→ [[TestExtractEntry]] `[EXTRACTED]` (L125)
- —contains→ [[TestExtractFile]] `[EXTRACTED]` (L60)
- —contains→ [[tmp_dir()]] `[EXTRACTED]` (L52)
- —contains→ [[tmp_js()]] `[EXTRACTED]` (L37)
- —contains→ [[tmp_py()]] `[EXTRACTED]` (L18)
- ←rationale_for— [[Tests for the local AST code extractor.]] `[EXTRACTED]` (L1)
<!-- graphify:end -->

## Définition

`tests/test_ast_extractor.py` est la suite de tests de l’extracteur de code local, avec des fixtures temporaires Python et JavaScript ainsi qu’un répertoire qui les réunit. `TestExtractFile` vérifie classes, fonctions, imports, héritage, nœud de fichier et extension inconnue ; `TestExtractDirectory` vérifie l’agrégation multilangage, le nombre de fichiers et la fusion des nœuds. `TestExtractEntry` couvre la forme sérialisée et les chemins invalides, tandis que `TestCLI` exécute la commande `ast-extract`, son mode `--pretty` et son erreur sur chemin absent.

Cette suite relie les trois niveaux publics de l’extracteur — fichier, répertoire et façade sérialisée — et protège leur contrat commun jusqu’à l’interface en ligne de commande. ^[inferred] Elle sert ainsi de validation transversale aux principaux hubs de la communauté AST Extraction. ^[inferred]

La couverture fonctionnelle des motifs de langage reste concentrée sur Python et JavaScript, alors que l’implémentation déclare de nombreux autres langages. ^[inferred]

## Voir aussi

- [[extract_file()]]
- [[extract_directory()]]
- [[extract()]]
