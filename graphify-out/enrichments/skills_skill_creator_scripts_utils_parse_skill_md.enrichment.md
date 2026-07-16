---
node: skills_skill_creator_scripts_utils_parse_skill_md
title: "parse_skill_md()"
community: "Loop Report Generation"
source_file: ".skills/skill-creator/scripts/utils.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.0
---

# parse_skill_md()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Loop Report Generation · **Fichier:** `.skills/skill-creator/scripts/utils.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←calls— [[main()]] `[INFERRED]` (L213)
- ←calls— [[main()]] `[INFERRED]` (L279)
- ←calls— [[run_loop()]] `[INFERRED]` (L64)
- ←calls— [[main()]] `[INFERRED]` (L268)
- ←contains— [[utils.py]] `[EXTRACTED]` (L7)
- —references→ [[Path]] `[EXTRACTED]` (L7)
- ←rationale_for— [[Parse a SKILL.md file, returning (name, description, full_content).]] `[EXTRACTED]` (L8)
<!-- graphify:end -->

## Définition

`parse_skill_md(skill_path: Path) -> tuple[str, str, str]` lit `SKILL.md`, repère son frontmatter délimité par `---` et renvoie le nom, la description et le contenu complet. Elle accepte une description YAML simple ou multiligne (`>`, `|`, `>-`, `|-`) et lève `ValueError` si l’une des bornes du frontmatter manque.

Elle fournit à `run_loop()` les métadonnées et le corps nécessaires pour évaluer puis améliorer la description du skill. ^[inferred]

## Voir aussi

- [[run_loop()]]
