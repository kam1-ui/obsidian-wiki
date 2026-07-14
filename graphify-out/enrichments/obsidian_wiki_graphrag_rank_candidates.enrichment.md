---
node: obsidian_wiki_graphrag_rank_candidates
title: "rank_candidates()"
community: "GraphRAG Query System"
source_file: "obsidian_wiki/graphrag.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.65
  inferred: 0.35
  ambiguous: 0.0
---

# rank_candidates()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** GraphRAG Query System · **Fichier:** `obsidian_wiki/graphrag.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[graphrag.py]] `[EXTRACTED]` (L179)
- —calls→ [[_score()]] `[EXTRACTED]` (L189)
- ←calls— [[query()]] `[EXTRACTED]` (L322)
- ←imports— [[test_graphrag.py]] `[EXTRACTED]` (L9)
- ←calls— [[.test_core_tier_boosted()]] `[EXTRACTED]` (L133)
- ←calls— [[.test_exact_title_match_scores_highest()]] `[EXTRACTED]` (L117)
- ←calls— [[.test_no_match_returns_empty()]] `[EXTRACTED]` (L128)
- ←calls— [[.test_respects_top_n()]] `[EXTRACTED]` (L141)
- ←calls— [[.test_tag_match_included()]] `[EXTRACTED]` (L122)
<!-- graphify:end -->

## Définition

`rank_candidates(index: dict[str, dict], terms: list[str], top_n: int = 8) -> list[dict]` score chaque entrée d'index avec `_score()`, conserve le slug, le chemin de page, le titre, le résumé, le tier et le degré entrant, puis trie par score décroissant et degré entrant décroissant. La fonction retourne au plus `top_n` candidats dont le score est strictement positif.

Ce nœud est le filtre de pertinence central de GraphRAG : `query()` l'utilise pour choisir les candidats à exposer, et aussi pour résoudre un terme de chemin vers un slug quand la correspondance exacte échoue. ^[inferred]

Le classement dépend des champs frontmatter et liens déjà extraits par `build_index()`, donc une page sans titre, résumé, tags ou liens informatifs aura peu de chances de remonter. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graphrag]]
- [[obsidian_wiki_graphrag_find_path]]
- [[obsidian_wiki_graphrag_classify_query]]
- [[tests_test_graphrag_testbuildindex]]
- [[tests_test_graphrag_testquery]]
