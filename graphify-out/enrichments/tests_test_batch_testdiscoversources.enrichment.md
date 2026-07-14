---
node: tests_test_batch_testdiscoversources
title: "TestDiscoverSources"
community: "Batch Discovery/Planning"
source_file: "tests/test_batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.7
  inferred: 0.3
  ambiguous: 0.0
---

# TestDiscoverSources

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `tests/test_batch.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_batch.py]] `[EXTRACTED]` (L72)
- —method→ [[.test_excludes_code_by_default()]] `[EXTRACTED]` (L80)
- —method→ [[.test_finds_markdown()]] `[EXTRACTED]` (L73)
- —method→ [[.test_includes_code_when_flag_set()]] `[EXTRACTED]` (L86)
- —method→ [[.test_returns_size()]] `[EXTRACTED]` (L109)
- —method→ [[.test_skips_binary()]] `[EXTRACTED]` (L91)
- —method→ [[.test_skips_hidden_dirs()]] `[EXTRACTED]` (L96)
- —method→ [[.test_skips_node_modules()]] `[EXTRACTED]` (L103)
<!-- graphify:end -->

## Définition

`TestDiscoverSources` est une classe pytest qui exerce `discover_sources(source_dir, vault=...)`. Ses méthodes vérifient que les fichiers Markdown sont trouvés, que le code est exclu par défaut puis inclus avec `include_code=True`, que les binaires sont ignorés, que les répertoires cachés et `node_modules` sont sautés, et que `size_bytes` reflète la taille du fichier.

Cette classe encadre le comportement de marche de répertoire avant la création des lots : elle teste l'interaction entre `_classify()`, `SKIP_DIRS`, l'option `include_code` et `_file_size()`. ^[inferred] Elle constitue donc la couverture de la phase qui décide quels fichiers atteindront ensuite `_make_batches()` et `plan_batches()`. ^[inferred]

Les assertions se concentrent sur quelques répertoires et extensions sentinelles ; elles ne couvrent pas toutes les familles d'extensions déclarées dans `batch.py`, comme Office ou images. ^[inferred]

## Voir aussi

- [[obsidian_wiki_batch]]
- [[obsidian_wiki_batch_classify]]
- [[tests_test_batch_testclassify]]
- [[tests_test_batch_testplanbatches]]
