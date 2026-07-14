---
node: tests_test_cache_testcachecli_run
title: "._run()"
community: "Ingest Cache/Staleness"
source_file: "tests/test_cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# ._run()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `tests/test_cache.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←method— [[TestCacheCLI]] `[EXTRACTED]` (L168)
- ←calls— [[.test_cache_check_new()]] `[EXTRACTED]` (L185)
- ←calls— [[.test_cache_check_pretty()]] `[EXTRACTED]` (L191)
- ←calls— [[.test_cache_hash_file()]] `[EXTRACTED]` (L175)
- ←calls— [[.test_cache_hash_missing_exits_nonzero()]] `[EXTRACTED]` (L181)
- ←calls— [[.test_cache_update_then_check_unchanged()]] `[EXTRACTED]` (L196)
- ←calls— [[.test_cache_update_with_pages()]] `[EXTRACTED]` (L202)
<!-- graphify:end -->

## Définition

`TestCacheCLI._run(self, *args)` exécute `subprocess.run([sys.executable, "-m", "obsidian_wiki.cli", *args], capture_output=True, text=True)`. Il retourne l'objet `CompletedProcess` produit par le subprocess.

Ce helper factorise l'invocation CLI réelle pour tous les tests `TestCacheCLI`, ce qui donne accès au `returncode`, à `stdout` et à `stderr` en texte. ^[inferred]

## Voir aussi

- [[tests_test_cache_testcachecli]]
