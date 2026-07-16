---
node: tests_test_manifest_delta_manifestnormalizerelativekeytest
title: "ManifestNormalizeRelativeKeyTest"
community: "Manifest Delta Tests"
source_file: "tests/test_manifest_delta.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# ManifestNormalizeRelativeKeyTest

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Manifest Delta Tests · **Fichier:** `tests/test_manifest_delta.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_manifest_delta.py]] `[EXTRACTED]` (L95)
- —method→ [[._keys_after_normalize()]] `[EXTRACTED]` (L116)
- —method→ [[.setUp()]] `[EXTRACTED]` (L103)
- —method→ [[.tearDown()]] `[EXTRACTED]` (L109)
- —method→ [[.test_absolute_keys_still_dedup_and_canonicalize()]] `[EXTRACTED]` (L135)
- —method→ [[.test_relative_key_preserved_regardless_of_cwd()]] `[EXTRACTED]` (L128)
- —method→ [[._write_manifest()]] `[EXTRACTED]` (L112)
- ←rationale_for— [[cmd_normalize must not corrupt relative source keys.      canonical() resolves a]] `[EXTRACTED]` (L96)
<!-- graphify:end -->

## Définition

`ManifestNormalizeRelativeKeyTest` est une classe de tests `unittest.TestCase` qui vérifie que `cmd_normalize` conserve les clés de source relatives indépendamment du répertoire courant, tout en continuant à canoniser et fusionner les clés absolues équivalentes.

Elle protège la règle de compatibilité selon laquelle une clé relative représente un chemin relatif à la racine d’ingestion et ne doit donc pas être transformée en chemin absolu basé sur le CWD. ^[inferred]

## Voir aussi

- [[scripts_manifest_cmd_normalize|cmd_normalize()]]
- [[tests_test_manifest_delta_manifestnormalizerelativekeytest_write_manifest|._write_manifest()]]
