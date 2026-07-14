---
node: tests_test_batch_testplanbatches
title: "TestPlanBatches"
community: "Batch Discovery/Planning"
source_file: "tests/test_batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.7
  inferred: 0.3
  ambiguous: 0.0
---

# TestPlanBatches

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `tests/test_batch.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_batch.py]] `[EXTRACTED]` (L154)
- —method→ [[.test_batch_kinds_tallied()]] `[EXTRACTED]` (L172)
- —method→ [[.test_batch_total_bytes_correct()]] `[EXTRACTED]` (L195)
- —method→ [[.test_empty_dir_gives_zero_batches()]] `[EXTRACTED]` (L162)
- —method→ [[.test_json_serialisable()]] `[EXTRACTED]` (L202)
- —method→ [[.test_no_cache_flag_includes_unchanged()]] `[EXTRACTED]` (L188)
- —method→ [[.test_returns_required_keys()]] `[EXTRACTED]` (L155)
- —method→ [[.test_single_file_single_batch()]] `[EXTRACTED]` (L166)
- —method→ [[.test_skips_unchanged_after_cache_update()]] `[EXTRACTED]` (L179)
<!-- graphify:end -->

## Définition

`TestPlanBatches` est une classe de tests pytest pour `plan_batches(source_dir, vault, ...)`. Elle vérifie que le résultat contient `batches`, `stats` et `merge_hint`, qu'un répertoire vide produit zéro lot, qu'un fichier seul produit un lot, que les kinds sont comptés, que le cache peut exclure ou inclure les fichiers inchangés, que les octets sont totalisés et que le résultat est sérialisable en JSON.

Cette classe couvre l'entrée principale du module après la classification, la découverte, le filtrage de cache et le découpage en lots. ^[inferred] Elle relie donc les garanties unitaires de `_classify()` et `_make_batches()` au contrat de sortie consommé par le CLI et les workflows d'ingestion. ^[inferred]

Les tests valident le comportement attendu du cache via `update_source`, mais ils ne forcent pas de scénario d'erreur dans `_filter_unchanged()`, qui retourne silencieusement tous les fichiers en cas d'exception. ^[inferred]

## Voir aussi

- [[obsidian_wiki_batch]]
- [[tests_test_batch_testdiscoversources]]
- [[tests_test_batch_testmakebatches]]
