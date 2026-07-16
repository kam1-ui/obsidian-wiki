---
node: obsidian_wiki_graph_analysis_detect_communities_greedy
title: "detect_communities_greedy()"
community: "Graph Analysis Engine"
source_file: "obsidian_wiki/graph_analysis.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.6
  inferred: 0.4
  ambiguous: 0.0
---

# detect_communities_greedy()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Graph Analysis Engine · **Fichier:** `obsidian_wiki/graph_analysis.py` · **Degré:** 11

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[graph_analysis.py]] `[EXTRACTED]` (L176)
- ←calls— [[detect_communities()]] `[EXTRACTED]` (L241)
- ←rationale_for— [[Greedy modularity community detection (label propagation variant).      Fast O(n]] `[EXTRACTED]` (L177)
- ←imports— [[test_graph_analysis.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_all_nodes_assigned()]] `[EXTRACTED]` (L152)
- ←calls— [[.test_connected_cluster_grouped()]] `[EXTRACTED]` (L176)
- ←calls— [[.test_empty_graph()]] `[EXTRACTED]` (L182)
- ←calls— [[.test_no_overlap()]] `[EXTRACTED]` (L161)
- ←calls— [[.test_returns_list_of_sets()]] `[EXTRACTED]` (L145)
- ←calls— [[.test_cross_community_edge_found()]] `[EXTRACTED]` (L200)
- ←calls— [[.test_scores_positive()]] `[EXTRACTED]` (L220)
<!-- graphify:end -->

## Définition

`detect_communities_greedy(outgoing: dict[str, list[str]]) -> list[set[str]]` applique une détection de communautés par propagation d'étiquettes sur une projection non orientée du graphe de wikilinks. Elle retourne `[]` pour un graphe vide, initialise chaque nœud avec sa propre étiquette, itère au plus 20 tours, puis groupe les nœuds par étiquette finale.

Ce nœud est le repli pur Python de `detect_communities()` quand `igraph` ou `leidenalg` ne sont pas disponibles, et il alimente ensuite les communautés utilisées par `analyse_vault()` et `surprising_connections()`. ^[inferred]

La stratégie privilégie une approximation rapide adaptée aux vaults modestes plutôt qu'une modularité Leiden exacte, donc l'ordre des nœuds et les choix de labels peuvent influencer les clusters produits. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graph_analysis_surprising_connections]]
- [[tests_test_graph_analysis_page]]
- [[tests_test_graph_analysis_testparsevaultgraph]]
