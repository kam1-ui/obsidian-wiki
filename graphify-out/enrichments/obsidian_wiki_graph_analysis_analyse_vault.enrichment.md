---
node: obsidian_wiki_graph_analysis_analyse_vault
title: "analyse_vault()"
community: "Graph Analysis Engine"
source_file: "obsidian_wiki/graph_analysis.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.0
---

# analyse_vault()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Graph Analysis Engine · **Fichier:** `obsidian_wiki/graph_analysis.py` · **Degré:** 17

### Connexions (EXTRACTED — depuis graph.json)
- ←imports— [[cli.py]] `[EXTRACTED]` (L658)
- ←calls— [[cmd_graph_analyse()]] `[EXTRACTED]` (L663)
- ←contains— [[graph_analysis.py]] `[EXTRACTED]` (L317)
- —references→ [[Path]] `[EXTRACTED]` (L317)
- —calls→ [[parse_vault_graph()]] `[EXTRACTED]` (L318)
- —calls→ [[god_nodes()]] `[EXTRACTED]` (L334)
- —calls→ [[dead_ends()]] `[EXTRACTED]` (L345)
- —calls→ [[isolated()]] `[EXTRACTED]` (L346)
- —calls→ [[detect_communities()]] `[EXTRACTED]` (L327)
- —calls→ [[surprising_connections()]] `[EXTRACTED]` (L344)
- —calls→ [[_label_community()]] `[EXTRACTED]` (L340)
- —references→ [[Any]] `[EXTRACTED]` (L317)
- ←imports— [[test_graph_analysis.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_empty_vault()]] `[EXTRACTED]` (L244)
- ←calls— [[.test_json_serialisable()]] `[EXTRACTED]` (L248)
- ←calls— [[.test_returns_all_keys()]] `[EXTRACTED]` (L232)
- ←calls— [[.test_stats_correct()]] `[EXTRACTED]` (L239)
<!-- graphify:end -->

## Définition

`analyse_vault(vault: Path, top_n: int = 20) -> dict[str, Any]` parse le graphe du vault avec `parse_vault_graph()`, renvoie des listes vides et des stats à zéro si aucun nœud n'est trouvé, puis calcule les communautés, les hubs, les connexions surprenantes, les dead ends, les pages isolées et les statistiques globales. Pour chaque communauté, il fournit un `id`, une `size`, la liste triée des `pages` et un `label` produit par `_label_community()`.

Ce nœud est le point d'entrée agrégé du moteur d'analyse de graphe : il transforme les primitives du module en rapport JSON consommable par la CLI et vérifié par `tests/test_graph_analysis.py`. ^[inferred] Sa position de hub vient du fait qu'il appelle presque toutes les fonctions analytiques du module et normalise leurs résultats en une structure unique. ^[inferred]

La source trie les communautés par taille avant de les numéroter, donc les `id` sont des identifiants de rang dans le résultat courant plutôt que des identifiants stables de communauté. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graph_analysis_parse_vault_graph|parse_vault_graph()]]
- [[obsidian_wiki_graph_analysis_god_nodes|god_nodes()]]
- [[obsidian_wiki_graph_analysis_surprising_connections|surprising_connections()]]
- [[tests_test_graph_analysis|test_graph_analysis.py]]
