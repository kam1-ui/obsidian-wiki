---
node: obsidian_wiki_cache_sha256_file
title: "sha256_file()"
community: "Ingest Cache/Staleness"
source_file: "obsidian_wiki/cache.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# sha256_file()

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Ingest Cache/Staleness · **Fichier:** `obsidian_wiki/cache.py` · **Degré:** 11

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[cache.py]] `[EXTRACTED]` (L69)
- —references→ [[Path]] `[EXTRACTED]` (L69)
- ←calls— [[compute_hash()]] `[EXTRACTED]` (L95)
- ←rationale_for— [[Return the hex SHA-256 digest of *path* without loading it all into RAM.]] `[EXTRACTED]` (L70)
- ←calls— [[sha256_dir()]] `[EXTRACTED]` (L88)
- ←imports— [[test_cache.py]] `[EXTRACTED]` (L10)
- ←calls— [[.test_cache_hash_file()]] `[EXTRACTED]` (L178)
- ←calls— [[.test_hash_file_alias()]] `[EXTRACTED]` (L73)
- ←calls— [[.test_sha256_file_changes_on_edit()]] `[EXTRACTED]` (L54)
- ←calls— [[.test_sha256_file_deterministic()]] `[EXTRACTED]` (L51)
- ←calls— [[.test_records_correct_hash()]] `[EXTRACTED]` (L134)
<!-- graphify:end -->

## Définition

`sha256_file(path: Path, chunk: int = 1 << 20) -> str` calcule le digest SHA-256 hexadécimal d'un fichier en l'ouvrant en binaire et en lisant des blocs successifs de taille `chunk`. La fonction met à jour un objet `hashlib.sha256()` jusqu'à EOF puis retourne `h.hexdigest()`, ce qui évite de charger tout le fichier en mémoire.

Dans le graphe, c'est la primitive de hash fichier utilisée directement par `sha256_dir()` pour chaque fichier d'un arbre et par `compute_hash()` quand la cible n'est pas un répertoire. ^[inferred] Les tests couvrent sa déterminisme, sa sensibilité aux modifications de contenu et son équivalence avec l'alias `hash_file()`. ^[inferred]

## Voir aussi

- [[obsidian_wiki_cache_sha256_dir]]
- [[obsidian_wiki_cache_compute_hash]]
- [[obsidian_wiki_cache_hash_file]]
- [[tests_test_cache_testhashing]]
