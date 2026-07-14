---
node: obsidian_wiki_ast_extractor
title: "ast_extractor.py"
community: "AST Extraction"
source_file: "obsidian_wiki/ast_extractor.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# ast_extractor.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** AST Extraction · **Fichier:** `obsidian_wiki/ast_extractor.py` · **Degré:** 12

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[Edge]] `[EXTRACTED]` (L35)
- —contains→ [[extract()]] `[EXTRACTED]` (L379)
- —contains→ [[extract_directory()]] `[EXTRACTED]` (L355)
- —contains→ [[extract_file()]] `[EXTRACTED]` (L260)
- —contains→ [[_file_id()]] `[EXTRACTED]` (L255)
- —contains→ [[Graph]] `[EXTRACTED]` (L43)
- —contains→ [[LangSpec]] `[EXTRACTED]` (L112)
- —contains→ [[Node]] `[EXTRACTED]` (L25)
- —contains→ [[_os_walk()]] `[EXTRACTED]` (L349)
- —contains→ [[_walk_code_files()]] `[EXTRACTED]` (L340)
- ←rationale_for— [[Local AST-based code structure extractor.  Extracts classes, functions, and impo]] `[EXTRACTED]` (L1)
- ←imports_from— [[test_ast_extractor.py]] `[EXTRACTED]` (L10)
<!-- graphify:end -->

## Définition

Module d’extraction locale de structure de code fondé sur des expressions régulières, avec prise en charge optionnelle de tree-sitter et repli automatique. Il définit les modèles `Node`, `Edge` et `Graph`, les spécifications de langages, l’extraction d’un fichier ou d’un répertoire, puis un point d’entrée qui renvoie un dictionnaire sérialisable.

Il constitue le noyau de la communauté « AST Extraction » : ses primitives produisent le graphe de classes, fonctions, imports et héritages que la suite de tests valide. ^[inferred]

## Voir aussi

- [[TestExtractFile]]
