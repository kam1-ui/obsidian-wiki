---
type: community
members: 67
---

# Graph Analysis Engine

**Members:** 67 nodes

## Members
- [[.test_all_nodes_assigned()]] - code - tests/test_graph_analysis.py
- [[.test_all_pages_present_as_keys()]] - code - tests/test_graph_analysis.py
- [[.test_c_is_top_hub()]] - code - tests/test_graph_analysis.py
- [[.test_connected_cluster_grouped()]] - code - tests/test_graph_analysis.py
- [[.test_cross_community_edge_found()]] - code - tests/test_graph_analysis.py
- [[.test_dead_ends()]] - code - tests/test_graph_analysis.py
- [[.test_degree_sum()]] - code - tests/test_graph_analysis.py
- [[.test_empty_graph()]] - code - tests/test_graph_analysis.py
- [[.test_empty_vault()]] - code - tests/test_graph_analysis.py
- [[.test_empty_vault()_1]] - code - tests/test_graph_analysis.py
- [[.test_isolated()]] - code - tests/test_graph_analysis.py
- [[.test_json_serialisable()_1]] - code - tests/test_graph_analysis.py
- [[.test_links_to_nonexistent_pages_excluded()]] - code - tests/test_graph_analysis.py
- [[.test_missing_vault_exits_nonzero()]] - code - tests/test_graph_analysis.py
- [[.test_no_intra_community_edges()]] - code - tests/test_graph_analysis.py
- [[.test_no_overlap()]] - code - tests/test_graph_analysis.py
- [[.test_outputs_json()_1]] - code - tests/test_graph_analysis.py
- [[.test_pretty_flag()_1]] - code - tests/test_graph_analysis.py
- [[.test_reads_tags()]] - code - tests/test_graph_analysis.py
- [[.test_reads_wikilinks()]] - code - tests/test_graph_analysis.py
- [[.test_respects_top_n()]] - code - tests/test_graph_analysis.py
- [[.test_returns_all_keys()]] - code - tests/test_graph_analysis.py
- [[.test_returns_list_of_sets()]] - code - tests/test_graph_analysis.py
- [[.test_scores_positive()]] - code - tests/test_graph_analysis.py
- [[.test_self_links_ignored()]] - code - tests/test_graph_analysis.py
- [[.test_stats_correct()]] - code - tests/test_graph_analysis.py
- [[.test_top_flag()]] - code - tests/test_graph_analysis.py
- [[A → B → C     A → C     D (isolated)     E → F (dead-end cluster)]] - rationale - tests/test_graph_analysis.py
- [[Any_1]] - code
- [[Approximate modularity Q for an undirected projection of outgoing edges.]] - rationale - obsidian_wiki/graph_analysis.py
- [[Edges that cross community boundaries, ranked by unexpectedness.      Score = 1]] - rationale - obsidian_wiki/graph_analysis.py
- [[Greedy modularity community detection (label propagation variant).      Fast O(n]] - rationale - obsidian_wiki/graph_analysis.py
- [[Normalise a wikilink target to a page slug.]] - rationale - obsidian_wiki/graph_analysis.py
- [[Pages with no outgoing links.]] - rationale - obsidian_wiki/graph_analysis.py
- [[Pages with zero links in either direction.]] - rationale - obsidian_wiki/graph_analysis.py
- [[Parse all .md pages and return (outgoing_edges, page_tags).      outgoing_edges]] - rationale - obsidian_wiki/graph_analysis.py
- [[Path_11]] - code
- [[Path_16]] - code
- [[TestAnalyseVault]] - code - tests/test_graph_analysis.py
- [[TestCommunityDetection]] - code - tests/test_graph_analysis.py
- [[TestDeadEndsIsolated]] - code - tests/test_graph_analysis.py
- [[TestGodNodes]] - code - tests/test_graph_analysis.py
- [[TestGraphAnalyseCLI]] - code - tests/test_graph_analysis.py
- [[TestParseVaultGraph]] - code - tests/test_graph_analysis.py
- [[TestSurprisingConnections]] - code - tests/test_graph_analysis.py
- [[Tests for vault graph analysis community detection, god nodes, surprising conne]] - rationale - tests/test_graph_analysis.py
- [[Try Leiden (leidenalg + igraph) first; fall back to greedy label propagation.]] - rationale - obsidian_wiki/graph_analysis.py
- [[Vault graph analysis community detection, god nodes, surprising connections.  R]] - rationale - obsidian_wiki/graph_analysis.py
- [[Write a minimal wiki page with wikilinks.]] - rationale - tests/test_graph_analysis.py
- [[_build_degree_tables()]] - code - obsidian_wiki/graph_analysis.py
- [[_label_community()]] - code - obsidian_wiki/graph_analysis.py
- [[_modularity()]] - code - obsidian_wiki/graph_analysis.py
- [[_page()]] - code - tests/test_graph_analysis.py
- [[_page_slug()]] - code - obsidian_wiki/graph_analysis.py
- [[_slug()]] - code - obsidian_wiki/graph_analysis.py
- [[analyse_vault()]] - code - obsidian_wiki/graph_analysis.py
- [[dead_ends()]] - code - obsidian_wiki/graph_analysis.py
- [[detect_communities()]] - code - obsidian_wiki/graph_analysis.py
- [[detect_communities_greedy()]] - code - obsidian_wiki/graph_analysis.py
- [[god_nodes()]] - code - obsidian_wiki/graph_analysis.py
- [[graph_analysis.py]] - code - obsidian_wiki/graph_analysis.py
- [[isolated()]] - code - obsidian_wiki/graph_analysis.py
- [[parse_vault_graph()]] - code - obsidian_wiki/graph_analysis.py
- [[simple_vault()]] - code - tests/test_graph_analysis.py
- [[surprising_connections()]] - code - obsidian_wiki/graph_analysis.py
- [[test_graph_analysis.py]] - code - tests/test_graph_analysis.py
- [[vault()_2]] - code - tests/test_graph_analysis.py

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Graph_Analysis_Engine
SORT file.name ASC
```

## Connections to other communities
- 2 edges to [[_COMMUNITY_CLI Command Layer]]

## Top bridge nodes
- [[analyse_vault()]] - degree 17, connects to 1 community