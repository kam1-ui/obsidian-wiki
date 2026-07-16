---
node: obsidian_wiki_cache_load_manifest
title: "_load_manifest()"
community: "Ingest Cache/Staleness"
source_file: "obsidian_wiki/cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# _load_manifest()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `obsidian_wiki/cache.py` · **Degré:** 13

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cache.py]] `[EXTRACTED]` (L46)
- —references→ [[SourceEntry]] `[EXTRACTED]` (L46)
- —calls→ [[_manifest_path()]] `[EXTRACTED]` (L47)
- —references→ [[Path]] `[EXTRACTED]` (L46)
- ←calls— [[check_sources()]] `[EXTRACTED]` (L103)
- ←calls— [[update_source()]] `[EXTRACTED]` (L136)
- ←imports— [[test_cache.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_cache_update_with_pages()]] `[EXTRACTED]` (L205)
- ←calls— [[.test_preserves_other_manifest_entries()]] `[EXTRACTED]` (L158)
- ←calls— [[.test_records_correct_hash()]] `[EXTRACTED]` (L135)
- ←calls— [[.test_records_last_ingested_timestamp()]] `[EXTRACTED]` (L145)
- ←calls— [[.test_records_pages_produced()]] `[EXTRACTED]` (L140)
- ←calls— [[.test_update_overwrites_old_hash()]] `[EXTRACTED]` (L152)
<!-- graphify:end -->

## Définition

`_load_manifest(vault: Path) -> dict[str, SourceEntry]` construit le chemin du manifeste avec `_manifest_path(vault)`, retourne `{}` si `.manifest.json` n'existe pas, puis lit le JSON UTF-8 et renvoie `data.get("sources", {})`. Si la lecture échoue par JSON invalide ou erreur d'I/O, la fonction retourne aussi `{}`.

Ce nœud est le lecteur partagé de l'état de cache: `check_sources()` l'utilise pour comparer les hashes courants aux entrées déjà ingérées, `update_source()` l'utilise avant de modifier une source, et les tests l'appellent pour vérifier les champs écrits dans le manifeste.^[inferred]

Son comportement tolérant rend un manifeste absent ou illisible équivalent à un cache vide, ce qui évite une exception au moment de classifier ou de mettre à jour les sources mais peut masquer une corruption du fichier manifeste.^[inferred]

## Voir aussi

- [[cache.py]]
- [[_manifest_path()]]
- [[check_sources()]]
- [[update_source()]]
- [[test_cache.py]]
