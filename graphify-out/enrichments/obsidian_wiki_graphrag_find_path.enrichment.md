---
node: obsidian_wiki_graphrag_find_path
title: "find_path()"
community: "GraphRAG Query System"
source_file: "obsidian_wiki/graphrag.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.65
  inferred: 0.35
  ambiguous: 0.0
---

# find_path()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** GraphRAG Query System · **Fichier:** `obsidian_wiki/graphrag.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[graphrag.py]] `[EXTRACTED]` (L204)
- ←calls— [[query()]] `[EXTRACTED]` (L327)
- ←rationale_for— [[BFS shortest path from source to target through wikilinks.]] `[EXTRACTED]` (L210)
- ←imports— [[test_graphrag.py]] `[EXTRACTED]` (L9)
- ←calls— [[.test_direct_link()]] `[EXTRACTED]` (L152)
- ←calls— [[.test_multi_hop()]] `[EXTRACTED]` (L172)
- ←calls— [[.test_no_path_returns_none()]] `[EXTRACTED]` (L180)
- ←calls— [[.test_same_node()]] `[EXTRACTED]` (L159)
- ←calls— [[.test_unknown_node_returns_none()]] `[EXTRACTED]` (L164)
<!-- graphify:end -->

## Définition

`find_path(index: dict[str, dict], source_slug: str, target_slug: str, max_depth: int = 4) -> list[str] | None` cherche par BFS le plus court chemin entre deux slugs à travers les `out_links` et `in_links`. Elle retourne `None` si la source ou la cible est absente, retourne `[source_slug]` pour un nœud identique, et arrête l'exploration au-delà de `max_depth`.

Dans GraphRAG, `query()` appelle cette fonction pour peupler le champ `path` des questions classées comme demandes de connexion entre deux notions. ^[inferred]

Comme la recherche traverse les liens entrants et sortants, le chemin obtenu décrit une connexion non orientée du graphe de pages plutôt qu'un parcours strictement sortant. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graphrag]]
- [[obsidian_wiki_graphrag_classify_query]]
- [[obsidian_wiki_graphrag_rank_candidates]]
- [[tests_test_graphrag_testquery]]
