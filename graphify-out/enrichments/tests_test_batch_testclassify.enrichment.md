---
node: tests_test_batch_testclassify
title: "TestClassify"
community: "Batch Discovery/Planning"
source_file: "tests/test_batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.0
---

# TestClassify

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `tests/test_batch.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_batch.py]] `[EXTRACTED]` (L48)
- —method→ [[.test_image()]] `[EXTRACTED]` (L55)
- —method→ [[.test_markdown()]] `[EXTRACTED]` (L49)
- —method→ [[.test_pdf()]] `[EXTRACTED]` (L52)
- —method→ [[.test_python_code()]] `[EXTRACTED]` (L58)
- —method→ [[.test_skip_binary()]] `[EXTRACTED]` (L61)
- —method→ [[.test_skip_lockfile()]] `[EXTRACTED]` (L64)
<!-- graphify:end -->

## Définition

`TestClassify` est une classe pytest qui appelle `_classify()` sur des chemins synthétiques. Elle vérifie que `foo.md` devient `"text"`, `paper.pdf` devient `"pdf"`, `shot.png` devient `"image"`, `main.py` devient `"code"`, `lib.so` devient `"skip"` et `poetry.lock` devient `"skip"`.

Cette classe documente les catégories minimales attendues par la phase de découverte des sources. ^[inferred] Elle est directement liée à `discover_sources()`, qui utilise `_classify()` pour décider quels fichiers inclure, exclure ou filtrer selon `include_code`. ^[inferred]

Les tests ne couvrent pas la branche MIME fallback de `_classify()`, seulement les extensions explicitement listées. ^[inferred]

## Voir aussi

- [[obsidian_wiki_batch_classify]]
- [[tests_test_batch_testdiscoversources]]
- [[obsidian_wiki_batch]]
