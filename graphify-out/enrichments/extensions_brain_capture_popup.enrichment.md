---
node: extensions_brain_capture_popup
title: "popup.js"
community: "Browser Extension Popup"
source_file: "extensions/brain-capture/popup.js"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# popup.js

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Browser Extension Popup · **Fichier:** `extensions/brain-capture/popup.js` · **Degré:** 23

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[buildFilename()]] `[EXTRACTED]` (L151)
- —contains→ [[buildMarkdown()]] `[EXTRACTED]` (L164)
- —contains→ [[captureButton]] `[EXTRACTED]` (L7)
- —contains→ [[chooseFolder]] `[EXTRACTED]` (L6)
- —contains→ [[copyStatus]] `[EXTRACTED]` (L11)
- —contains→ [[ensureWritable()]] `[EXTRACTED]` (L112)
- —contains→ [[escapeYaml()]] `[EXTRACTED]` (L175)
- —contains→ [[extractPage()]] `[EXTRACTED]` (L230)
- —contains→ [[folderStatus]] `[EXTRACTED]` (L5)
- —contains→ [[getUniqueFileHandle()]] `[EXTRACTED]` (L131)
- —contains→ [[init()]] `[EXTRACTED]` (L98)
- —contains→ [[loadRawHandle()]] `[EXTRACTED]` (L206)
- —contains→ [[noteField]] `[EXTRACTED]` (L12)
- —contains→ [[openDb()]] `[EXTRACTED]` (L197)
- —contains→ [[pathCommand]] `[EXTRACTED]` (L10)
- —contains→ [[pathHelpButton]] `[EXTRACTED]` (L8)
- —contains→ [[pathPanel]] `[EXTRACTED]` (L9)
- —contains→ [[saveRawHandle()]] `[EXTRACTED]` (L217)
- —contains→ [[setBusy()]] `[EXTRACTED]` (L192)
- —contains→ [[setFolderStatus()]] `[EXTRACTED]` (L179)
- *…3 autres arêtes*
<!-- graphify:end -->

## Définition

`popup.js` pilote la popup Chrome de capture web: il sélectionne les éléments DOM de l'interface, initialise le chemin d'aide vers `vault/_raw`, restaure un dossier via IndexedDB, demande un dossier avec la File System Access API, puis capture l'onglet actif au clic. Le flux de capture vérifie la permission d'écriture, refuse les pages internes Chrome, exécute `extractPage()` dans l'onglet, construit un nom de fichier daté et slugifié, génère un Markdown avec frontmatter `web-capture`/`raw-ingest`, écrit un fichier `.md` unique et remet le champ de note à zéro.

Ce fichier est le hub de l'extension parce qu'il concentre l'orchestration UI, la persistance du handle `_raw`, la génération du Markdown et l'extraction de contenu lisible depuis la page courante.^[inferred] Son rôle dans le système est de transformer une page web et une note utilisateur en source brute prête pour le pipeline d'ingestion du vault, sans passer par le CLI.^[inferred]

Les limites visibles sont celles des APIs navigateur: la capture dépend de `showDirectoryPicker`, des permissions de handle persisté et de `chrome.scripting`, et elle ne peut pas lire les pages `chrome://` ou `chrome-extension://`.^[inferred] L'extraction supprime des éléments structurels puis tronque le texte à 140000 caractères et la sélection à 30000 caractères, donc elle favorise un contenu brut compact plutôt qu'une archive complète de la page.^[inferred]
