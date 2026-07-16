---
node: tests_test_batch
title: "test_batch.py"
community: "Batch Discovery/Planning"
source_file: "tests/test_batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# test_batch.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `tests/test_batch.py` · **Degré:** 15

### Connexions (EXTRACTED — depuis graph.json)
- —imports_from→ [[batch.py]] `[EXTRACTED]` (L9)
- —imports→ [[_classify()]] `[EXTRACTED]` (L9)
- —imports→ [[discover_sources()]] `[EXTRACTED]` (L9)
- —imports→ [[_make_batches()]] `[EXTRACTED]` (L9)
- —imports→ [[plan_batches()]] `[EXTRACTED]` (L9)
- —imports→ [[update_source()]] `[EXTRACTED]` (L182)
- —contains→ [[source_dir()]] `[EXTRACTED]` (L29)
- —contains→ [[TestBatchPlanCLI]] `[EXTRACTED]` (L212)
- —contains→ [[TestClassify]] `[EXTRACTED]` (L48)
- —contains→ [[TestDiscoverSources]] `[EXTRACTED]` (L72)
- —contains→ [[TestMakeBatches]] `[EXTRACTED]` (L119)
- —contains→ [[TestPlanBatches]] `[EXTRACTED]` (L154)
- —contains→ [[vault()]] `[EXTRACTED]` (L22)
- —contains→ [[_write()]] `[EXTRACTED]` (L35)
- ←rationale_for— [[Tests for the batch planning module.]] `[EXTRACTED]` (L1)
<!-- graphify:end -->

## Définition

`tests/test_batch.py` est le module de tests pour `obsidian_wiki.batch`; il importe `_classify`, `_make_batches`, `discover_sources` et `plan_batches`. Il définit les fixtures `vault` et `source_dir`, le helper `_write()`, puis des classes de tests pour la classification, la découverte de sources, le découpage en batches, la planification et la commande CLI `batch-plan`.

Dans le graphe, ce fichier est le hub de validation de la communauté Batch Discovery/Planning parce qu'il relie les fonctions internes du module `batch.py` à leurs comportements attendus. ^[inferred] Les assertions couvrent les formats acceptés ou ignorés, l'exclusion du code par défaut, les répertoires ignorés, les limites de taille et de nombre de fichiers, le cache des sources inchangées, la sérialisation JSON et les sorties CLI. ^[inferred]

## Voir aussi

- [[_write()]]
- [[discover_sources()]]
- [[plan_batches()]]
- [[_make_batches()]]
