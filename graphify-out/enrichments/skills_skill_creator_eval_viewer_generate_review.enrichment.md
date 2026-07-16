---
node: skills_skill_creator_eval_viewer_generate_review
title: "generate_review.py"
community: "Skill Eval Review Viewer"
source_file: ".skills/skill-creator/eval-viewer/generate_review.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.83
  inferred: 0.17
  ambiguous: 0.0
---

# generate_review.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Skill Eval Review Viewer · **Fichier:** `.skills/skill-creator/eval-viewer/generate_review.py` · **Degré:** 10

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[build_run()]] `[EXTRACTED]` (L85)
- —contains→ [[embed_file()]] `[EXTRACTED]` (L149)
- —contains→ [[find_runs()]] `[EXTRACTED]` (L60)
- —contains→ [[_find_runs_recursive()]] `[EXTRACTED]` (L68)
- —contains→ [[generate_html()]] `[EXTRACTED]` (L250)
- —contains→ [[get_mime_type()]] `[EXTRACTED]` (L52)
- —contains→ [[_kill_port()]] `[EXTRACTED]` (L288)
- —contains→ [[load_previous_iteration()]] `[EXTRACTED]` (L213)
- —contains→ [[main()]] `[EXTRACTED]` (L387)
- —contains→ [[ReviewHandler]] `[EXTRACTED]` (L308)
<!-- graphify:end -->

## Définition

Ce script Python sans dépendance découvre récursivement les runs d'évaluation contenant un dossier `outputs/`, puis rassemble pour chacun le prompt, l'identifiant d'évaluation, les fichiers produits et les données de notation. Il incorpore les textes et les fichiers binaires ou multimédias dans les données d'une page HTML autonome, avec prise en charge d'une itération précédente et d'un benchmark optionnel. Il peut soit écrire cette page en mode `--static`, soit servir une vue régénérée à chaque chargement via un serveur HTTP local. Le gestionnaire expose aussi `/api/feedback` en lecture et en écriture afin de persister les revues dans `feedback.json`.

Il est le hub d'orchestration du visualiseur de revues : découverte des résultats, normalisation de leurs représentations, assemblage du modèle de données et collecte du retour humain convergent dans ce fichier. ^[inferred]

Les erreurs de lecture et de décodage de plusieurs fichiers de métadonnées sont ignorées ou remplacées par des valeurs de repli, tandis que le démarrage du serveur tente d'arrêter tout processus déjà à l'écoute sur le port demandé.
