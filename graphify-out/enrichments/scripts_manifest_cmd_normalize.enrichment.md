---
node: scripts_manifest_cmd_normalize
title: "cmd_normalize()"
community: "Manifest CLI"
source_file: "scripts/manifest.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# cmd_normalize()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Manifest CLI · **Fichier:** `scripts/manifest.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[manifest.py]] `[EXTRACTED]` (L62)
- —calls→ [[canonical()]] `[EXTRACTED]` (L78)
- —calls→ [[manifest_path()]] `[EXTRACTED]` (L99)
- —calls→ [[load_manifest()]] `[EXTRACTED]` (L63)
- —calls→ [[_newest()]] `[EXTRACTED]` (L82)
- —references→ [[Namespace]] `[EXTRACTED]` (L62)
- ←indirect_call— [[main()]] `[INFERRED]` (L190)
<!-- graphify:end -->

## Définition

`cmd_normalize(args: argparse.Namespace) -> int` charge les sources du manifeste, conserve sans changement les clés relatives, canonise les clés absolues et fusionne les collisions avec `_newest`. Elle affiche les avertissements et le bilan, respecte le mode `dry_run`, et ne réécrit `.manifest.json` que si une clé absolue a changé ou si une collision a été fusionnée.

La commande assainit donc les identités de sources absolues sans corrompre les clés relatives dont la base de résolution appartient au processus d’ingestion plutôt qu’au répertoire courant. ^[inferred]

## Voir aussi

- [[tests_test_manifest_delta_manifestnormalizerelativekeytest|ManifestNormalizeRelativeKeyTest]]
