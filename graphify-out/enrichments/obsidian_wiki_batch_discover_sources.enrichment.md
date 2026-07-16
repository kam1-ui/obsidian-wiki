---
node: obsidian_wiki_batch_discover_sources
title: "discover_sources()"
community: "Batch Discovery/Planning"
source_file: "obsidian_wiki/batch.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# discover_sources()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Batch Discovery/Planning · **Fichier:** `obsidian_wiki/batch.py` · **Degré:** 14

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[batch.py]] `[EXTRACTED]` (L101)
- —calls→ [[_classify()]] `[EXTRACTED]` (L120)
- —references→ [[Path]] `[EXTRACTED]` (L101)
- —calls→ [[_file_size()]] `[EXTRACTED]` (L125)
- ←calls— [[plan_batches()]] `[EXTRACTED]` (L195)
- ←rationale_for— [[Walk source_dir and return a list of ingestible file dicts.      Each dict: {pat]] `[EXTRACTED]` (L107)
- ←imports— [[test_batch.py]] `[EXTRACTED]` (L9)
- ←calls— [[.test_excludes_code_by_default()]] `[EXTRACTED]` (L83)
- ←calls— [[.test_finds_markdown()]] `[EXTRACTED]` (L76)
- ←calls— [[.test_includes_code_when_flag_set()]] `[EXTRACTED]` (L88)
- ←calls— [[.test_returns_size()]] `[EXTRACTED]` (L111)
- ←calls— [[.test_skips_binary()]] `[EXTRACTED]` (L93)
- ←calls— [[.test_skips_hidden_dirs()]] `[EXTRACTED]` (L99)
- ←calls— [[.test_skips_node_modules()]] `[EXTRACTED]` (L106)
<!-- graphify:end -->

## Définition

`discover_sources(source_dir: Path, *, vault: Path | None = None, include_code: bool = False) -> list[dict]` parcourt `source_dir` avec `os.walk()`, retire des sous-dossiers les noms de `SKIP_DIRS` et les dossiers cachés, classe chaque fichier avec `_classify()`, ignore les fichiers `skip`, ignore les fichiers `code` sauf si `include_code` est vrai, puis renvoie des dicts `{path, kind, size_bytes}`. La taille est fournie par `_file_size()`, qui retourne `0` en cas d'erreur `OSError`.

Ce nœud est la porte d'entrée de la planification parce qu'il transforme un arbre de fichiers brut en liste normalisée que `plan_batches()` peut ensuite filtrer et découper. ^[inferred] Les tests associés montrent que le comportement attendu inclut les fichiers markdown, exclut le code par défaut, peut inclure le code sur option, ignore les binaires, `.git` et `node_modules`, et renseigne `size_bytes`. ^[inferred]

Le paramètre `vault` est présent dans la signature mais n'est pas utilisé dans le corps de la fonction; il sert probablement à garder une interface cohérente avec l'appel depuis `plan_batches()` ou avec des extensions futures. ^[inferred]

## Voir aussi

- [[plan_batches()]]
- [[_classify()]]
- [[test_batch.py]]
