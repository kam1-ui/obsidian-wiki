---
node: tests_test_graph_analysis_page
title: "_page()"
community: "Graph Analysis Engine"
source_file: "tests/test_graph_analysis.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.0
---

# _page()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Graph Analysis Engine · **Fichier:** `tests/test_graph_analysis.py` · **Degré:** 10

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_graph_analysis.py]] `[EXTRACTED]` (L32)
- —references→ [[Path]] `[EXTRACTED]` (L32)
- ←rationale_for— [[Write a minimal wiki page with wikilinks.]] `[EXTRACTED]` (L33)
- ←calls— [[simple_vault()]] `[EXTRACTED]` (L52)
- ←calls— [[.test_connected_cluster_grouped()]] `[EXTRACTED]` (L169)
- ←calls— [[.test_links_to_nonexistent_pages_excluded()]] `[EXTRACTED]` (L89)
- ←calls— [[.test_self_links_ignored()]] `[EXTRACTED]` (L84)
- ←calls— [[.test_cross_community_edge_found()]] `[EXTRACTED]` (L193)
- ←calls— [[.test_no_intra_community_edges()]] `[EXTRACTED]` (L207)
- ←calls— [[.test_scores_positive()]] `[EXTRACTED]` (L215)
<!-- graphify:end -->

## Définition

`_page(vault: Path, name: str, links: list[str], tags: list[str] | None = None) -> Path` écrit une page Markdown minimale avec frontmatter `title`, tags optionnels, titre H1 et une ligne `[[wikilink]]` par lien fourni. La fonction écrit le fichier `<name>.md` dans le vault de test et retourne son `Path`.

Cette fabrique de fixture rend les tests de `parse_vault_graph()`, `detect_communities_greedy()` et `surprising_connections()` lisibles en exprimant directement la topologie des mini-vaults synthétiques. ^[inferred]

## Voir aussi

- [[tests_test_graph_analysis_testparsevaultgraph]]
- [[obsidian_wiki_graph_analysis_detect_communities_greedy]]
- [[obsidian_wiki_graph_analysis_surprising_connections]]
