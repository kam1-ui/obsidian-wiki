---
node: obsidian_wiki_batch_make_batches
title: "_make_batches()"
community: "Batch Discovery/Planning"
source_file: "obsidian_wiki/batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.65
  inferred: 0.35
  ambiguous: 0.0
---

# _make_batches()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `obsidian_wiki/batch.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[batch.py]] `[EXTRACTED]` (L153)
- ←calls— [[plan_batches()]] `[EXTRACTED]` (L205)
- ←rationale_for— [[Split files into batches respecting size and file-count limits.]] `[EXTRACTED]` (L159)
- ←imports— [[test_batch.py]] `[EXTRACTED]` (L9)
- ←calls— [[.test_all_files_present_in_batches()]] `[EXTRACTED]` (L145)
- ←calls— [[.test_empty_input()]] `[EXTRACTED]` (L141)
- ←calls— [[.test_single_batch_small()]] `[EXTRACTED]` (L126)
- ←calls— [[.test_splits_on_byte_limit()]] `[EXTRACTED]` (L132)
- ←calls— [[.test_splits_on_file_count()]] `[EXTRACTED]` (L137)
<!-- graphify:end -->

## Définition

`_make_batches(files: list[dict], *, max_batch_bytes: int, max_batch_files: int) -> list[list[dict]]` parcourt les fichiers dans leur ordre reçu et construit des lots successifs. Avant d'ajouter un fichier, elle clôt le lot courant si l'ajout dépasserait `max_batch_bytes` ou si `len(current) >= max_batch_files`, puis ajoute le dernier lot non vide.

Cette fonction est le découpeur pur appelé par `plan_batches()` après découverte et filtrage des sources. ^[inferred] Les tests `TestMakeBatches` en fixent les invariants pratiques : entrée vide, petit ensemble en un seul lot, découpe par limite d'octets, découpe par nombre de fichiers et conservation de tous les fichiers. ^[inferred]

Un fichier individuel plus gros que `max_batch_bytes` n'est pas subdivisé : il sera placé seul dans un lot qui peut dépasser la limite, car la fonction ne découpe qu'entre fichiers. ^[inferred]

## Voir aussi

- [[obsidian_wiki_batch]]
- [[tests_test_batch_testmakebatches]]
- [[tests_test_batch_testplanbatches]]
