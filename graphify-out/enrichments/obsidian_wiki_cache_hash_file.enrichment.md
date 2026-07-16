---
node: obsidian_wiki_cache_hash_file
title: "hash_file()"
community: "Ingest Cache/Staleness"
source_file: "obsidian_wiki/cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.5
  inferred: 0.5
  ambiguous: 0.0
---

# hash_file()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `obsidian_wiki/cache.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cache.py]] `[EXTRACTED]` (L149)
- —references→ [[Path]] `[EXTRACTED]` (L149)
- —calls→ [[compute_hash()]] `[EXTRACTED]` (L151)
- ←rationale_for— [[Just compute and return the hash — no manifest I/O.]] `[EXTRACTED]` (L150)
- ←imports— [[cli.py]] `[EXTRACTED]` (L694)
- ←calls— [[cmd_cache_hash()]] `[EXTRACTED]` (L699)
- ←imports— [[test_cache.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_hash_file_alias()]] `[EXTRACTED]` (L73)
<!-- graphify:end -->

## Définition

`hash_file(path: Path) -> str` est une fonction publique mince qui retourne `compute_hash(path)`. Sa docstring précise qu'elle calcule et retourne seulement le hash, sans entrée-sortie de manifeste.

Dans le graphe, elle sert d'API stable pour la commande CLI `cache-hash`, qui résout le chemin, refuse les chemins inexistants et imprime un JSON contenant `path` et `sha256`. ^[inferred] Malgré son nom orienté fichier, elle délègue à `compute_hash()` et hérite donc aussi de la prise en charge des répertoires. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cache_compute_hash]]
- [[obsidian_wiki_cache_sha256_file]]
- [[tests_test_cache_testcachecli]]
- [[tests_test_cache_testhashing]]
