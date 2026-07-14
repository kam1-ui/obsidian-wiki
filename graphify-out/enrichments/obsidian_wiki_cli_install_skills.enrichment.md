---
node: obsidian_wiki_cli_install_skills
title: "install_skills()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.82
  inferred: 0.18
  ambiguous: 0.0
---

# install_skills()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L70)
- —references→ [[Path]] `[EXTRACTED]` (L70)
- —calls→ [[skills_dir()]] `[EXTRACTED]` (L79)
- ←calls— [[install_global_skills()]] `[EXTRACTED]` (L134)
- ←calls— [[_install_hermes_profiles()]] `[EXTRACTED]` (L145)
- ←calls— [[install_project()]] `[EXTRACTED]` (L210)
- ←rationale_for— [[Install bundled skills into *target_dir*. Returns the count installed.]] `[EXTRACTED]` (L78)
<!-- graphify:end -->

## Définition

`install_skills(target_dir: Path, label: str, *, subset: tuple[str, ...] | None = None, mode: str = "symlink", quiet: bool = False) -> int` installe les dossiers de skills embarqués dans `target_dir`, en filtrant éventuellement par `subset`, puis en créant soit des symlinks soit des copies. Elle remplace les liens, fichiers et anciens dossiers de skills gérés, saute les dossiers utilisateur non gérés, vérifie que chaque installation contient `SKILL.md`, affiche un résumé sauf en mode silencieux, et renvoie le nombre installé.

Cette fonction est la primitive commune des installations globales, des profils Hermes et de l'installation projet, ce qui concentre la politique de remplacement et de validation des skills dans un seul passage.^[inferred]

## Voir aussi

- [[skills_dir()]]
