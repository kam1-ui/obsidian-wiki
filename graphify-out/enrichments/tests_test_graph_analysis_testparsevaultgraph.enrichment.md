---
node: tests_test_graph_analysis_testparsevaultgraph
title: "TestParseVaultGraph"
community: "Graph Analysis Engine"
source_file: "tests/test_graph_analysis.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.7
  inferred: 0.3
  ambiguous: 0.0
---

# TestParseVaultGraph

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Graph Analysis Engine · **Fichier:** `tests/test_graph_analysis.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_graph_analysis.py]] `[EXTRACTED]` (L65)
- —method→ [[.test_all_pages_present_as_keys()]] `[EXTRACTED]` (L71)
- —method→ [[.test_empty_vault()]] `[EXTRACTED]` (L79)
- —method→ [[.test_links_to_nonexistent_pages_excluded()]] `[EXTRACTED]` (L88)
- —method→ [[.test_reads_tags()]] `[EXTRACTED]` (L75)
- —method→ [[.test_reads_wikilinks()]] `[EXTRACTED]` (L66)
- —method→ [[.test_self_links_ignored()]] `[EXTRACTED]` (L83)
<!-- graphify:end -->

## Définition

`TestParseVaultGraph` est une classe de tests pytest pour `parse_vault_graph()`. Elle vérifie la lecture des wikilinks, la présence de toutes les pages comme clés, l'extraction des tags, le retour de structures vides pour un vault vide, l'ignorance des liens vers soi-même et l'exclusion des liens vers des pages inexistantes.

Dans la communauté Graph Analysis Engine, cette classe fixe le contrat d'entrée de tout le pipeline d'analyse : les fonctions de degrés, communautés et connexions surprenantes dépendent du dictionnaire `outgoing` produit par `parse_vault_graph()`. ^[inferred]

## Voir aussi

- [[tests_test_graph_analysis_page]]
- [[obsidian_wiki_graph_analysis_god_nodes]]
- [[obsidian_wiki_graph_analysis_detect_communities_greedy]]
- [[obsidian_wiki_graph_analysis_surprising_connections]]
