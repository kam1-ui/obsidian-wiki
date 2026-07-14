---
node: tests_test_cache_testhashing
title: "TestHashing"
community: "Ingest Cache/Staleness"
source_file: "tests/test_cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# TestHashing

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `tests/test_cache.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_cache.py]] `[EXTRACTED]` (L49)
- —method→ [[.test_compute_hash_dispatches()]] `[EXTRACTED]` (L68)
- —method→ [[.test_hash_file_alias()]] `[EXTRACTED]` (L72)
- —method→ [[.test_sha256_dir_changes_on_edit()]] `[EXTRACTED]` (L62)
- —method→ [[.test_sha256_dir_deterministic()]] `[EXTRACTED]` (L59)
- —method→ [[.test_sha256_file_changes_on_edit()]] `[EXTRACTED]` (L53)
- —method→ [[.test_sha256_file_deterministic()]] `[EXTRACTED]` (L50)
<!-- graphify:end -->

## Définition

`TestHashing` est une classe de tests pytest consacrée aux fonctions de hash de `obsidian_wiki.cache`. Elle teste le déterminisme de `sha256_file()` et `sha256_dir()`, leur changement après édition de contenu, le dispatch de `compute_hash()` et l'alias `hash_file()`.

Dans cette communauté, c'est le socle de tests qui protège la sémantique de hash avant qu'elle ne soit utilisée par le manifeste ou la CLI. ^[inferred] Les assertions se concentrent sur les propriétés observables, notamment digest SHA-256 de 64 caractères et changement quand le contenu change. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cache_sha256_file]]
- [[obsidian_wiki_cache_sha256_dir]]
- [[obsidian_wiki_cache_compute_hash]]
- [[obsidian_wiki_cache_hash_file]]
