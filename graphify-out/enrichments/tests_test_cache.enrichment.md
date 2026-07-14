---
node: tests_test_cache
title: "test_cache.py"
community: "Ingest Cache/Staleness"
source_file: "tests/test_cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.72
  inferred: 0.28
  ambiguous: 0.0
---

# test_cache.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `tests/test_cache.py` · **Degré:** 17

### Connexions (EXTRACTED — depuis graph.json)
- —imports_from→ [[cache.py]] `[EXTRACTED]` (L10)
- —imports→ [[_manifest_path()]] `[EXTRACTED]` (L10)
- —imports→ [[_load_manifest()]] `[EXTRACTED]` (L10)
- —imports→ [[sha256_file()]] `[EXTRACTED]` (L10)
- —imports→ [[sha256_dir()]] `[EXTRACTED]` (L10)
- —imports→ [[compute_hash()]] `[EXTRACTED]` (L10)
- —imports→ [[check_sources()]] `[EXTRACTED]` (L10)
- —imports→ [[update_source()]] `[EXTRACTED]` (L10)
- —imports→ [[hash_file()]] `[EXTRACTED]` (L10)
- —contains→ [[src_dir()]] `[EXTRACTED]` (L37)
- —contains→ [[src_file()]] `[EXTRACTED]` (L30)
- —contains→ [[TestCacheCLI]] `[EXTRACTED]` (L167)
- —contains→ [[TestCheckSources]] `[EXTRACTED]` (L80)
- —contains→ [[TestHashing]] `[EXTRACTED]` (L49)
- —contains→ [[TestUpdateSource]] `[EXTRACTED]` (L127)
- —contains→ [[vault()]] `[EXTRACTED]` (L23)
- ←rationale_for— [[Tests for the content-hash cache module.]] `[EXTRACTED]` (L1)
<!-- graphify:end -->

## Définition

`tests/test_cache.py` est le module de tests du cache par hash de contenu: il importe les fonctions publiques et auxiliaires de `obsidian_wiki.cache`, définit des fixtures `vault`, `src_file` et `src_dir`, puis regroupe les vérifications dans `TestHashing`, `TestCheckSources`, `TestUpdateSource` et `TestCacheCLI`. Les tests couvrent la stabilité et le changement des hashes fichier/dossier, le dispatch de `compute_hash`, l'alias `hash_file`, les états de `check_sources`, l'écriture du manifeste, la conservation de `pages_produced`, `last_ingested`, l'écrasement du hash ancien, la préservation des autres entrées, et les commandes `cache-hash`, `cache-check`, `cache-update`.

Dans la communauté, ce fichier sert de spécification executable du contrat de cache: il relie `check_sources()`, `_load_manifest()`, `update_source()` et les commandes CLI à des comportements observables plutôt qu'à de simples assertions de structure.^[inferred]

Le test `test_timestamp_irrelevant` documente une limite volontaire du modèle: seule la modification du contenu rend une source `modified`, tandis qu'un changement d'horodatage sans changement de texte reste `unchanged`.^[inferred]

## Voir aussi

- [[cache.py]]
- [[check_sources()]]
- [[_load_manifest()]]
- [[update_source()]]
- [[sha256_file()]]
- [[sha256_dir()]]
- [[compute_hash()]]
- [[hash_file()]]
