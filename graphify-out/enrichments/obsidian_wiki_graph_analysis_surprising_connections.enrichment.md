---
node: obsidian_wiki_graph_analysis_surprising_connections
title: "surprising_connections()"
community: "Graph Analysis Engine"
source_file: "obsidian_wiki/graph_analysis.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.65
  inferred: 0.35
  ambiguous: 0.0
---

# surprising_connections()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Graph Analysis Engine · **Fichier:** `obsidian_wiki/graph_analysis.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[graph_analysis.py]] `[EXTRACTED]` (L248)
- ←calls— [[analyse_vault()]] `[EXTRACTED]` (L344)
- ←rationale_for— [[Edges that cross community boundaries, ranked by unexpectedness.      Score = 1]] `[EXTRACTED]` (L253)
- ←imports— [[test_graph_analysis.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_cross_community_edge_found()]] `[EXTRACTED]` (L201)
- ←calls— [[.test_no_intra_community_edges()]] `[EXTRACTED]` (L211)
- ←calls— [[.test_scores_positive()]] `[EXTRACTED]` (L221)
<!-- graphify:end -->

## Définition

`surprising_connections(outgoing: dict[str, list[str]], communities: list[set[str]], top_n: int = 20) -> list[dict]` retourne des arêtes qui traversent les frontières de communautés. Elle construit une table `node_comm`, compte les degrés inter-communautés, déduplique les paires non orientées, calcule `1.0 / sqrt(cd_s * cd_t)`, trie par score décroissant et limite le résultat à `top_n`.

Cette fonction transforme les communautés détectées en signaux d'audit : `analyse_vault()` l'utilise pour lister les liens qui relient des zones autrement séparées du vault. ^[inferred]

Le score favorise les ponts rares entre communautés et peut donc sous-classer des pages très connectées même si elles portent des relations importantes. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graph_analysis_detect_communities_greedy]]
- [[obsidian_wiki_graph_analysis_god_nodes]]
- [[tests_test_graph_analysis_page]]
- [[tests_test_graph_analysis_testparsevaultgraph]]
