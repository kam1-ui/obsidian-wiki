---
node: scripts_extract_jsonl_run
title: "run()"
community: "JSONL History Extraction"
source_file: "scripts/extract-jsonl.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# run()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** JSONL History Extraction · **Fichier:** `scripts/extract-jsonl.py` · **Degré:** 9

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[extract-jsonl.py]] `[EXTRACTED]` (L240)
- —calls→ [[canonical()]] `[EXTRACTED]` (L241)
- —calls→ [[default_output_dir()]] `[EXTRACTED]` (L242)
- —calls→ [[skip_patterns()]] `[EXTRACTED]` (L243)
- —calls→ [[is_skipped()]] `[EXTRACTED]` (L273)
- —calls→ [[needs_extraction()]] `[EXTRACTED]` (L285)
- —calls→ [[extract_conversation()]] `[EXTRACTED]` (L294)
- ←calls— [[main()]] `[EXTRACTED]` (L373)
- —references→ [[Namespace]] `[EXTRACTED]` (L240)
<!-- graphify:end -->

## Définition

`run(args: argparse.Namespace) -> int` normalise les chemins d’historique et de sortie, valide l’option `--since`, parcourt les fichiers `projects/*/*.jsonl`, applique les exclusions et les contrôles d’ancienneté, puis extrait chaque conversation exploitable en JSON. Il respecte les modes dry-run et verbose, affiche des statistiques récapitulatives, retourne `1` pour une date invalide et `0` dans les autres chemins traités.

Cette fonction orchestre tout le pipeline d’extraction incrémentale en coordonnant les fonctions spécialisées de filtrage, de détection de changements et de conversion des conversations. ^[inferred]
