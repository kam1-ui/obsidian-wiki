---
node: extensions_brain_capture_manifest
title: "manifest.json"
community: "Extension Manifest"
source_file: "extensions/brain-capture/manifest.json"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# manifest.json

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Extension Manifest · **Fichier:** `extensions/brain-capture/manifest.json` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[action]] `[EXTRACTED]` (L6)
- —contains→ [[background]] `[EXTRACTED]` (L20)
- —contains→ [[description]] `[EXTRACTED]` (L4)
- —contains→ [[icons]] `[EXTRACTED]` (L15)
- —contains→ [[manifest_version]] `[EXTRACTED]` (L2)
- —contains→ [[name]] `[EXTRACTED]` (L3)
- —contains→ [[permissions]] `[EXTRACTED]` (L23)
- —contains→ [[version]] `[EXTRACTED]` (L5)
<!-- graphify:end -->

## Définition

Ce manifeste Chrome Manifest V3 déclare l’extension « Brain Vault Capture » en version `0.1.0`, avec `popup.html` comme popup d’action et `background.js` comme service worker. Il référence trois tailles d’icônes et demande les permissions `activeTab`, `contextMenus` et `scripting` ; sa description annonce la capture de l’URL et du texte lisible de la page courante vers le dossier `_raw` du vault.

Il constitue le point de déclaration qui relie l’interface, le processus d’arrière-plan et les capacités navigateur de l’extension. ^[inferred]
