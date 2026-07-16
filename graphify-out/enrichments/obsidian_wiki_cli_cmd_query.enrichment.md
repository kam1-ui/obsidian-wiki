---
node: obsidian_wiki_cli_cmd_query
title: "cmd_query()"
community: "CLI Command Layer"
source_file: "obsidian_wiki/cli.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.78
  inferred: 0.22
  ambiguous: 0.0
---

# cmd_query()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** CLI Command Layer · **Fichier:** `obsidian_wiki/cli.py` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cli.py]] `[EXTRACTED]` (L786)
- —calls→ [[Path]] `[EXTRACTED]` (L794)
- —calls→ [[_read_config_value()]] `[EXTRACTED]` (L789)
- —references→ [[Namespace]] `[EXTRACTED]` (L786)
- —calls→ [[_print_query()]] `[EXTRACTED]` (L806)
- ←indirect_call— [[build_parser()]] `[INFERRED]` (L965)
- —calls→ [[query()]] `[EXTRACTED]` (L799)
<!-- graphify:end -->

## Définition

`cmd_query(args: argparse.Namespace) -> int` résout le vault depuis `args.vault` ou `OBSIDIAN_VAULT_PATH`, échoue avec un message d'erreur si aucun vault n'est configuré ou si le chemin n'est pas un dossier, puis appelle `obsidian_wiki.graphrag.query(vault, args.question, top_n=args.top, max_should_read=args.max_read)`. Le résultat est imprimé en JSON compact ou indenté quand demandé, sinon via `_print_query()`, et la commande renvoie `0` après une requête valide.

Dans la couche CLI, cette commande est l'adaptateur entre les arguments utilisateur du sous-parseur `query` et le moteur GraphRAG, avec une sortie orientée machine ou console selon les flags.^[inferred]
