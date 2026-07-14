---
node: obsidian_wiki_batch
title: "batch.py"
community: "Batch Discovery/Planning"
source_file: "obsidian_wiki/batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.65
  inferred: 0.35
  ambiguous: 0.0
---

# batch.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `obsidian_wiki/batch.py` · **Degré:** 10

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[_classify()]] `[EXTRACTED]` (L69)
- —contains→ [[discover_sources()]] `[EXTRACTED]` (L101)
- —contains→ [[_file_size()]] `[EXTRACTED]` (L90)
- —contains→ [[_filter_unchanged()]] `[EXTRACTED]` (L133)
- —contains→ [[_make_batches()]] `[EXTRACTED]` (L153)
- —contains→ [[plan_batches()]] `[EXTRACTED]` (L185)
- —imports→ [[check_sources()]] `[EXTRACTED]` (L139)
- —imports→ [[compute_hash()]] `[EXTRACTED]` (L139)
- ←rationale_for— [[Batch planner for parallel wiki-ingest subagent dispatch.  When ingesting a larg]] `[EXTRACTED]` (L1)
- ←imports_from— [[test_batch.py]] `[EXTRACTED]` (L9)
<!-- graphify:end -->

## Définition

`batch.py` est le module de planification de lots pour l'ingestion parallèle : sa docstring décrit un plan JSON contenant `batches`, `stats` et `merge_hint`. Il définit la classification de fichiers, la découverte de sources, le filtrage des fichiers inchangés par manifeste, le découpage en lots et l'entrée principale `plan_batches()`.

Dans la communauté du graphe, ce fichier regroupe les fonctions appelées par les tests de `test_batch.py` et sert de surface centrale pour produire un plan exploitable par `obsidian-wiki batch-plan`. ^[inferred] Son rôle est de transformer un répertoire source en lots bornés par taille et nombre de fichiers, avec les métadonnées nécessaires à une ingestion distribuée. ^[inferred]

Le compteur `skipped_binary` reste à `0` dans `plan_batches()` alors que les fichiers binaires sont déjà exclus pendant `discover_sources()`, ce qui signifie que la statistique ne mesure pas réellement le nombre de binaires rencontrés. ^[inferred]

## Voir aussi

- [[obsidian_wiki_batch_classify]]
- [[obsidian_wiki_batch_make_batches]]
- [[tests_test_batch_testdiscoversources]]
- [[tests_test_batch_testmakebatches]]
- [[tests_test_batch_testplanbatches]]
