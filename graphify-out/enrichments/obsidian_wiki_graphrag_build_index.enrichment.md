---
node: obsidian_wiki_graphrag_build_index
title: "build_index()"
community: "GraphRAG Query System"
source_file: "obsidian_wiki/graphrag.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.7
  inferred: 0.3
  ambiguous: 0.0
---

# build_index()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** GraphRAG Query System · **Fichier:** `obsidian_wiki/graphrag.py` · **Degré:** 25

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[graphrag.py]] `[EXTRACTED]` (L57)
- —calls→ [[_slug()]] `[EXTRACTED]` (L72)
- —references→ [[Path]] `[EXTRACTED]` (L57)
- ←calls— [[query()]] `[EXTRACTED]` (L293)
- ←rationale_for— [[Build a lightweight index dict from vault frontmatter and wikilinks.      Return]] `[EXTRACTED]` (L58)
- ←imports— [[test_graphrag.py]] `[EXTRACTED]` (L9)
- ←calls— [[.test_empty_vault()]] `[EXTRACTED]` (L100)
- ←calls— [[.test_in_links_reverse()]] `[EXTRACTED]` (L96)
- ←calls— [[.test_out_links()]] `[EXTRACTED]` (L92)
- ←calls— [[.test_reads_summary()]] `[EXTRACTED]` (L80)
- ←calls— [[.test_reads_tags()]] `[EXTRACTED]` (L84)
- ←calls— [[.test_reads_tier()]] `[EXTRACTED]` (L88)
- ←calls— [[.test_reads_title()]] `[EXTRACTED]` (L76)
- ←calls— [[.test_returns_slugs()]] `[EXTRACTED]` (L71)
- ←calls— [[.test_skips_raw_dir()]] `[EXTRACTED]` (L106)
- ←calls— [[.test_direct_link()]] `[EXTRACTED]` (L151)
- ←calls— [[.test_multi_hop()]] `[EXTRACTED]` (L171)
- ←calls— [[.test_no_path_returns_none()]] `[EXTRACTED]` (L179)
- ←calls— [[.test_same_node()]] `[EXTRACTED]` (L158)
- ←calls— [[.test_unknown_node_returns_none()]] `[EXTRACTED]` (L163)
- *…5 autres arêtes*
<!-- graphify:end -->

## Définition

`build_index(vault: Path)` construit un index léger du vault en deux passes sur tous les `.md` (hors `SKIP_DIRS`) : la première collecte slug, `title`, `tags`, `summary`, `category` et `tier` depuis le frontmatter (regex, pas de parseur YAML), la seconde résout les `out_links`/`in_links` par wikilinks. Retourne `{slug: {title, tags, summary, category, tier, out_links, in_links, path}}`.

C'est le point d'entrée de tout le sous-système GraphRAG : `query()` l'appelle avant chaque traversée, et l'intégralité de la suite `test_graphrag.py` s'appuie dessus (voir les arêtes `←calls—` ci-dessus). Le choix regex-sur-frontmatter plutôt qu'un vrai parseur YAML privilégie la robustesse aux vaults mal formés au détriment des cas YAML exotiques. ^[inferred]

Le slug est dérivé du nom de fichier seul (`_slug(page.stem)`) — deux pages de même nom dans des dossiers différents se cannibalisent dans l'index. ^[inferred]

## Voir aussi

- [[obsidian_wiki_graphrag_query.enrichment|query()]] — le consommateur principal de cet index
