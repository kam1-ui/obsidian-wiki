---
node: obsidian_wiki_graph_analysis_parse_vault_graph
title: "parse_vault_graph()"
community: "Graph Analysis Engine"
source_file: "obsidian_wiki/graph_analysis.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# parse_vault_graph()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Graph Analysis Engine · **Fichier:** `obsidian_wiki/graph_analysis.py` · **Degré:** 26

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[graph_analysis.py]] `[EXTRACTED]` (L55)
- —calls→ [[_slug()]] `[EXTRACTED]` (L91)
- —calls→ [[_page_slug()]] `[EXTRACTED]` (L71)
- —references→ [[Path]] `[EXTRACTED]` (L55)
- ←calls— [[analyse_vault()]] `[EXTRACTED]` (L318)
- ←rationale_for— [[Parse all .md pages and return (outgoing_edges, page_tags).      outgoing_edges:]] `[EXTRACTED]` (L56)
- ←imports— [[test_graph_analysis.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_all_nodes_assigned()]] `[EXTRACTED]` (L151)
- ←calls— [[.test_connected_cluster_grouped()]] `[EXTRACTED]` (L175)
- ←calls— [[.test_empty_graph()]] `[EXTRACTED]` (L181)
- ←calls— [[.test_no_overlap()]] `[EXTRACTED]` (L160)
- ←calls— [[.test_returns_list_of_sets()]] `[EXTRACTED]` (L144)
- ←calls— [[.test_dead_ends()]] `[EXTRACTED]` (L124)
- ←calls— [[.test_isolated()]] `[EXTRACTED]` (L131)
- ←calls— [[.test_c_is_top_hub()]] `[EXTRACTED]` (L100)
- ←calls— [[.test_degree_sum()]] `[EXTRACTED]` (L107)
- ←calls— [[.test_respects_top_n()]] `[EXTRACTED]` (L113)
- ←calls— [[.test_all_pages_present_as_keys()]] `[EXTRACTED]` (L72)
- ←calls— [[.test_empty_vault()]] `[EXTRACTED]` (L80)
- ←calls— [[.test_links_to_nonexistent_pages_excluded()]] `[EXTRACTED]` (L90)
- *…6 autres arêtes*
<!-- graphify:end -->

## Définition

`parse_vault_graph(vault: Path)` parcourt les fichiers Markdown d'un vault et retourne deux dictionnaires: `outgoing_edges` de slug source vers slugs cibles, et `page_tags` de slug vers tags. Il ignore les répertoires `_raw`, `_archived`, `_staging`, `_archives` et `.obsidian`, calcule les slugs connus avec `_page_slug()`, lit chaque page en UTF-8 avec remplacement d'erreurs, extrait les tags frontmatter sous forme inline ou liste, puis ajoute les wikilinks et liens Markdown `.md` seulement si la cible existe dans le vault.

Cette fonction est le parseur de base de l'engine d'analyse: `analyse_vault()` l'appelle avant de calculer god nodes, communautés, connexions surprenantes, dead ends, isolés et statistiques.^[inferred] Elle est centrale dans le graphe parce que les tests de `graph_analysis` vérifient directement ses garanties structurantes: graphe vide, clés présentes pour toutes les pages, exclusion des liens vers pages inexistantes et compatibilité avec les métriques en aval.^[inferred]

La normalisation réduit chaque page à `path.stem` et chaque cible de wikilink au dernier segment, donc deux pages de dossiers différents mais de même nom se confondent dans le graphe.^[inferred] Le parseur ne résout pas non plus les ancres, alias ou chemins complets au-delà de cette réduction, ce qui privilégie un graphe simple de pages connues plutôt qu'une représentation fidèle de tous les liens Obsidian.^[inferred]
