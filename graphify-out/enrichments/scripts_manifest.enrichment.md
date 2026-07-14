---
node: scripts_manifest
title: "manifest.py"
community: "Manifest CLI"
source_file: "scripts/manifest.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.8
  inferred: 0.2
  ambiguous: 0.0
---

# manifest.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Manifest CLI · **Fichier:** `scripts/manifest.py` · **Degré:** 11

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[canonical()]] `[EXTRACTED]` (L30)
- —contains→ [[cmd_delta()]] `[EXTRACTED]` (L139)
- —contains→ [[cmd_normalize()]] `[EXTRACTED]` (L62)
- —contains→ [[load_manifest()]] `[EXTRACTED]` (L39)
- —contains→ [[main()]] `[EXTRACTED]` (L183)
- —contains→ [[manifest_path()]] `[EXTRACTED]` (L35)
- —contains→ [[_match_relative()]] `[EXTRACTED]` (L131)
- —contains→ [[_newest()]] `[EXTRACTED]` (L47)
- —contains→ [[_relative_key_index()]] `[EXTRACTED]` (L115)
- —contains→ [[_skip_patterns()]] `[EXTRACTED]` (L107)
- ←calls— [[Claude History Ingest Skill]] `[EXTRACTED]`
<!-- graphify:end -->

## Définition

Ce script Python sans dépendance fournit deux sous-commandes sur `.manifest.json` : `normalize`, qui canonise les clés de sources absolues et fusionne leurs collisions, et `delta`, qui classe les fichiers trouvés par glob comme nouveaux ou modifiés. `delta` applique les exclusions de `WIKI_SKIP_PROJECTS` et de `--skip`, compare la date de modification à `ingested_at`, et reconnaît aussi les clés relatives par index de nom de fichier puis correspondance de suffixe. `normalize` préserve volontairement les clés relatives, car les convertir avec `abspath` les résoudrait contre le répertoire courant et produirait de fausses clés absolues.

Ce module centralise la logique déterministe et testable de suivi incrémental des sources utilisée par les workflows d'ingestion. ^[inferred]

La correspondance des clés relatives ne parcourt que les candidates partageant le même nom de base, puis exige que la clé complète soit un suffixe du chemin scanné.

## Voir aussi

- [[ManifestDeltaRelativeKeyTest]]
