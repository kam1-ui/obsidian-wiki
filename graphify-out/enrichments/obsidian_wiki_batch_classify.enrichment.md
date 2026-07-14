---
node: obsidian_wiki_batch_classify
title: "_classify()"
community: "Batch Discovery/Planning"
source_file: "obsidian_wiki/batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.6
  inferred: 0.4
  ambiguous: 0.0
---

# _classify()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `obsidian_wiki/batch.py` · **Degré:** 10

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[batch.py]] `[EXTRACTED]` (L69)
- —references→ [[Path]] `[EXTRACTED]` (L69)
- ←calls— [[discover_sources()]] `[EXTRACTED]` (L120)
- ←imports— [[test_batch.py]] `[EXTRACTED]` (L9)
- ←calls— [[.test_image()]] `[EXTRACTED]` (L56)
- ←calls— [[.test_markdown()]] `[EXTRACTED]` (L50)
- ←calls— [[.test_pdf()]] `[EXTRACTED]` (L53)
- ←calls— [[.test_python_code()]] `[EXTRACTED]` (L59)
- ←calls— [[.test_skip_binary()]] `[EXTRACTED]` (L62)
- ←calls— [[.test_skip_lockfile()]] `[EXTRACTED]` (L65)
<!-- graphify:end -->

## Définition

`_classify(path: Path) -> str` lit le suffixe du chemin en minuscules et renvoie `"text"`, `"pdf"`, `"image"`, `"office"`, `"code"` ou `"skip"` selon les ensembles d'extensions déclarés dans `batch.py`. Si l'extension n'est pas reconnue, la fonction tente `mimetypes.guess_type(str(path))` et classe les types MIME `text/*` comme `"text"`, puis retombe sur `"skip"`.

Ce nœud est le point de décision de bas niveau pour `discover_sources()`, qui l'utilise avant d'exclure les binaires et, par défaut, le code. ^[inferred] Les tests `TestClassify` fixent les cas représentatifs : Markdown, PDF, image PNG, code Python, bibliothèque `.so` et lockfile.

La classification privilégie des listes d'extensions statiques avant le MIME guessing, donc un format absent de ces listes peut être ignoré même s'il serait conceptuellement ingérable. ^[inferred]

## Voir aussi

- [[obsidian_wiki_batch]]
- [[tests_test_batch_testclassify]]
- [[tests_test_batch_testdiscoversources]]
