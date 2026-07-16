---
node: scripts_extract_jsonl
title: "extract-jsonl.py"
community: "JSONL History Extraction"
source_file: "scripts/extract-jsonl.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# extract-jsonl.py

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** JSONL History Extraction · **Fichier:** `scripts/extract-jsonl.py` · **Degré:** 11

### Connexions (EXTRACTED — depuis graph.json)
- —contains→ [[canonical()]] `[EXTRACTED]` (L76)
- —contains→ [[default_history_path()]] `[EXTRACTED]` (L80)
- —contains→ [[default_output_dir()]] `[EXTRACTED]` (L84)
- —contains→ [[extract_conversation()]] `[EXTRACTED]` (L157)
- —contains→ [[is_skipped()]] `[EXTRACTED]` (L99)
- —contains→ [[main()]] `[EXTRACTED]` (L333)
- —contains→ [[needs_extraction()]] `[EXTRACTED]` (L107)
- —contains→ [[run()]] `[EXTRACTED]` (L240)
- —contains→ [[skip_patterns()]] `[EXTRACTED]` (L92)
- —contains→ [[_text_from_content()]] `[EXTRACTED]` (L135)
- ←calls— [[Claude History Ingest Skill]] `[EXTRACTED]`
<!-- graphify:end -->

## Définition

`extract-jsonl.py` est un exécutable Python sans dépendance externe qui parcourt les conversations Claude Code sous `projects/*/*.jsonl` et produit un JSON compact par session. Il ignore les événements de progression et d’historique de fichiers, ne conserve que le texte des tours utilisateur et assistant, tronque chaque bloc textuel à 8 000 caractères et calcule les métadonnées de session ainsi que le nombre de mots utilisateur. Son contrôle de fraîcheur extrait toujours une sortie absente, applique `--since` seulement aux sources disposant déjà d’une sortie, puis réextrait lorsque le `mtime` source dépasse celui du JSON produit.

Ce script est l’étape de réduction de bruit appelée par la skill d’ingestion de l’historique Claude : il transforme les journaux volumineux en une représentation directement consommable et réduit ainsi la quantité de contexte nécessaire aux traitements suivants. ^[inferred] `run()` centralise le filtrage de projets, le mode simulation, la décision de fraîcheur, l’écriture par projet et les statistiques, tandis que `main()` expose ces choix en ligne de commande. ^[inferred]

Le parseur tolère silencieusement les lignes JSON invalides et les erreurs d’ouverture en traitant la conversation comme vide ; cette robustesse peut aussi masquer la différence entre un fichier illisible et une session réellement dépourvue de tours utiles. ^[inferred]

## Voir aussi

- [[ExtractStalenessTest]]
