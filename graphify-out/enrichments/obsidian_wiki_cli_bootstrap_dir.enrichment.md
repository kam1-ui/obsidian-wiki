---
node: obsidian_wiki_cli_bootstrap_dir
title: "bootstrap_dir()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.78
  inferred: 0.22
  ambiguous: 0.0
---

# bootstrap_dir()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L49)
- —calls→ [[_pkg_dir()]] `[EXTRACTED]` (L56)
- —references→ [[Path]] `[EXTRACTED]` (L49)
- ←calls— [[cmd_info()]] `[EXTRACTED]` (L820)
- ←calls— [[install_project()]] `[EXTRACTED]` (L212)
- ←rationale_for— [[Return the directory containing agent bootstrap context files.      For a wheel]] `[EXTRACTED]` (L50)
- ←calls— [[run_doctor()]] `[EXTRACTED]` (L397)
<!-- graphify:end -->

## Définition

`bootstrap_dir() -> Path | None` renvoie le répertoire des fichiers de contexte agent : dans une roue, `<package>/_data/bootstrap`; dans un checkout source, la racine du dépôt si `AGENTS.md` y existe; sinon `None`. Sa docstring précise que les fichiers d'un checkout source sont résolus ensuite via le layout repo-relatif de `_bootstrap_files`.

Ce helper centralise la différence entre installation packagée et checkout source pour les commandes qui doivent signaler ou copier les assets bootstrap, notamment `cmd_info()`, `install_project()` et `run_doctor()`.^[inferred]

## Voir aussi

- [[cmd_info()]]
