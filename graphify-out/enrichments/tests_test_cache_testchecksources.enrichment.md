---
node: tests_test_cache_testchecksources
title: "TestCheckSources"
community: "Ingest Cache/Staleness"
source_file: "tests/test_cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# TestCheckSources

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `tests/test_cache.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_cache.py]] `[EXTRACTED]` (L80)
- —method→ [[.test_empty_source_list()]] `[EXTRACTED]` (L105)
- —method→ [[.test_missing_path()]] `[EXTRACTED]` (L100)
- —method→ [[.test_modified_after_content_change()]] `[EXTRACTED]` (L94)
- —method→ [[.test_multiple_sources()]] `[EXTRACTED]` (L109)
- —method→ [[.test_new_source()]] `[EXTRACTED]` (L81)
- —method→ [[.test_timestamp_irrelevant()]] `[EXTRACTED]` (L115)
- —method→ [[.test_unchanged_after_update()]] `[EXTRACTED]` (L87)
<!-- graphify:end -->

## Définition

`TestCheckSources` est une classe de tests pytest couvrant `check_sources(vault, source_paths)`. Ses méthodes vérifient les cas source nouvelle, inchangée après `update_source`, modifiée après changement de contenu, chemin manquant, liste vide, sources multiples et horodatage modifié sans changement de contenu.

Dans la communauté cache/staleness, cette classe fixe le contrat de classification `new` / `modified` / `unchanged` / `missing` à partir du manifeste et du hash courant. ^[inferred] Elle montre aussi que la fraîcheur repose sur le contenu plutôt que sur le mtime, puisque `test_timestamp_irrelevant` attend `unchanged` après un simple `touch()`. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cache_compute_hash]]
- [[tests_test_cache_testupdatesource]]
- [[tests_test_cache_testhashing]]
