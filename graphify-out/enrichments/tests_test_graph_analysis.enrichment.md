---
node: tests_test_graph_analysis
title: "test_graph_analysis.py"
community: "Graph Analysis Engine"
source_file: "tests/test_graph_analysis.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# test_graph_analysis.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Graph Analysis Engine · **Fichier:** `tests/test_graph_analysis.py` · **Degré:** 19

### Connexions (EXTRACTED — depuis graph.json)
- —imports_from→ [[graph_analysis.py]] `[EXTRACTED]` (L10)
- —imports→ [[parse_vault_graph()]] `[EXTRACTED]` (L10)
- —imports→ [[god_nodes()]] `[EXTRACTED]` (L10)
- —imports→ [[dead_ends()]] `[EXTRACTED]` (L10)
- —imports→ [[isolated()]] `[EXTRACTED]` (L10)
- —imports→ [[detect_communities_greedy()]] `[EXTRACTED]` (L10)
- —imports→ [[surprising_connections()]] `[EXTRACTED]` (L10)
- —imports→ [[analyse_vault()]] `[EXTRACTED]` (L10)
- —contains→ [[_page()]] `[EXTRACTED]` (L32)
- —contains→ [[simple_vault()]] `[EXTRACTED]` (L45)
- —contains→ [[TestAnalyseVault]] `[EXTRACTED]` (L230)
- —contains→ [[TestCommunityDetection]] `[EXTRACTED]` (L142)
- —contains→ [[TestDeadEndsIsolated]] `[EXTRACTED]` (L122)
- —contains→ [[TestGodNodes]] `[EXTRACTED]` (L98)
- —contains→ [[TestGraphAnalyseCLI]] `[EXTRACTED]` (L256)
- —contains→ [[TestParseVaultGraph]] `[EXTRACTED]` (L65)
- —contains→ [[TestSurprisingConnections]] `[EXTRACTED]` (L190)
- —contains→ [[vault()]] `[EXTRACTED]` (L26)
- ←rationale_for— [[Tests for vault graph analysis: community detection, god nodes, surprising conne]] `[EXTRACTED]` (L1)
<!-- graphify:end -->

## Définition

`tests/test_graph_analysis.py` est la suite pytest qui couvre l'analyse de graphe de vault : parsing des wikilinks et tags, calcul des hubs, détection des dead ends et isolés, communautés, connexions surprenantes, intégration `analyse_vault()` et commande CLI `graph-analyse`. Elle construit des vaults Markdown synthétiques avec `_page()` et `simple_vault()` pour vérifier les cas nominaux, les graphes vides, les self-links ignorés, les liens vers pages inexistantes exclus, la sérialisation JSON et les erreurs de chemin manquant.

Dans le graphe, ce fichier est central parce qu'il importe presque toute l'API de `obsidian_wiki.graph_analysis` et relie les helpers bas niveau au point d'entrée `analyse_vault()` et à la CLI. ^[inferred] Sa centralité indique que le comportement attendu du moteur d'analyse est principalement spécifié par des fixtures minimales et des assertions de structure plutôt que par des tests sur un vault réel. ^[inferred]

La couverture visible vérifie surtout les invariants de sortie, la présence de clés et quelques propriétés de scoring, mais elle ne fige pas précisément la composition des communautés ni l'ordre complet des résultats. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graph_analysis_analyse_vault|analyse_vault()]]
- [[obsidian_wiki_graph_analysis_parse_vault_graph|parse_vault_graph()]]
- [[obsidian_wiki_graph_analysis_god_nodes|god_nodes()]]
- [[obsidian_wiki_graph_analysis_detect_communities_greedy|detect_communities_greedy()]]
- [[obsidian_wiki_graph_analysis_surprising_connections|surprising_connections()]]
