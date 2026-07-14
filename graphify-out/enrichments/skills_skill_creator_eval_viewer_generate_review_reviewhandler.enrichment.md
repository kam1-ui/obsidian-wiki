---
node: skills_skill_creator_eval_viewer_generate_review_reviewhandler
title: "ReviewHandler"
community: "Skill Eval Review Viewer"
source_file: ".skills/skill-creator/eval-viewer/generate_review.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# ReviewHandler

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Skill Eval Review Viewer · **Fichier:** `.skills/skill-creator/eval-viewer/generate_review.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[generate_review.py]] `[EXTRACTED]` (L308)
- ←indirect_call— [[main()]] `[INFERRED]` (L441)
- ←rationale_for— [[Serves the review HTML and handles feedback saves.      Regenerates the HTML on]] `[EXTRACTED]` (L309)
- —inherits→ [[BaseHTTPRequestHandler]] `[EXTRACTED]` (L308)
- —method→ [[.do_GET()]] `[EXTRACTED]` (L332)
- —method→ [[.do_POST()]] `[EXTRACTED]` (L361)
- —method→ [[.__init__()]] `[EXTRACTED]` (L315)
- —method→ [[.log_message()]] `[EXTRACTED]` (L382)
<!-- graphify:end -->

## Définition

`ReviewHandler` hérite de `BaseHTTPRequestHandler` et sert l’interface de revue sur `/` ou `/index.html`, expose le feedback sur `/api/feedback`, puis valide et enregistre les soumissions JSON contenant une clé `reviews`. Il rescane le workspace et régénère le HTML à chaque chargement de page afin d’intégrer les nouvelles sorties sans redémarrer le serveur.

Instancié par `main()` via `functools.partial`, il constitue la couche HTTP interactive du viewer entre les runs présents sur disque, le HTML généré et le fichier `feedback.json`. ^[inferred]

## Voir aussi

- [[skills_skill_creator_eval_viewer_generate_review_main|main()]]
- [[skills_skill_creator_eval_viewer_generate_review_find_runs|find_runs()]]
