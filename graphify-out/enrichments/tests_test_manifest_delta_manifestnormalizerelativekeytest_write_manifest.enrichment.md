---
node: tests_test_manifest_delta_manifestnormalizerelativekeytest_write_manifest
title: "._write_manifest()"
community: "Manifest Delta Tests"
source_file: "tests/test_manifest_delta.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# ._write_manifest()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Manifest Delta Tests · **Fichier:** `tests/test_manifest_delta.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←calls— [[.test_relative_key_older_ingest_is_modified_not_new()]] `[EXTRACTED]` (L54)
- ←calls— [[.test_relative_key_recent_ingest_is_unchanged()]] `[EXTRACTED]` (L66)
- ←calls— [[.test_absolute_key_still_matches()]] `[EXTRACTED]` (L78)
- ←calls— [[.test_unknown_file_is_new()]] `[EXTRACTED]` (L87)
- ←method— [[ManifestNormalizeRelativeKeyTest]] `[EXTRACTED]` (L112)
- ←calls— [[.test_absolute_keys_still_dedup_and_canonicalize()]] `[EXTRACTED]` (L141)
- ←calls— [[.test_relative_key_preserved_regardless_of_cwd()]] `[EXTRACTED]` (L130)
<!-- graphify:end -->

## Définition

`._write_manifest(self, sources: dict) -> None` écrit dans le manifeste temporaire du test un objet JSON de version 1 contenant les sources fournies et des sections `projects` et `stats` vides.

Ce helper permet aux tests de construire précisément les cas de clés relatives, absolues ou concurrentes avant d’exécuter la normalisation. ^[inferred]

## Voir aussi

- [[tests_test_manifest_delta_manifestnormalizerelativekeytest|ManifestNormalizeRelativeKeyTest]]
