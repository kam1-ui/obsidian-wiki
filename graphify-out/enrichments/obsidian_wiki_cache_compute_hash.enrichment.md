---
node: obsidian_wiki_cache_compute_hash
title: "compute_hash()"
community: "Ingest Cache/Staleness"
source_file: "obsidian_wiki/cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# compute_hash()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `obsidian_wiki/cache.py` · **Degré:** 10

### Connexions (EXTRACTED — depuis graph.json)
- ←imports— [[batch.py]] `[EXTRACTED]` (L139)
- ←contains— [[cache.py]] `[EXTRACTED]` (L92)
- —references→ [[Path]] `[EXTRACTED]` (L92)
- —calls→ [[sha256_file()]] `[EXTRACTED]` (L95)
- —calls→ [[sha256_dir()]] `[EXTRACTED]` (L94)
- ←calls— [[check_sources()]] `[EXTRACTED]` (L111)
- ←calls— [[hash_file()]] `[EXTRACTED]` (L151)
- ←calls— [[update_source()]] `[EXTRACTED]` (L138)
- ←imports— [[test_cache.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_compute_hash_dispatches()]] `[EXTRACTED]` (L69)
<!-- graphify:end -->

## Définition

`compute_hash(path: Path) -> str` est le dispatcher de hash de contenu : il appelle `sha256_dir(path)` si `path.is_dir()` est vrai, sinon `sha256_file(path)`. Il retourne directement le digest produit par la branche choisie.

Ce nœud centralise la décision fichier/répertoire pour les opérations de cache, ce qui permet à `check_sources()`, `update_source()` et `hash_file()` de partager la même sémantique de contenu. ^[inferred] Le test `test_compute_hash_dispatches` vérifie que les deux branches produisent bien une chaîne SHA-256 hexadécimale de 64 caractères. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cache_sha256_file]]
- [[obsidian_wiki_cache_sha256_dir]]
- [[obsidian_wiki_cache_hash_file]]
- [[tests_test_cache_testhashing]]
