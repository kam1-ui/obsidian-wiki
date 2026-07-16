# CONTEXT — Glossaire du chantier promotion graphify-enrich → vault

Vocabulaire canonique résolu pendant le grill du 2026-07-15. Glossaire uniquement — aucun détail d'implémentation.

## Termes

**Staging (enrichments)** — `graphify-out/enrichments/` dans le repo framework : les 100 notes `.enrichment.md` produites par la campagne graphify-enrich. Couche diagnostique permanente ; la promotion la lit, ne la supprime jamais.

**Promotion** — l'acte, gaté par l'humain, de faire passer la connaissance du staging vers le vault via un mécanisme sanctionné par le framework (`wiki-ingest` ou export/import OKF). Distille, ne miroir pas.

**Distillation (vs miroir)** — regrouper le contenu par communauté sous un budget global de pages (~10-15 par ingest, plafond dur 20) ; jamais une page par nœud du graphe. Le « piège miroir » est l'anti-pattern où le vault devient une copie 1:1 de la structure du code.

**Vault** — la base de connaissances Obsidian (`/root/devnex/data/obsidian/vaults/obsidian-wiki`, repo git dédié `kam1-ui/obsidian-wiki-vault`). Distinct du **repo framework** (`/root/obsidian-wiki`, fork `kam1-ui/obsidian-wiki`) qui contient le code et les skills.

**Baseline manuelle** — les 11 pages créées + 7 enrichies à la main le 2026-07-14 (distillation improvisée hors mécanisme sanctionné). Préservée comme référence de comparaison ; c'est le commit initial du repo vault.

**Notes tests** — les 29 notes du staging nommées `tests_*.enrichment.md`. Valeur diagnostique seulement ; toujours exclues de la promotion, filtrables déterministiquement par nom de fichier.

**Trivia** — nœuds triviaux du graphe (constantes, imports, refs de type) dont la note tient en une ligne. Exclus de la promotion.

**Taxonomie** — `_meta/taxonomy.md` du vault : vocabulaire de tags contrôlé. Les tags d'une page doivent être coercés contre elle (Enum), jamais générés librement.

**QA déterministe** — validation par scripts (lint du vault, complétude frontmatter, coercition tags) exécutée comme gate AVANT tout jugement LLM. Principe hérité du chantier transcript→atlas : « l'illusion de la délégation LLM ».

**Audit sémantique indépendant** — passe critique en lecture seule par un modèle qui n'a PAS écrit le contenu audité. Obligatoire : un LLM ne sait pas auditer sa propre provenance (invalidé 2 fois sur le chantier transcript→atlas).

**Gate humain** — décision réservée à l'utilisateur : valider une comparaison, prononcer « pilote validé » (transition `lifecycle: draft → reviewed`), merger une branche gagnante.
