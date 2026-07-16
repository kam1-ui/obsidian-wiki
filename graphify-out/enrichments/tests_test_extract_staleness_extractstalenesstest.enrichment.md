---
node: tests_test_extract_staleness_extractstalenesstest
title: "ExtractStalenessTest"
community: "Extract Staleness Tests"
source_file: "tests/test_extract_staleness.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# ExtractStalenessTest

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Extract Staleness Tests · **Fichier:** `tests/test_extract_staleness.py` · **Degré:** 11

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_extract_staleness.py]] `[EXTRACTED]` (L22)
- —method→ [[._run()]] `[EXTRACTED]` (L52)
- —method→ [[._set_mtimes()]] `[EXTRACTED]` (L64)
- —method→ [[.setUp()]] `[EXTRACTED]` (L33)
- —method→ [[.tearDown()]] `[EXTRACTED]` (L49)
- —method→ [[.test_first_run_extracts()]] `[EXTRACTED]` (L68)
- —method→ [[.test_missing_output_is_reextracted()]] `[EXTRACTED]` (L74)
- —method→ [[.test_missing_output_reextracted_despite_since_gate()]] `[EXTRACTED]` (L89)
- —method→ [[.test_output_newer_is_skipped()]] `[EXTRACTED]` (L97)
- —method→ [[.test_source_newer_is_reextracted()]] `[EXTRACTED]` (L81)
- ←rationale_for— [[The extractor must be idempotent based on output-file staleness.      Regression]] `[EXTRACTED]` (L23)
<!-- graphify:end -->

## Définition

`ExtractStalenessTest` est une classe `unittest.TestCase` qui importe `scripts/extract-jsonl.py` par son chemin, construit une fausse session Claude dans un répertoire temporaire et appelle `extract_jsonl.main()` avec des chemins isolés. Ses cinq tests vérifient la première extraction, la recréation d’une sortie supprimée même derrière une barrière `--since`, la réextraction quand la source est plus récente et le saut quand la sortie est au moins aussi récente.

La classe constitue la garde de régression du contrat d’idempotence de l’extracteur : elle protège le choix de décider à partir de l’existence et des dates du fichier de sortie plutôt qu’à partir d’un manifeste temporel fourni par l’appelant. ^[inferred] En manipulant directement les `mtime` et en contrôlant les traces `EXTRACT` et `SKIP(unchanged)`, elle couvre les branches de décision qui avaient auparavant laissé une session manquante en aval. ^[inferred]

## Voir aussi

- [[extract-jsonl.py]]
