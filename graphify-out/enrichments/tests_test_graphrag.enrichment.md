---
node: tests_test_graphrag
title: "test_graphrag.py"
community: "GraphRAG Query System"
source_file: "tests/test_graphrag.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# test_graphrag.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** GraphRAG Query System · **Fichier:** `tests/test_graphrag.py` · **Degré:** 16

### Connexions (EXTRACTED — depuis graph.json)
- —imports_from→ [[graphrag.py]] `[EXTRACTED]` (L9)
- —imports→ [[build_index()]] `[EXTRACTED]` (L9)
- —imports→ [[rank_candidates()]] `[EXTRACTED]` (L9)
- —imports→ [[find_path()]] `[EXTRACTED]` (L9)
- —imports→ [[classify_query()]] `[EXTRACTED]` (L9)
- —imports→ [[query()]] `[EXTRACTED]` (L9)
- —contains→ [[_page()]] `[EXTRACTED]` (L29)
- —contains→ [[simple_vault()]] `[EXTRACTED]` (L49)
- —contains→ [[TestBuildIndex]] `[EXTRACTED]` (L69)
- —contains→ [[TestClassifyQuery]] `[EXTRACTED]` (L188)
- —contains→ [[TestFindPath]] `[EXTRACTED]` (L149)
- —contains→ [[TestGraphQueryCLI]] `[EXTRACTED]` (L256)
- —contains→ [[TestQuery]] `[EXTRACTED]` (L217)
- —contains→ [[TestRankCandidates]] `[EXTRACTED]` (L114)
- —contains→ [[vault()]] `[EXTRACTED]` (L23)
- ←rationale_for— [[Tests for the GraphRAG query index module.]] `[EXTRACTED]` (L1)
<!-- graphify:end -->

## Définition

`tests/test_graphrag.py` est la suite pytest du module d'index et de requête GraphRAG. Elle crée un vault synthétique de pages Markdown avec frontmatter, résumés, tags, tiers et wikilinks, puis teste `build_index()`, `rank_candidates()`, `find_path()`, `classify_query()`, `query()` et la commande CLI `graph-query`.

Dans le graphe, ce fichier sert de spécification comportementale pour le système de requête : il relie les fonctions unitaires, le point d'entrée `query()` et l'interface CLI autour des mêmes fixtures. ^[inferred] Les cas testés établissent les garanties principales attendues par un agent consommateur : index JSON-sérialisable, scoring orienté titre/tag/tier, chemins multi-hop, classification de questions et décision `index_only`. ^[inferred]

La couverture visible ne valide pas le texte d'une réponse finale ; elle vérifie plutôt les candidats, chemins, clés de sortie et décisions de lecture que d'autres couches peuvent ensuite utiliser. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graphrag_query|query()]]
- [[obsidian_wiki_graphrag_build_index|build_index()]]
- [[obsidian_wiki_graphrag_rank_candidates|rank_candidates()]]
- [[obsidian_wiki_graphrag_find_path|find_path()]]
- [[obsidian_wiki_graphrag_classify_query|classify_query()]]
