---
node: obsidian_wiki_graph_analysis
title: "graph_analysis.py"
community: "Graph Analysis Engine"
source_file: "obsidian_wiki/graph_analysis.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.0
---

# graph_analysis.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Graph Analysis Engine · **Fichier:** `obsidian_wiki/graph_analysis.py` · **Degré:** 15

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[analyse_vault()]] `[EXTRACTED]` (L317)
- —contains→ [[_build_degree_tables()]] `[EXTRACTED]` (L116)
- —contains→ [[dead_ends()]] `[EXTRACTED]` (L140)
- —contains→ [[detect_communities()]] `[EXTRACTED]` (L220)
- —contains→ [[detect_communities_greedy()]] `[EXTRACTED]` (L176)
- —contains→ [[god_nodes()]] `[EXTRACTED]` (L130)
- —contains→ [[isolated()]] `[EXTRACTED]` (L145)
- —contains→ [[_label_community()]] `[EXTRACTED]` (L293)
- —contains→ [[_modularity()]] `[EXTRACTED]` (L155)
- —contains→ [[_page_slug()]] `[EXTRACTED]` (L51)
- —contains→ [[parse_vault_graph()]] `[EXTRACTED]` (L55)
- —contains→ [[_slug()]] `[EXTRACTED]` (L46)
- —contains→ [[surprising_connections()]] `[EXTRACTED]` (L248)
- ←rationale_for— [[Vault graph analysis: community detection, god nodes, surprising connections.  R]] `[EXTRACTED]` (L1)
- ←imports_from— [[test_graph_analysis.py]] `[EXTRACTED]` (L10)
<!-- graphify:end -->

## Définition

Module pur Python (stdlib uniquement : `json`, `math`, `re`, `collections`, `pathlib`) d'analyse du graphe de wikilinks d'un vault. Son docstring (L1-24) annonce trois analyses : classement des god nodes par degré, détection de communautés par modularité greedy (« equivalent to Leiden for small-to-medium graphs (<10k nodes) »), et « surprising connections » — les arêtes inter-communautés classées par improbabilité. La sortie est un JSON avec les clés `god_nodes`, `communities`, `surprising_connections`, `dead_ends`, `isolated`, `stats`. L'extra optionnel `obsidian-wiki[graph]` installe `leidenalg` + `igraph` pour le vrai algorithme Leiden ; sinon repli automatique sur la méthode greedy.

C'est le hub de la communauté « Graph Analysis Engine » : il contient tout le pipeline, de `parse_vault_graph()` (lecture des `.md`) aux métriques (`god_nodes()`, `dead_ends()`, `isolated()`), à la détection de communautés (`detect_communities()` / `detect_communities_greedy()`) et au point d'entrée `analyse_vault()`, consommé par la commande CLI `graph-analyse` et couvert intégralement par `tests/test_graph_analysis.py`. ^[inferred]

`_modularity()` (L155) est définie mais n'est appelée nulle part dans le module — code mort résiduel, probablement d'une variante antérieure de la détection greedy. ^[inferred]

## Voir aussi

- [[analyse_vault()]] — point d'entrée principal contenu dans ce module
- [[parse_vault_graph()]] — première étape du pipeline
- [[detect_communities_greedy()]] — repli pur Python de la détection de communautés
- [[test_graph_analysis.py]] — suite de tests dédiée
