---
node: tests_test_lint
title: "test_lint.py"
community: "Wiki Lint Checks"
source_file: "tests/test_lint.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# test_lint.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Wiki Lint Checks · **Fichier:** `tests/test_lint.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- —imports_from→ [[lint.py]] `[EXTRACTED]` (L11)
- —imports→ [[lint_vault()]] `[EXTRACTED]` (L11)
- —contains→ [[_page()]] `[EXTRACTED]` (L14)
- —contains→ [[_run()]] `[EXTRACTED]` (L52)
- —contains→ [[test_lint_cli_uses_configured_vault_and_strict_mode()]] `[EXTRACTED]` (L103)
- —contains→ [[test_lint_vault_fails_on_broken_links_and_missing_frontmatter()]] `[EXTRACTED]` (L78)
- —contains→ [[test_lint_vault_passes_clean_graph()]] `[EXTRACTED]` (L63)
- —contains→ [[test_lint_vault_warns_on_duplicates_missing_summaries_and_orphans()]] `[EXTRACTED]` (L90)
- ←rationale_for— [[Tests for vault linting.]] `[EXTRACTED]` (L1)
<!-- graphify:end -->

## Définition

Ce module de tests construit des pages de vault temporaires, appelle `lint_vault()` et vérifie les statuts `pass`, `warn` et `fail` associés aux graphes propres, aux liens cassés, au frontmatter manquant, aux titres dupliqués, aux résumés absents et aux pages orphelines. Il teste aussi la commande `lint --json --strict` avec un vault fourni par la configuration globale.

Il constitue la spécification exécutable du comportement attendu de [[lint.py]], y compris la distinction entre erreurs bloquantes et avertissements d’hygiène. ^[inferred]

## Voir aussi

- [[lint.py]]
