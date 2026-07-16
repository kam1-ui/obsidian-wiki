---
node: obsidian_wiki_cli_skills_dir
title: "skills_dir()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.0
---

# skills_dir()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L38)
- —calls→ [[_pkg_dir()]] `[EXTRACTED]` (L40)
- —references→ [[Path]] `[EXTRACTED]` (L38)
- ←calls— [[cmd_info()]] `[EXTRACTED]` (L819)
- ←calls— [[install_skills()]] `[EXTRACTED]` (L79)
- ←calls— [[list_skills()]] `[EXTRACTED]` (L66)
- ←rationale_for— [[Return the directory holding the bundled skill folders.]] `[EXTRACTED]` (L39)
- ←calls— [[write_config()]] `[EXTRACTED]` (L285)
<!-- graphify:end -->

## Définition

`skills_dir()` renvoie le répertoire des dossiers de compétences embarqués : il essaie d'abord `<package>/_data/skills`, puis le répertoire `.skills` voisin du checkout source, et lève `FileNotFoundError` avec une consigne de réinstallation si aucun candidat n'est un dossier.

Ce helper est un point d'ancrage du CLI parce que l'installation, la configuration, la commande `info`, la liste des skills et le contrôle de fraîcheur dépendent tous de la même résolution de source des compétences.^[inferred]

## Voir aussi

- [[cmd_info()]]
- [[install_skills()]]
- [[_check_stale()]]
