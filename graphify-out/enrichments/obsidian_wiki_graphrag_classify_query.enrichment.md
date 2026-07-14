---
node: obsidian_wiki_graphrag_classify_query
title: "classify_query()"
community: "GraphRAG Query System"
source_file: "obsidian_wiki/graphrag.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.65
  inferred: 0.35
  ambiguous: 0.0
---

# classify_query()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** GraphRAG Query System · **Fichier:** `obsidian_wiki/graphrag.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[graphrag.py]] `[EXTRACTED]` (L256)
- ←calls— [[query()]] `[EXTRACTED]` (L305)
- ←rationale_for— [[Return (answer_type, extracted_terms).      answer_type: "path" | "gap" | "list"]] `[EXTRACTED]` (L257)
- ←imports— [[test_graphrag.py]] `[EXTRACTED]` (L9)
- ←calls— [[.test_direct_query()]] `[EXTRACTED]` (L190)
- ←calls— [[.test_gap_query()]] `[EXTRACTED]` (L200)
- ←calls— [[.test_list_query()]] `[EXTRACTED]` (L204)
- ←calls— [[.test_path_query()]] `[EXTRACTED]` (L195)
- ←calls— [[.test_stop_words_filtered()]] `[EXTRACTED]` (L208)
<!-- graphify:end -->

## Définition

`classify_query(question: str) -> tuple[str, list[str]]` classe une question en `"path"`, `"gap"`, `"list"` ou `"direct"` et extrait les termes associés. Elle utilise des expressions régulières pour les chemins, les lacunes et les listes, puis applique par défaut un filtrage simple de stop words pour produire des termes de requête directe.

Cette fonction décide quelle branche de `query()` sera activée : recherche de chemin avec `find_path()`, classement standard avec `rank_candidates()`, ou réponse de type gap/list. ^[inferred]

Les règles sont heuristiques et anglophones, donc des formulations hors patrons ou dans une autre langue risquent d'être traitées comme requêtes directes. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graphrag]]
- [[obsidian_wiki_graphrag_find_path]]
- [[obsidian_wiki_graphrag_rank_candidates]]
- [[tests_test_graphrag_testquery]]
