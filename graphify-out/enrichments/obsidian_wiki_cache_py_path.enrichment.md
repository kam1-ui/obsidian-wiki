---
node: obsidian_wiki_cache_py_path
title: "Path"
community: "Ingest Cache/Staleness"
source_file: ""
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.0
  inferred: 1.0
  ambiguous: 0.0
---

# Path

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `?` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- ←references— [[_manifest_path()]] `[EXTRACTED]` (L42)
- ←references— [[check_sources()]] `[EXTRACTED]` (L98)
- ←references— [[compute_hash()]] `[EXTRACTED]` (L92)
- ←references— [[hash_file()]] `[EXTRACTED]` (L149)
- ←references— [[_load_manifest()]] `[EXTRACTED]` (L46)
- ←references— [[_save_manifest()]] `[EXTRACTED]` (L57)
- ←references— [[sha256_dir()]] `[EXTRACTED]` (L81)
- ←references— [[sha256_file()]] `[EXTRACTED]` (L69)
- ←references— [[update_source()]] `[EXTRACTED]` (L129)
<!-- graphify:end -->

## Définition

Représente le type `Path` de la bibliothèque standard `pathlib` de Python, utilisé de manière centrale au sein du module `cache.py` pour valider l'existence, manipuler et hacher les fichiers sources et le manifeste d'ingestion.^[inferred]

## Voir aussi

- [[obsidian_wiki_cache_check_sources]]
- [[obsidian_wiki_cache_compute_hash]]
- [[obsidian_wiki_cache_update_source]]
