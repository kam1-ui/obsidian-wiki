---
node: tests_test_cache_testcachecli
title: "TestCacheCLI"
community: "Ingest Cache/Staleness"
source_file: "tests/test_cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# TestCacheCLI

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `tests/test_cache.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_cache.py]] `[EXTRACTED]` (L167)
- —method→ [[._run()]] `[EXTRACTED]` (L168)
- —method→ [[.test_cache_check_new()]] `[EXTRACTED]` (L184)
- —method→ [[.test_cache_check_pretty()]] `[EXTRACTED]` (L190)
- —method→ [[.test_cache_hash_file()]] `[EXTRACTED]` (L174)
- —method→ [[.test_cache_hash_missing_exits_nonzero()]] `[EXTRACTED]` (L180)
- —method→ [[.test_cache_update_then_check_unchanged()]] `[EXTRACTED]` (L195)
- —method→ [[.test_cache_update_with_pages()]] `[EXTRACTED]` (L201)
<!-- graphify:end -->

## Définition

`TestCacheCLI` est une classe de tests pytest pour les commandes CLI de cache exécutées via `python -m obsidian_wiki.cli`. Elle contient le helper `_run()` et des tests pour `cache-hash`, `cache-check`, le mode `--pretty`, `cache-update`, et l'option `--pages`.

Cette classe relie les fonctions de cache au comportement utilisateur exposé par la CLI, en vérifiant les codes retour, le JSON de sortie et les écritures dans le manifeste. ^[inferred] Elle complète les tests unitaires en couvrant le chemin subprocess réel plutôt qu'un appel direct aux fonctions Python. ^[inferred]

## Voir aussi

- [[tests_test_cache_testcachecli_run]]
- [[obsidian_wiki_cache_hash_file]]
- [[tests_test_cache_testupdatesource]]
