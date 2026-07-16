---
node: obsidian_wiki_lint
title: "lint.py"
community: "Wiki Lint Checks"
source_file: "obsidian_wiki/lint.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# lint.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Wiki Lint Checks · **Fichier:** `obsidian_wiki/lint.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[_iter_pages()]] `[EXTRACTED]` (L24)
- —contains→ [[lint_vault()]] `[EXTRACTED]` (L87)
- —contains→ [[_parse_frontmatter_values()]] `[EXTRACTED]` (L31)
- —contains→ [[_parse_page()]] `[EXTRACTED]` (L60)
- —contains→ [[_slug()]] `[EXTRACTED]` (L20)
- ←rationale_for— [[Vault lint checks for wiki structure and metadata hygiene.]] `[EXTRACTED]` (L1)
- ←imports_from— [[test_lint.py]] `[EXTRACTED]` (L11)
<!-- graphify:end -->

## Définition

Ce module parcourt les pages Markdown d’un vault hors dossiers exclus, analyse leur frontmatter et leurs liens wiki ou Markdown, puis détecte liens cassés, champs requis absents, titres dupliqués, résumés manquants et pages orphelines. `lint_vault()` renvoie un rapport structuré avec statistiques et statut `fail` pour les liens cassés ou le frontmatter incomplet, `warn` pour les autres constats, sinon `pass`.

Il centralise les règles automatisables d’intégrité structurelle et d’hygiène des métadonnées que [[test_lint.py]] fixe par des scénarios de régression. ^[inferred]

## Voir aussi

- [[test_lint.py]]
