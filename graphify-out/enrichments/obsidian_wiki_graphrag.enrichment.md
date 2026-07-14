---
node: obsidian_wiki_graphrag
title: "graphrag.py"
community: "GraphRAG Query System"
source_file: "obsidian_wiki/graphrag.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.6
  inferred: 0.4
  ambiguous: 0.0
---

# graphrag.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** GraphRAG Query System · **Fichier:** `obsidian_wiki/graphrag.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[build_index()]] `[EXTRACTED]` (L57)
- —contains→ [[classify_query()]] `[EXTRACTED]` (L256)
- —contains→ [[find_path()]] `[EXTRACTED]` (L204)
- —contains→ [[query()]] `[EXTRACTED]` (L286)
- —contains→ [[rank_candidates()]] `[EXTRACTED]` (L179)
- —contains→ [[_score()]] `[EXTRACTED]` (L154)
- —contains→ [[_slug()]] `[EXTRACTED]` (L53)
- ←rationale_for— [[GraphRAG query index for wiki-query.  Builds a compact in-memory index from vaul]] `[EXTRACTED]` (L1)
- ←imports_from— [[test_graphrag.py]] `[EXTRACTED]` (L9)
<!-- graphify:end -->

## Définition

`graphrag.py` construit un index compact en mémoire à partir du frontmatter et des wikilinks d'un vault, puis répond à des requêtes structurelles ou factuelles sans ouvrir les corps de pages quand l'index suffit. Le module expose notamment `build_index()`, `_score()`, `rank_candidates()`, `find_path()`, `classify_query()` et `query()`.

Dans le graphe, ce fichier est le centre du système GraphRAG Query System parce qu'il relie extraction d'index, scoring, classification de question, recherche de chemin et format JSON de réponse pour la commande `graph-query`. ^[inferred]

Le module repose sur des regex et des heuristiques locales plutôt que sur un parseur YAML complet ou un moteur de recherche externe, ce qui simplifie l'exécution mais limite la couverture des formats de frontmatter et des requêtes complexes. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graphrag_rank_candidates]]
- [[obsidian_wiki_graphrag_find_path]]
- [[obsidian_wiki_graphrag_classify_query]]
- [[tests_test_graphrag_testbuildindex]]
- [[tests_test_graphrag_testquery]]
