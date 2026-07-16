---
node: obsidian_wiki_cache
title: "cache.py"
community: "Ingest Cache/Staleness"
source_file: "obsidian_wiki/cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.7
  inferred: 0.3
  ambiguous: 0.0
---

# cache.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `obsidian_wiki/cache.py` · **Degré:** 13

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[check_sources()]] `[EXTRACTED]` (L98)
- —contains→ [[CheckResult]] `[EXTRACTED]` (L35)
- —contains→ [[compute_hash()]] `[EXTRACTED]` (L92)
- —contains→ [[hash_file()]] `[EXTRACTED]` (L149)
- —contains→ [[_load_manifest()]] `[EXTRACTED]` (L46)
- —contains→ [[_manifest_path()]] `[EXTRACTED]` (L42)
- —contains→ [[_save_manifest()]] `[EXTRACTED]` (L57)
- —contains→ [[sha256_dir()]] `[EXTRACTED]` (L81)
- —contains→ [[sha256_file()]] `[EXTRACTED]` (L69)
- —contains→ [[SourceEntry]] `[EXTRACTED]` (L29)
- —contains→ [[update_source()]] `[EXTRACTED]` (L129)
- ←rationale_for— [[Content-hash cache for wiki-ingest source tracking.  Provides a reliable, platfo]] `[EXTRACTED]` (L1)
- ←imports_from— [[test_cache.py]] `[EXTRACTED]` (L10)
<!-- graphify:end -->

## Définition

`obsidian_wiki/cache.py` est le module de cache par hash de contenu pour le suivi des sources de `wiki-ingest`. Il définit le format `sources` de `.manifest.json`, les types `SourceEntry` et `CheckResult`, les helpers `_manifest_path()`, `_load_manifest()` et `_save_manifest()`, les fonctions de hash `sha256_file()`, `sha256_dir()`, `compute_hash()` et `hash_file()`, ainsi que `check_sources()` et `update_source()` pour classifier puis enregistrer les sources.

Dans le graphe, ce fichier concentre la logique qui permet au batch et à la CLI d'éviter de retraiter les sources inchangées sans dépendre de `sha256sum` ni d'un parsing manuel du manifeste.^[inferred] Il est relié directement à `tests/test_cache.py`, qui exerce à la fois les fonctions internes et les commandes `cache-check`, `cache-update` et `cache-hash`.^[inferred]

La dette visible est que `_load_manifest()` et `_save_manifest()` tolèrent silencieusement les erreurs JSON ou I/O, donc une corruption du manifeste se traduit par un cache vide ou réécrit plutôt que par un diagnostic explicite.^[inferred]

## Voir aussi

- [[check_sources()]]
- [[_load_manifest()]]
- [[compute_hash()]]
- [[update_source()]]
- [[test_cache.py]]
