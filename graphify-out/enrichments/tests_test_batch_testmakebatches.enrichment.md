---
node: tests_test_batch_testmakebatches
title: "TestMakeBatches"
community: "Batch Discovery/Planning"
source_file: "tests/test_batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.7
  inferred: 0.3
  ambiguous: 0.0
---

# TestMakeBatches

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `tests/test_batch.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_batch.py]] `[EXTRACTED]` (L119)
- —method→ [[._files()]] `[EXTRACTED]` (L120)
- —method→ [[.test_all_files_present_in_batches()]] `[EXTRACTED]` (L143)
- —method→ [[.test_empty_input()]] `[EXTRACTED]` (L140)
- —method→ [[.test_single_batch_small()]] `[EXTRACTED]` (L124)
- —method→ [[.test_splits_on_byte_limit()]] `[EXTRACTED]` (L130)
- —method→ [[.test_splits_on_file_count()]] `[EXTRACTED]` (L135)
<!-- graphify:end -->

## Définition

`TestMakeBatches` est une classe pytest pour `_make_batches()`. Elle fournit un helper `_files(sizes: list[int])` qui fabrique des dictionnaires `{path, kind, size_bytes}`, puis vérifie le lot unique pour de petits fichiers, le découpage sur limite d'octets, le découpage sur limite de nombre de fichiers, l'entrée vide et la présence de tous les fichiers dans les lots produits.

Cette classe spécifie le contrat local du découpage sans dépendre du système de fichiers ni du cache. ^[inferred] Elle protège directement le comportement que `plan_batches()` réutilise après avoir construit la liste `to_ingest`. ^[inferred]

Le test de limite d'octets exige seulement `len(batches) >= 2`, donc il confirme une séparation sans figer exactement la distribution des lots. ^[inferred]

## Voir aussi

- [[obsidian_wiki_batch_make_batches]]
- [[tests_test_batch_testplanbatches]]
- [[obsidian_wiki_batch]]
