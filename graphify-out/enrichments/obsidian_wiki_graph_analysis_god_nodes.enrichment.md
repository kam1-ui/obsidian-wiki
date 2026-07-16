---
node: obsidian_wiki_graph_analysis_god_nodes
title: "god_nodes()"
community: "Graph Analysis Engine"
source_file: "obsidian_wiki/graph_analysis.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.65
  inferred: 0.35
  ambiguous: 0.0
---

# god_nodes()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Graph Analysis Engine · **Fichier:** `obsidian_wiki/graph_analysis.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[graph_analysis.py]] `[EXTRACTED]` (L130)
- —calls→ [[_build_degree_tables()]] `[EXTRACTED]` (L131)
- ←calls— [[analyse_vault()]] `[EXTRACTED]` (L334)
- ←imports— [[test_graph_analysis.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_c_is_top_hub()]] `[EXTRACTED]` (L101)
- ←calls— [[.test_degree_sum()]] `[EXTRACTED]` (L108)
- ←calls— [[.test_respects_top_n()]] `[EXTRACTED]` (L114)
<!-- graphify:end -->

## Définition

`god_nodes(outgoing: dict[str, list[str]], top_n: int = 20) -> list[dict]` calcule les degrés via `_build_degree_tables()`, trie les pages par degré total décroissant et retourne pour chacune `page`, `degree`, `in_degree` et `out_degree`. Le résultat est limité aux `top_n` premiers nœuds.

Dans `analyse_vault()`, ce nœud produit la liste des hubs du vault, utile pour repérer les pages qui concentrent le plus de liens entrants et sortants. ^[inferred]

La métrique est purement fondée sur le degré, donc elle mesure la centralité de liens sans distinguer la qualité sémantique ou la fraîcheur des pages. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graph_analysis_surprising_connections]]
- [[obsidian_wiki_graph_analysis_detect_communities_greedy]]
- [[tests_test_graph_analysis_testparsevaultgraph]]
