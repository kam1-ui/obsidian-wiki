---
node: tests_test_graphrag_testbuildindex
title: "TestBuildIndex"
community: "GraphRAG Query System"
source_file: "tests/test_graphrag.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.7
  inferred: 0.3
  ambiguous: 0.0
---

# TestBuildIndex

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** GraphRAG Query System · **Fichier:** `tests/test_graphrag.py` · **Degré:** 10

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_graphrag.py]] `[EXTRACTED]` (L69)
- —method→ [[.test_empty_vault()]] `[EXTRACTED]` (L99)
- —method→ [[.test_in_links_reverse()]] `[EXTRACTED]` (L95)
- —method→ [[.test_out_links()]] `[EXTRACTED]` (L91)
- —method→ [[.test_reads_summary()]] `[EXTRACTED]` (L79)
- —method→ [[.test_reads_tags()]] `[EXTRACTED]` (L83)
- —method→ [[.test_reads_tier()]] `[EXTRACTED]` (L87)
- —method→ [[.test_reads_title()]] `[EXTRACTED]` (L75)
- —method→ [[.test_returns_slugs()]] `[EXTRACTED]` (L70)
- —method→ [[.test_skips_raw_dir()]] `[EXTRACTED]` (L103)
<!-- graphify:end -->

## Définition

`TestBuildIndex` est une classe de tests pytest pour `build_index()`. Ses méthodes vérifient que l'index retourne les slugs attendus, lit le titre, le résumé, les tags et le tier, reconstruit les liens sortants et entrants, retourne `{}` pour un vault vide, et ignore le répertoire `_raw`.

Dans la communauté GraphRAG, cette classe verrouille le contrat minimal de l'index en mémoire consommé ensuite par `rank_candidates()`, `find_path()` et `query()`. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graphrag]]
- [[obsidian_wiki_graphrag_rank_candidates]]
- [[obsidian_wiki_graphrag_find_path]]
- [[tests_test_graphrag_testquery]]
