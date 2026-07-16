---
node: tests_test_cache_testupdatesource
title: "TestUpdateSource"
community: "Ingest Cache/Staleness"
source_file: "tests/test_cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# TestUpdateSource

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `tests/test_cache.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_cache.py]] `[EXTRACTED]` (L127)
- —method→ [[.test_preserves_other_manifest_entries()]] `[EXTRACTED]` (L155)
- —method→ [[.test_records_correct_hash()]] `[EXTRACTED]` (L132)
- —method→ [[.test_records_last_ingested_timestamp()]] `[EXTRACTED]` (L143)
- —method→ [[.test_records_pages_produced()]] `[EXTRACTED]` (L138)
- —method→ [[.test_update_overwrites_old_hash()]] `[EXTRACTED]` (L148)
- —method→ [[.test_writes_manifest()]] `[EXTRACTED]` (L128)
<!-- graphify:end -->

## Définition

`TestUpdateSource` est une classe de tests pytest pour `update_source()` et les écritures de manifeste associées. Elle vérifie la création de `.manifest.json`, l'enregistrement du hash correct, des pages produites, de `last_ingested`, l'écrasement d'un ancien hash après modification, et la préservation d'autres entrées.

Cette classe définit le contrat persistant du cache : une mise à jour doit recalculer le hash courant, conserver les métadonnées utiles et ne pas supprimer les sources voisines. ^[inferred] Elle est complémentaire de `TestCheckSources`, qui relit ensuite ces entrées pour classifier l'état des sources. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cache_manifest_path]]
- [[obsidian_wiki_cache_compute_hash]]
- [[tests_test_cache_testchecksources]]
- [[tests_test_cache_testcachecli]]
