---
node: skills_skill_creator_eval_viewer_generate_review_main
title: "main()"
community: "Skill Eval Review Viewer"
source_file: ".skills/skill-creator/eval-viewer/generate_review.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.0
---

# main()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Skill Eval Review Viewer · **Fichier:** `.skills/skill-creator/eval-viewer/generate_review.py` · **Degré:** 6

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[generate_review.py]] `[EXTRACTED]` (L387)
- —calls→ [[find_runs()]] `[EXTRACTED]` (L411)
- —calls→ [[load_previous_iteration()]] `[EXTRACTED]` (L421)
- —calls→ [[generate_html()]] `[EXTRACTED]` (L432)
- —calls→ [[_kill_port()]] `[EXTRACTED]` (L440)
- —indirect_call→ [[ReviewHandler]] `[INFERRED]` (L441)
<!-- graphify:end -->

## Définition

`main() -> None` analyse les options du viewer, valide le workspace, découvre les runs et charge facultativement l’itération précédente et le benchmark. En mode statique, elle écrit le HTML autonome puis termine ; sinon, elle libère le port demandé, construit un `ReviewHandler`, démarre un `HTTPServer` local, ouvre son URL dans le navigateur et sert jusqu’à interruption.

Elle orchestre l’ensemble du viewer en reliant la découverte et la génération des données à l’un des deux modes de livraison, fichier statique ou serveur interactif. ^[inferred]

## Voir aussi

- [[skills_skill_creator_eval_viewer_generate_review_find_runs|find_runs()]]
- [[skills_skill_creator_eval_viewer_generate_review_reviewhandler|ReviewHandler]]
