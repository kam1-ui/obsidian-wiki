---
node: obsidian_wiki_cache_check_sources
title: "check_sources()"
community: "Ingest Cache/Staleness"
source_file: "obsidian_wiki/cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.63
  inferred: 0.37
  ambiguous: 0.0
---

# check_sources()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `obsidian_wiki/cache.py` · **Degré:** 18

### Connexions (EXTRACTED — depuis graph.json)
- ←imports— [[batch.py]] `[EXTRACTED]` (L139)
- ←calls— [[_filter_unchanged()]] `[EXTRACTED]` (L141)
- ←contains— [[cache.py]] `[EXTRACTED]` (L98)
- —references→ [[CheckResult]] `[EXTRACTED]` (L98)
- —references→ [[Path]] `[EXTRACTED]` (L98)
- —calls→ [[_load_manifest()]] `[EXTRACTED]` (L103)
- —calls→ [[compute_hash()]] `[EXTRACTED]` (L111)
- ←rationale_for— [[Classify each source as new / modified / unchanged vs. the manifest.      Also r]] `[EXTRACTED]` (L99)
- ←imports— [[cli.py]] `[EXTRACTED]` (L672)
- ←calls— [[cmd_cache_check()]] `[EXTRACTED]` (L675)
- ←imports— [[test_cache.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_empty_source_list()]] `[EXTRACTED]` (L106)
- ←calls— [[.test_missing_path()]] `[EXTRACTED]` (L102)
- ←calls— [[.test_modified_after_content_change()]] `[EXTRACTED]` (L97)
- ←calls— [[.test_multiple_sources()]] `[EXTRACTED]` (L111)
- ←calls— [[.test_new_source()]] `[EXTRACTED]` (L82)
- ←calls— [[.test_timestamp_irrelevant()]] `[EXTRACTED]` (L119)
- ←calls— [[.test_unchanged_after_update()]] `[EXTRACTED]` (L89)
<!-- graphify:end -->

## Définition

`check_sources(vault: Path, source_paths: list[Path]) -> CheckResult` charge les entrées `sources` du manifeste, calcule le hash courant de chaque chemin existant, puis classe les sources dans `new`, `modified`, `unchanged` ou `missing`. La fonction accepte une correspondance par chemin tel quel ou par chemin absolu, et ajoute aussi aux `missing` les clés du manifeste qui ne font pas partie du scan courant et dont le fichier n'existe plus sur disque.

Ce nœud est central parce qu'il est le point de décision du cache: `_filter_unchanged()` s'en sert pour retirer les fichiers inchangés du traitement batch, `cmd_cache_check()` l'expose en JSON côté CLI, et `tests/test_cache.py` vérifie les scénarios nouveau, modifié, inchangé, absent, liste vide, sources multiples et timestamp inchangé.^[inferred]

La comparaison repose sur le contenu, pas sur `mtime`: le test `test_timestamp_irrelevant` touche le fichier sans modifier son texte et attend encore `unchanged`.^[inferred]

## Voir aussi

- [[cache.py]]
- [[_load_manifest()]]
- [[compute_hash()]]
- [[test_cache.py]]
