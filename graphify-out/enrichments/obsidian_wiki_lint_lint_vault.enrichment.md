---
node: obsidian_wiki_lint_lint_vault
title: "lint_vault()"
community: "Wiki Lint Checks"
source_file: "obsidian_wiki/lint.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.6
  inferred: 0.4
  ambiguous: 0.0
---

# lint_vault()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Wiki Lint Checks · **Fichier:** `obsidian_wiki/lint.py` · **Degré:** 11

### Connexions (EXTRACTED — depuis graph.json)
- ←imports— [[cli.py]] `[EXTRACTED]` (L743)
- ←calls— [[cmd_lint()]] `[EXTRACTED]` (L755)
- ←contains— [[lint.py]] `[EXTRACTED]` (L87)
- —calls→ [[_iter_pages()]] `[EXTRACTED]` (L88)
- —references→ [[Path]] `[EXTRACTED]` (L87)
- —calls→ [[_parse_page()]] `[EXTRACTED]` (L88)
- —references→ [[Any]] `[EXTRACTED]` (L87)
- ←imports— [[test_lint.py]] `[EXTRACTED]` (L11)
- ←calls— [[test_lint_vault_fails_on_broken_links_and_missing_frontmatter()]] `[EXTRACTED]` (L83)
- ←calls— [[test_lint_vault_passes_clean_graph()]] `[EXTRACTED]` (L71)
- ←calls— [[test_lint_vault_warns_on_duplicates_missing_summaries_and_orphans()]] `[EXTRACTED]` (L95)
<!-- graphify:end -->

## Définition

`lint_vault(vault: Path) -> dict[str, Any]` parcourt les pages Markdown hors répertoires exclus, les analyse, résout leurs wikiliens et liens Markdown par slug, puis collecte les liens cassés, champs de frontmatter requis absents, titres dupliqués, résumés manquants et pages orphelines. Il renvoie un rapport structuré contenant ces listes, le nombre de pages et de liens, ainsi qu’un statut `fail` pour les liens cassés ou frontmatters incomplets, `warn` pour les autres constats, et `pass` en leur absence. Les pages réservées `index`, `log`, `hot` et `_insights` sont exemptées du contrôle d’orphelin, et les liens vers soi ne comptent pas comme connexions.

Cette fonction est le point d’agrégation des contrôles de santé du vault : la commande CLI `cmd_lint()` l’appelle, affiche ou sérialise son rapport et convertit son statut en code de sortie, avec promotion optionnelle des avertissements en échec via le mode strict. ^[inferred] Sa centralité vient aussi du fait que les tests de lint valident directement ses trois états et les catégories de constats qui les déclenchent. ^[inferred]
