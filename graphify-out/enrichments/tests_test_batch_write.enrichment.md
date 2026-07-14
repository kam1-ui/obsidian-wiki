---
node: tests_test_batch_write
title: "_write()"
community: "Batch Discovery/Planning"
source_file: "tests/test_batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# _write()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `tests/test_batch.py` · **Degré:** 16

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_batch.py]] `[EXTRACTED]` (L35)
- ←calls— [[.test_excludes_code_by_default()]] `[EXTRACTED]` (L81)
- ←calls— [[.test_finds_markdown()]] `[EXTRACTED]` (L74)
- ←calls— [[.test_includes_code_when_flag_set()]] `[EXTRACTED]` (L87)
- ←calls— [[.test_returns_size()]] `[EXTRACTED]` (L110)
- ←calls— [[.test_skips_binary()]] `[EXTRACTED]` (L92)
- ←calls— [[.test_skips_hidden_dirs()]] `[EXTRACTED]` (L97)
- ←calls— [[.test_skips_node_modules()]] `[EXTRACTED]` (L104)
- ←calls— [[.test_batch_kinds_tallied()]] `[EXTRACTED]` (L173)
- ←calls— [[.test_batch_total_bytes_correct()]] `[EXTRACTED]` (L196)
- ←calls— [[.test_json_serialisable()]] `[EXTRACTED]` (L203)
- ←calls— [[.test_no_cache_flag_includes_unchanged()]] `[EXTRACTED]` (L189)
- ←calls— [[.test_returns_required_keys()]] `[EXTRACTED]` (L156)
- ←calls— [[.test_single_file_single_batch()]] `[EXTRACTED]` (L167)
- ←calls— [[.test_skips_unchanged_after_cache_update()]] `[EXTRACTED]` (L180)
- —references→ [[Path]] `[EXTRACTED]` (L35)
<!-- graphify:end -->

## Définition

`_write(path: Path, content: str = "x", size: int | None = None) -> Path` crée le dossier parent, écrit soit `size` octets `b"x"` avec `write_bytes()`, soit le texte `content` avec `write_text()`, puis renvoie le `Path`. Dans `tests/test_batch.py`, ce helper fabrique les fichiers temporaires utilisés par les tests de découverte, de planification, de taille de batch et de cache.

Le nœud est central dans la communauté parce qu'il fournit les fixtures de fichiers à presque tous les scénarios qui exercent `discover_sources()` et `plan_batches()`. ^[inferred] Son paramètre `size` permet aux tests de vérifier les chemins qui dépendent de `size_bytes` sans introduire de contenu de test volumineux ou variable. ^[inferred]

## Voir aussi

- [[test_batch.py]]
- [[discover_sources()]]
- [[plan_batches()]]
