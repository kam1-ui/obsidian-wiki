---
node: obsidian_wiki_graphrag_query
title: "query()"
community: "GraphRAG Query System"
source_file: "obsidian_wiki/graphrag.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.71
  inferred: 0.29
  ambiguous: 0.0
---

# query()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** GraphRAG Query System · **Fichier:** `obsidian_wiki/graphrag.py` · **Degré:** 19

### Connexions (EXTRACTED — depuis graph.json)
- ←imports— [[cli.py]] `[EXTRACTED]` (L622)
- ←calls— [[cmd_graph_query()]] `[EXTRACTED]` (L627)
- ←calls— [[cmd_query()]] `[EXTRACTED]` (L799)
- ←contains— [[graphrag.py]] `[EXTRACTED]` (L286)
- —calls→ [[_slug()]] `[EXTRACTED]` (L318)
- —calls→ [[build_index()]] `[EXTRACTED]` (L293)
- —references→ [[Path]] `[EXTRACTED]` (L286)
- —calls→ [[rank_candidates()]] `[EXTRACTED]` (L322)
- —calls→ [[find_path()]] `[EXTRACTED]` (L327)
- —calls→ [[classify_query()]] `[EXTRACTED]` (L305)
- —references→ [[Any]] `[EXTRACTED]` (L286)
- ←imports— [[test_graphrag.py]] `[EXTRACTED]` (L9)
- ←calls— [[.test_empty_vault()]] `[EXTRACTED]` (L243)
- ←calls— [[.test_finds_exact_match()]] `[EXTRACTED]` (L224)
- ←calls— [[.test_index_only_on_exact_with_summary()]] `[EXTRACTED]` (L233)
- ←calls— [[.test_json_serialisable()]] `[EXTRACTED]` (L248)
- ←calls— [[.test_path_query_populated()]] `[EXTRACTED]` (L229)
- ←calls— [[.test_returns_required_keys()]] `[EXTRACTED]` (L219)
- ←calls— [[.test_should_read_empty_when_index_only()]] `[EXTRACTED]` (L238)
<!-- graphify:end -->

## Définition

`query(vault: Path, question: str, *, top_n: int = 8, max_should_read: int = 3) -> dict[str, Any]` construit l'index GraphRAG du vault, renvoie une réponse vide en mode `index_only` si le vault est vide, classe la question avec `classify_query()`, calcule les god nodes pertinents, résout éventuellement un chemin entre deux termes, classe les candidats et produit un dictionnaire sérialisable. Sa sortie contient notamment `answer_type`, `candidates`, `path`, `god_nodes_relevant`, `should_read`, `index_only` et `stats`; `should_read` reste vide quand un titre exact avec résumé suffit à répondre depuis l'index.

Dans la communauté GraphRAG, `query()` est le point d'orchestration appelé par les commandes CLI et par les tests d'intégration. ^[inferred] Il assemble les fonctions spécialisées `build_index()`, `classify_query()`, `rank_candidates()` et `find_path()` en une décision exploitable par un agent : répondre depuis l'index ou lire quelques pages ciblées. ^[inferred]

La logique de lecture est heuristique : le seuil `score >= 10.0` avec résumé déclenche `index_only`, et les chemins trouvés peuvent élargir `should_read` jusqu'à `max_should_read + 2`. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graphrag_build_index|build_index()]]
- [[obsidian_wiki_graphrag_classify_query|classify_query()]]
- [[obsidian_wiki_graphrag_rank_candidates|rank_candidates()]]
- [[obsidian_wiki_graphrag_find_path|find_path()]]
- [[tests_test_graphrag|test_graphrag.py]]
