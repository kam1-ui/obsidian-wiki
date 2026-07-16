---
node: obsidian_wiki_cache_manifest_path
title: "_manifest_path()"
community: "Ingest Cache/Staleness"
source_file: "obsidian_wiki/cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# _manifest_path()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `obsidian_wiki/cache.py` · **Degré:** 6

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cache.py]] `[EXTRACTED]` (L42)
- ←calls— [[_load_manifest()]] `[EXTRACTED]` (L47)
- —references→ [[Path]] `[EXTRACTED]` (L42)
- ←calls— [[_save_manifest()]] `[EXTRACTED]` (L58)
- ←imports— [[test_cache.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_writes_manifest()]] `[EXTRACTED]` (L130)
<!-- graphify:end -->

## Définition

`_manifest_path(vault: Path) -> Path` retourne `vault / ".manifest.json"`, c'est-à-dire le chemin du manifeste de cache dans la racine du vault. ^[inferred] Elle est appelée par `_load_manifest()` et `_save_manifest()`, et le test `test_writes_manifest` l'utilise pour vérifier que `update_source()` crée bien ce fichier.

## Voir aussi

- [[tests_test_cache_testupdatesource]]
