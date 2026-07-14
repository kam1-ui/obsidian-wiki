---
node: tests_test_manifest_delta_manifestdeltarelativekeytest
title: "ManifestDeltaRelativeKeyTest"
community: "Manifest Delta Tests"
source_file: "tests/test_manifest_delta.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.0
---

# ManifestDeltaRelativeKeyTest

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Manifest Delta Tests · **Fichier:** `tests/test_manifest_delta.py` · **Degré:** 10

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_manifest_delta.py]] `[EXTRACTED]` (L17)
- —method→ [[._delta()]] `[EXTRACTED]` (L45)
- —method→ [[.setUp()]] `[EXTRACTED]` (L26)
- —method→ [[.tearDown()]] `[EXTRACTED]` (L38)
- —method→ [[.test_absolute_key_still_matches()]] `[EXTRACTED]` (L74)
- —method→ [[.test_relative_key_older_ingest_is_modified_not_new()]] `[EXTRACTED]` (L52)
- —method→ [[.test_relative_key_recent_ingest_is_unchanged()]] `[EXTRACTED]` (L62)
- —method→ [[.test_unknown_file_is_new()]] `[EXTRACTED]` (L85)
- —method→ [[._write_manifest()]] `[EXTRACTED]` (L41)
- ←rationale_for— [[cmd_delta must recognize sources stored under relative keys.      Real vaults ke]] `[EXTRACTED]` (L18)
<!-- graphify:end -->

## Définition

Cette classe `unittest.TestCase` construit un vault, une arborescence de projets et un fichier JSONL temporaires, puis invoque `manifest.main(["delta", ...])` en capturant sa sortie standard. Ses quatre tests vérifient qu'une clé relative déjà ingérée est signalée comme modifiée ou inchangée selon les horodatages, qu'une clé absolue continue de correspondre et qu'un fichier inconnu reste classé comme nouveau. Chaque exécution doit retourner le code zéro et produire les compteurs ainsi que les lignes `NEW` ou `MOD` attendus.

La classe protège la régression où `canonical()` transformait implicitement une clé relative selon le répertoire courant, faisant réapparaître comme nouvelles des sources déjà suivies. ^[inferred]

## Voir aussi

- [[manifest.py]]
