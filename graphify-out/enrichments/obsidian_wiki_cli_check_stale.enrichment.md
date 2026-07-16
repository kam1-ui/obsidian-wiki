---
node: obsidian_wiki_cli_check_stale
title: "_check_stale()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.77
  inferred: 0.23
  ambiguous: 0.0
---

# _check_stale()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 6

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L294)
- —calls→ [[list_skills()]] `[EXTRACTED]` (L316)
- —calls→ [[_read_config_value()]] `[EXTRACTED]` (L304)
- ←calls— [[cmd_info()]] `[EXTRACTED]` (L845)
- ←calls— [[main()]] `[EXTRACTED]` (L1006)
- ←rationale_for— [[Warn if the installed version doesn't match when setup last ran, or if skills ar]] `[EXTRACTED]` (L295)
<!-- graphify:end -->

## Définition

`_check_stale() -> None` avertit sur stderr si `obsidian-wiki` est installé sans setup global, si la version enregistrée dans `OBSIDIAN_WIKI_VERSION` diffère de `__version__`, ou si `~/.claude/skills` ne contient pas tous les skills embarqués. Elle lit la config via `_read_config_value()`, compare la liste installée à `list_skills()`, et imprime dans chaque cas une commande de setup à relancer.

Ce contrôle est appelé par `cmd_info()` et par `main()` pour les commandes autres que `setup`, `info` et `doctor`, ce qui en fait un garde-fou transversal contre les installations obsolètes ou incomplètes.^[inferred]

## Voir aussi

- [[cmd_info()]]
