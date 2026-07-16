---
node: obsidian_wiki_cache_sha256_dir
title: "sha256_dir()"
community: "Ingest Cache/Staleness"
source_file: "obsidian_wiki/cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.6
  inferred: 0.4
  ambiguous: 0.0
---

# sha256_dir()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `obsidian_wiki/cache.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cache.py]] `[EXTRACTED]` (L81)
- —references→ [[Path]] `[EXTRACTED]` (L81)
- —calls→ [[sha256_file()]] `[EXTRACTED]` (L88)
- ←calls— [[compute_hash()]] `[EXTRACTED]` (L94)
- ←rationale_for— [[Stable SHA-256 over all files in a directory tree (sorted by relative path).]] `[EXTRACTED]` (L82)
- ←imports— [[test_cache.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_sha256_dir_changes_on_edit()]] `[EXTRACTED]` (L63)
- ←calls— [[.test_sha256_dir_deterministic()]] `[EXTRACTED]` (L60)
<!-- graphify:end -->

## Définition

`sha256_dir(path: Path) -> str` calcule un SHA-256 stable sur tous les fichiers d'une arborescence. La fonction parcourt `sorted(path.rglob("*"))`, ignore les entrées non fichiers, injecte le chemin relatif encodé puis le digest `sha256_file(fp)` de chaque fichier, et retourne le digest final.

Son rôle est de donner à `compute_hash()` une représentation de contenu pour les répertoires, sensible à la fois aux chemins relatifs et aux contenus des fichiers. ^[inferred] Les tests associés vérifient que le hash de répertoire est déterministe et change quand un fichier enfant est édité. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cache_sha256_file]]
- [[obsidian_wiki_cache_compute_hash]]
- [[tests_test_cache_testhashing]]
