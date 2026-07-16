---
node: scripts_manifest_cmd_delta
title: "cmd_delta()"
community: "Manifest CLI"
source_file: "scripts/manifest.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# cmd_delta()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Manifest CLI · **Fichier:** `scripts/manifest.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[manifest.py]] `[EXTRACTED]` (L139)
- —calls→ [[canonical()]] `[EXTRACTED]` (L142)
- —calls→ [[load_manifest()]] `[EXTRACTED]` (L140)
- —references→ [[Namespace]] `[EXTRACTED]` (L139)
- —calls→ [[_skip_patterns()]] `[EXTRACTED]` (L144)
- —calls→ [[_relative_key_index()]] `[EXTRACTED]` (L143)
- —calls→ [[_match_relative()]] `[EXTRACTED]` (L157)
- ←indirect_call— [[main()]] `[INFERRED]` (L196)
<!-- graphify:end -->

## Définition

`cmd_delta(args: argparse.Namespace) -> int` charge le manifeste, développe récursivement le motif de scan, ignore les fichiers non ordinaires ou exclus, puis classe les fichiers en nouveaux ou modifiés en comparant leurs chemins et dates de modification aux entrées ingérées. Il tente d’abord une correspondance canonique absolue, puis une correspondance de suffixe indexée pour les clés relatives, et imprime un résumé suivi des lignes `NEW` et `MOD`.

Cette commande fournit le delta exploitable par les workflows d’ingestion tout en maintenant la compatibilité avec les manifestes qui enregistrent leurs sources sous des clés relatives. ^[inferred]
