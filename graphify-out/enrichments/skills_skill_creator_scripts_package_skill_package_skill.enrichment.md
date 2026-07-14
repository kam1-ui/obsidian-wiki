---
node: skills_skill_creator_scripts_package_skill_package_skill
title: "package_skill()"
community: "Skill Packaging"
source_file: ".skills/skill-creator/scripts/package_skill.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# package_skill()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Skill Packaging · **Fichier:** `.skills/skill-creator/scripts/package_skill.py` · **Degré:** 6

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[package_skill.py]] `[EXTRACTED]` (L42)
- —calls→ [[should_exclude()]] `[EXTRACTED]` (L97)
- —calls→ [[Path]] `[EXTRACTED]` (L53)
- ←calls— [[main()]] `[EXTRACTED]` (L127)
- —calls→ [[validate_skill()]] `[INFERRED]` (L72)
- ←rationale_for— [[Package a skill folder into a .skill file.      Args:         skill_path: Path t]] `[EXTRACTED]` (L43)
<!-- graphify:end -->

## Définition

`package_skill(skill_path, output_dir=None)` résout et valide le dossier d’un skill, exige un `SKILL.md`, exécute `validate_skill()`, puis crée une archive ZIP compressée portant l’extension `.skill`. Elle exclut les artefacts et dossiers configurés via `should_exclude()`, affiche chaque ajout ou exclusion, et renvoie le chemin de l’archive ou `None` en cas d’erreur.

Cette fonction est l’étape de distribution du workflow de création de skills : elle empêche l’empaquetage d’une structure invalide et produit un fichier transportable. ^[inferred]
