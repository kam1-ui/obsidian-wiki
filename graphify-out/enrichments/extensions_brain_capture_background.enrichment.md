---
node: extensions_brain_capture_background
title: "background.js"
community: "Extension Background Script"
source_file: "extensions/brain-capture/background.js"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# background.js

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Extension Background Script · **Fichier:** `extensions/brain-capture/background.js` · **Degré:** 15

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[buildFilename()]] `[EXTRACTED]` (L133)
- —contains→ [[buildMarkdown()]] `[EXTRACTED]` (L146)
- —contains→ [[buildSelectionPage()]] `[EXTRACTED]` (L93)
- —indirect_call→ [[createContextMenus()]] `[INFERRED]` (L8)
- —contains→ [[escapeYaml()]] `[EXTRACTED]` (L158)
- —contains→ [[extractPage()]] `[EXTRACTED]` (L182)
- —contains→ [[extractPageFromTab()]] `[EXTRACTED]` (L84)
- —contains→ [[flashBadge()]] `[EXTRACTED]` (L66)
- —contains→ [[getUniqueFileHandle()]] `[EXTRACTED]` (L113)
- —contains→ [[hasWritePermission()]] `[EXTRACTED]` (L78)
- —contains→ [[isBlockedUrl()]] `[EXTRACTED]` (L53)
- —contains→ [[loadRawHandle()]] `[EXTRACTED]` (L171)
- —contains→ [[openDb()]] `[EXTRACTED]` (L162)
- —contains→ [[showNeedsPopup()]] `[EXTRACTED]` (L57)
- —contains→ [[writeMarkdown()]] `[EXTRACTED]` (L105)
<!-- graphify:end -->

## Définition

`background.js` est le service worker de l’extension Brain Vault Capture : il installe deux menus contextuels, capture soit la sélection soit le contenu principal nettoyé de l’onglet, construit une note Markdown avec frontmatter, puis l’écrit dans le dossier `_raw` autorisé. Le handle du dossier est chargé depuis IndexedDB, l’écriture exige une permission `readwrite`, les collisions de noms reçoivent un suffixe et le badge de l’extension signale le succès ou l’erreur.

Ce fichier orchestre toute la chaîne de capture en reliant les API Chrome, l’extraction exécutée dans la page, la sérialisation Markdown et l’API File System Access ; son degré élevé vient de ce rôle de conteneur et de point de coordination des fonctions de la communauté. ^[inferred] La capture reste volontairement bornée : certaines pages internes Chrome sont refusées, le texte de page est tronqué à 140 000 caractères, la sélection à 30 000, et une collision au-delà de 100 essais bascule vers un suffixe temporel. ^[inferred]
