---
node: obsidian_wiki_batch_plan_batches
title: "plan_batches()"
community: "Batch Discovery/Planning"
source_file: "obsidian_wiki/batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# plan_batches()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `obsidian_wiki/batch.py` · **Degré:** 18

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[batch.py]] `[EXTRACTED]` (L185)
- —references→ [[Path]] `[EXTRACTED]` (L185)
- —calls→ [[discover_sources()]] `[EXTRACTED]` (L195)
- —calls→ [[_filter_unchanged()]] `[EXTRACTED]` (L202)
- —calls→ [[_make_batches()]] `[EXTRACTED]` (L205)
- —references→ [[Any]] `[EXTRACTED]` (L185)
- ←rationale_for— [[Discover sources, filter unchanged, and split into batches.]] `[EXTRACTED]` (L194)
- ←imports— [[cli.py]] `[EXTRACTED]` (L636)
- ←calls— [[cmd_batch_plan()]] `[EXTRACTED]` (L642)
- ←imports— [[test_batch.py]] `[EXTRACTED]` (L9)
- ←calls— [[.test_batch_kinds_tallied()]] `[EXTRACTED]` (L175)
- ←calls— [[.test_batch_total_bytes_correct()]] `[EXTRACTED]` (L198)
- ←calls— [[.test_empty_dir_gives_zero_batches()]] `[EXTRACTED]` (L163)
- ←calls— [[.test_json_serialisable()]] `[EXTRACTED]` (L204)
- ←calls— [[.test_no_cache_flag_includes_unchanged()]] `[EXTRACTED]` (L192)
- ←calls— [[.test_returns_required_keys()]] `[EXTRACTED]` (L157)
- ←calls— [[.test_single_file_single_batch()]] `[EXTRACTED]` (L168)
- ←calls— [[.test_skips_unchanged_after_cache_update()]] `[EXTRACTED]` (L184)
<!-- graphify:end -->

## Définition

`plan_batches(source_dir: Path, vault: Path, *, max_batch_mb: float = 2.0, max_batch_files: int = 20, skip_unchanged: bool = True, include_code: bool = False) -> dict[str, Any]` découvre les sources avec `discover_sources()`, filtre les fichiers inchangés via `_filter_unchanged()` quand `skip_unchanged` est vrai et que le vault existe, puis découpe les fichiers restants avec `_make_batches()`. La sortie contient `batches`, `stats` et `merge_hint`; chaque batch expose son `id`, sa liste de fichiers, son total d'octets et un comptage `kinds`.

Ce nœud est le point d'orchestration du graphe Batch Discovery/Planning parce qu'il relie la découverte, le cache, le découpage et le format JSON consommé par la CLI et les tests. ^[inferred] Sa centralité vient aussi du fait que `tests/test_batch.py` vérifie les clés de sortie, le cas vide, le batch unique, le comptage des types, le saut des sources inchangées, le total d'octets et la sérialisabilité JSON. ^[inferred]

La statistique `skipped_binary` reste toujours à `0`, avec un commentaire indiquant que les binaires sont déjà exclus par `_classify()`, donc elle ne compte pas réellement les fichiers binaires rencontrés pendant le parcours. ^[inferred]

## Voir aussi

- [[discover_sources()]]
- [[_make_batches()]]
- [[test_batch.py]]
