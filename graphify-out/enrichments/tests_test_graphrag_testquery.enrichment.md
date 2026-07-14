---
node: tests_test_graphrag_testquery
title: "TestQuery"
community: "GraphRAG Query System"
source_file: "tests/test_graphrag.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.7
  inferred: 0.3
  ambiguous: 0.0
---

# TestQuery

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** GraphRAG Query System · **Fichier:** `tests/test_graphrag.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_graphrag.py]] `[EXTRACTED]` (L217)
- —method→ [[.test_empty_vault()]] `[EXTRACTED]` (L242)
- —method→ [[.test_finds_exact_match()]] `[EXTRACTED]` (L223)
- —method→ [[.test_index_only_on_exact_with_summary()]] `[EXTRACTED]` (L232)
- —method→ [[.test_json_serialisable()]] `[EXTRACTED]` (L247)
- —method→ [[.test_path_query_populated()]] `[EXTRACTED]` (L228)
- —method→ [[.test_returns_required_keys()]] `[EXTRACTED]` (L218)
- —method→ [[.test_should_read_empty_when_index_only()]] `[EXTRACTED]` (L237)
<!-- graphify:end -->

## Définition

`TestQuery` est une classe de tests d'intégration pour `query()`. Elle vérifie la présence des clés de sortie requises, la remontée d'un candidat exact, la classification d'une requête de chemin, le mode `index_only` pour un titre exact avec résumé, l'absence de `should_read` dans ce cas, le comportement sur vault vide et la sérialisabilité JSON.

Cette classe protège le contrat de sortie consommé par les agents : `answer_type`, `candidates`, `path`, `god_nodes_relevant`, `should_read` et `index_only`. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graphrag]]
- [[obsidian_wiki_graphrag_classify_query]]
- [[obsidian_wiki_graphrag_find_path]]
- [[obsidian_wiki_graphrag_rank_candidates]]
- [[tests_test_graphrag_testbuildindex]]
