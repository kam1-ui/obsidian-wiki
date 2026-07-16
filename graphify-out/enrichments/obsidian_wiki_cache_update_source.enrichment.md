---
node: obsidian_wiki_cache_update_source
title: "update_source()"
community: "Ingest Cache/Staleness"
source_file: "obsidian_wiki/cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# update_source()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `obsidian_wiki/cache.py` · **Degré:** 22

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cache.py]] `[EXTRACTED]` (L129)
- —references→ [[Path]] `[EXTRACTED]` (L129)
- —calls→ [[_load_manifest()]] `[EXTRACTED]` (L136)
- —calls→ [[_save_manifest()]] `[EXTRACTED]` (L145)
- —calls→ [[compute_hash()]] `[EXTRACTED]` (L138)
- ←rationale_for— [[Record the current hash of *source_path* in the manifest. Returns the hash.]] `[EXTRACTED]` (L135)
- ←imports— [[cli.py]] `[EXTRACTED]` (L684)
- ←calls— [[cmd_cache_update()]] `[EXTRACTED]` (L688)
- ←imports— [[test_batch.py]] `[EXTRACTED]` (L182)
- ←calls— [[.test_no_cache_flag_includes_unchanged()]] `[EXTRACTED]` (L191)
- ←calls— [[.test_skips_unchanged_after_cache_update()]] `[EXTRACTED]` (L183)
- ←imports— [[test_cache.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_modified_after_content_change()]] `[EXTRACTED]` (L95)
- ←calls— [[.test_multiple_sources()]] `[EXTRACTED]` (L110)
- ←calls— [[.test_timestamp_irrelevant()]] `[EXTRACTED]` (L117)
- ←calls— [[.test_unchanged_after_update()]] `[EXTRACTED]` (L88)
- ←calls— [[.test_preserves_other_manifest_entries()]] `[EXTRACTED]` (L156)
- ←calls— [[.test_records_correct_hash()]] `[EXTRACTED]` (L133)
- ←calls— [[.test_records_last_ingested_timestamp()]] `[EXTRACTED]` (L144)
- ←calls— [[.test_records_pages_produced()]] `[EXTRACTED]` (L139)
- *…2 autres arêtes*
<!-- graphify:end -->

## Définition

`update_source(vault: Path, source_path: Path, *, pages_produced: list[str] | None = None) -> str` charge le manifest du vault, calcule le hash actuel du fichier ou dossier source avec `compute_hash()`, met à jour l'entrée indexée par `str(source_path)`, écrit `content_hash` et `last_ingested`, remplace `pages_produced` quand l'argument est fourni, sauvegarde le manifest et retourne le hash. La commande CLI `cache-update` résout le vault et la source, transmet `--pages` comme liste éventuelle, puis imprime le chemin et le hash en JSON.

Cette fonction est le point d'écriture du cache d'ingestion: elle fige l'état courant d'une source pour que `check_sources()` et la planification de batch puissent ensuite classer les sources en nouvelles, modifiées ou inchangées.^[inferred] Elle est centrale dans la communauté cache/staleness parce qu'elle relie le hash de contenu, l'horodatage d'ingestion et la liste des pages produites dans une seule entrée de manifest.^[inferred]

La clé de manifest est exactement `str(source_path)`, donc la stabilité dépend du fait que l'appelant fournisse un chemin normalisé; le CLI le fait avec `expanduser().resolve()`, mais la fonction elle-même ne canonicalise pas.^[inferred] Comme `pages_produced` n'est écrit que si l'argument n'est pas `None`, un appel sans pages conserve une éventuelle liste précédente au lieu de l'effacer.^[inferred]

## Voir aussi

- [[obsidian_wiki_cli]]
