---
node: obsidian_wiki_cli_cmd_lint
title: "cmd_lint()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.78
  inferred: 0.22
  ambiguous: 0.0
---

# cmd_lint()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L742)
- —calls→ [[Path]] `[EXTRACTED]` (L750)
- —calls→ [[_read_config_value()]] `[EXTRACTED]` (L745)
- —references→ [[Namespace]] `[EXTRACTED]` (L742)
- —calls→ [[_print_lint()]] `[EXTRACTED]` (L762)
- ←indirect_call— [[build_parser()]] `[INFERRED]` (L953)
- —calls→ [[lint_vault()]] `[EXTRACTED]` (L755)
<!-- graphify:end -->

## Définition

`cmd_lint(args: argparse.Namespace) -> int` résout le vault depuis l'argument positionnel ou `OBSIDIAN_VAULT_PATH`, échoue si le vault manque ou n'est pas un dossier, puis appelle `obsidian_wiki.lint.lint_vault(vault)`. Elle imprime le rapport en JSON compact ou indenté quand demandé, sinon via `_print_lint()`, et renvoie `1` pour un statut `fail` ou pour un `warn` en mode `--strict`.

Cette commande expose le linter du vault au CLI en gardant la validation de chemin, le formatage de sortie et la politique de code retour au même niveau que le parsing d'arguments.^[inferred]
