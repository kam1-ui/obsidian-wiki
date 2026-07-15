# Plan: Promotion graphify-enrich → vault via wiki-ingest (candidate 1/2) — v5
_Locked via grill-with-docs — by Claude + kam1-ui. Terms per CONTEXT.md. Revised after Codex rounds 1 (36), 2 (25), 3 (12) and 4 (7 findings)._

## Goal

Refaire la promotion du staging (`graphify-out/enrichments/`) vers le vault par le mécanisme sanctionné `wiki-ingest` (issue #5), dans un **worktree isolé** du repo vault avec **staged writes**, gates déterministes puis audit sémantique indépendant, et comparaison humaine finale entre **deux vaults distincts** ouverts dans Obsidian. La branche `feature/vault-promotion-okf-export` reste la candidate 2, intacte.

## Naming (canonical)

- **Repo framework** : `/root/obsidian-wiki`, branche `feature/vault-promotion-wiki-ingest` (plan, docs, run report, findings).
- **Repo vault** : `/root/devnex/data/obsidian/vaults/obsidian-wiki`, branche candidate `test/wiki-ingest-promotion` depuis `BASE_SHA`.
- **Worktree candidat** : `/root/devnex/data/obsidian/vaults/obsidian-wiki-candidate` (sous le mount Docker, visible comme 2ᵉ vault Obsidian).
- **EVIDENCE_SHA** : le SHA complet résolu par `git rev-parse 2cc6426^{commit}` — comparé en égalité stricte au `built_at_commit` complet embarqué dans `graph.json` (R3 #2). C'est le commit framework contre lequel le graphe a été construit. Checkout read-only dédié pour l'audit (`git worktree` du repo framework à ce SHA).
- **RUN_ID** : `wip-promo-<date>` ; **run report** : `run-reports/<RUN_ID>.md` sur la branche framework — l'unique artefact d'observabilité (SHAs, prédicat, hashes, counts, configs résolues, findings, décisions).

## Config candidate (opérationnalisation — findings R2 #4/#5/#24)

Un `.env` local **à la racine du worktree candidat** :
```
OBSIDIAN_VAULT_PATH=/root/devnex/data/obsidian/vaults/obsidian-wiki-candidate
WIKI_STAGED_WRITES=true
```
Toute invocation de skill se fait avec CWD = worktree candidat (le Config Resolution Protocol résout ce `.env` en premier). **Avant chaque skill d'écriture** : résoudre et logger dans le run report les variables effectives (`OBSIDIAN_VAULT_PATH`, `WIKI_STAGED_WRITES`, toute variable `QMD_*` — résolution complète, y compris `~/.obsidian-wiki/config`), et stopper si `OBSIDIAN_VAULT_PATH` ne pointe pas le worktree. Ce `.env` ne fait jamais partie du merge final.

## Predicate spec (filtre déterministe — findings R2 #1/#7/#8, gelé avant le run)

Sur les 100 notes de `graphify-out/enrichments/` :
1. **Exclure tests** : basename matche `tests_*.enrichment.md` → 29 notes.
2. **Exclure trivia/invérifiable** : frontmatter `source_file` vide, absent, `null` ou `~` → réfs stdlib sans source dans le repo. Énumération gelée (4 hors tests) : `obsidian_wiki_cache_py_path`, `obsidian_wiki_cli_py_namespace`, `obsidian_wiki_cli_py_path`, `skills_skill_creator_eval_viewer_generate_review_py_path` (la 5ᵉ, `tests_test_doctor_py_path`, tombe déjà sous la règle 1). Justification individuelle : nœuds `Path`×3 et `Namespace`×1, références de types stdlib — aucune source repo à auditer, valeur de distillation nulle.
3. **Éligibles : 67 notes.** Pas de critère de degré (le `metadata.kind` de `graph.json` est absent sur 666/677 nœuds — un prédicat « kind d'abord » n'est pas implémentable ; le degré seul exclurait des nœuds architecturaux légitimes à faible degré, donc pas utilisé).
- **Gel** : liste triée dans `eligible-sources.txt` + deux hashes nommés, même algorithme (SHA-256 du flux des enregistrements triés `relpath\0sha256(contenu)\n`) : `ELIGIBLE_HASH` (les 67) et `STAGING_HASH` (les 100) (R3 #1). Golden cases dans le run report : inclusions attendues (`obsidian_wiki_cli`, `obsidian_wiki_cache`…), exclusions attendues (les 33 ci-dessus).
- **Preuve d'absence de trivia résiduel** (R3 #9, prédicats exacts R4 #2) : pour chacun des 67 éligibles, assertions déterministes : (i) `source_file` non vide ET le fichier existe dans le checkout à EVIDENCE_SHA ; (ii) `label` ∉ denylist stdlib gelée (liste explicite écrite au run report : `Path`, `Namespace`, `Any`, `TypedDict`, `ArgumentParser`, `CompletedProcess`, `BaseHTTPRequestHandler`, et tout identifiant importable de la stdlib repéré à l'exécution — la liste finale est gelée AVANT l'ingest). Résultat attendu : 67/67 pass ; l'inventaire résultant (label + source_file) est gelé dans le run report.

## Approach

0. **Pré-vol** — committer d'abord PLAN.md/CONTEXT.md/PLAN-REVIEW-LOG.md sur la branche framework ; ensuite `git status` des deux repos : stop sur toute saleté **non listée et acquittée** dans le run report (le fichier parasite `obsidian_wiki/Procédure — …` sera **déplacé hors du repo avant le run** (R3 #12)). Enregistrer RUN_ID, SHA framework HEAD, EVIDENCE_SHA (assertion : `graph.json.built_at_commit == EVIDENCE_SHA` — le SHA complet résolu, seule comparaison utilisée, R4 #1), SHA `main` vault, configs résolues.
1. **Bootstrap taxonomie** — `_meta/taxonomy.md` n'existe pas et `tag-taxonomy` présuppose son existence : bootstrap explicite (vocabulaire depuis les tags des 20 pages actuelles + domaines du staging), **approbation humaine du vocabulaire avant commit**, commit sur `main` du vault → `BASE_SHA`. La baseline de comparaison est `BASE_SHA`.
2. **Worktree candidat** — `git worktree add <worktree> -b test/wiki-ingest-promotion BASE_SHA` + création du `.env` candidat (section Config).
3. **Filtre** — exécuter le Predicate spec, produire `eligible-sources.txt` + hashes + golden checks, tout dans le run report. Échec d'un golden check → stop.
4. **Plan de pages global** (finding R2 #9/#10) — AVANT toute écriture : construire le plan communautés → pages sur l'ensemble des 67 notes (étend le Step 4 du skill au global). Budget : **8–20 pages** ; chaque communauté retenue mappe vers ≥ 1 page (fusion multi-communautés autorisée). Plan écrit dans le run report.
5. **Run `wiki-ingest`** — mode full, staged writes, CWD = worktree. **Déviation sanctionnée du Step 0 du skill, documentée** (finding R2 #3) : pas de subagents parallèles (hasards d'écriture concurrente sur `.manifest.json`/`index.md`/`log.md`, distillation inter-lots non fiable) — invocations séquentielles, une par groupe de communautés ≤ 20 fichiers, avec la mention prévue par le skill (« Skip batch-plan — these files are already partitioned »). Annoncer l'estimation tokens avant de lancer.
6. **`wiki-stage-commit`** — revue par fichier effectuée par Claude (contrôle de contenu — adaptation documentée : le mécanisme staged sert ici l'isolation/atomicité ; le gate humain reste la sélection finale, finding R2 #14). Exigence : `_staging/` **vide** après promotion ; **l'éligibilité est immuable** — un rejet déclenche re-planification/ré-ingestion de la source concernée ou l'échec de la candidate, jamais un recalcul du set gelé (R3 #10). Puis **réconciliation `index.md`** (reconstruire/dédupliquer depuis les pages vivantes, R2 #12) et **réécriture des chemins du manifest** : les entrées `pages_created`/`pages_updated` pointant vers `_staging/...` sont réécrites vers les emplacements finaux AVANT la QA manifest (R4 #6). Commit.
7. **`cross-linker`** — avant les gates, en **deux phases** car le skill n'a ni allowlist ni dry-run natifs (R3 #7) : (a) **preview** — dérouler les étapes de découverte/scoring du skill SANS appliquer, produire la liste des éditions proposées ; filtrage déterministe : ne retenir que les **mentions littérales non liées avec cible de registre non ambiguë** — aucun lien issu du score seul (tags partagés, affinité de dossier) (R3 #8, remplace « EXTRACTED only ») ; éditions réciproques sur pages baseline listées et approuvées avant application ; (b) **apply** — appliquer uniquement le patch set approuvé ; toute modification hors liste → échec (R2 #18). Stoplist domaine (`Path`, `run`, `main`, `query`, `Namespace`, génériques) ; cibles path-qualified en collision. Commit. Contenu **gelé** ensuite.
8. **Gate 1 — QA déterministe** (scripts, périmètre = git diff worktree depuis BASE_SHA, chaque chemin classifié) :
   - YAML parsable ; **deux schémas distincts** (R2 #15) : pages neuves = schéma complet (`title/category/tags/sources/created/updated/summary/lifecycle/lifecycle_changed/tier/base_confidence` + `provenance` sommant ≈ 1.0) ; pages mises à jour = lifecycle préservé, `updated` avancé, `summary` présent et cohérent avec le contenu, `sources:` inclut les nouvelles sources de ce run, `provenance` sommant ≈ 1.0 si présent, `base_confidence` présent (recalcul attendu si les sources ont matériellement changé — contrat du skill, R4 #5) ; pas d'exigence de backfill au-delà ;
   - tags 100 % dans `_meta/taxonomy.md` (`visibility/*` validés séparément, ≤ 5 tags domaine) ;
   - `relationships[]` : type ∈ enum autorisé, cible existante, format wikilink, pas de doublons (R2 #16) ;
   - unicité slugs/basenames ; pas de lien court ambigu ;
   - `lint_vault()` : **0 broken link, 0 orphan candidat** (seuils explicites, R3 #3), règles de scan/exclusion écrites au run report + recomptage indépendant in/out-degree des pages candidates (0 orphelin recompté) ;
   - manifest : schéma, hashes, existence des pages, **couverture** = chaque source éligible a une entrée manifest ET figure dans le `sources:` d'au moins une page (réciprocité manifest→pages) (R2 #11) ;
   - `index.md` rebuild-check, entrées `log.md` parsables et rattachées au RUN_ID — les templates du skill n'émettent pas de RUN_ID : annotation post-opération déterministe, chaque entrée émise par ce run est suffixée ` run_id=<RUN_ID>` immédiatement après l'opération (R4 #7), `hot.md` rafraîchi dans la fenêtre du run (R2 #17) ;
   - comptage pages dans [8, 20].
9. **Gate 2 — audit sémantique indépendant** — session Codex fraîche `--sandbox read-only` ; identité modèle/prompt/entrées/SHAs consignés. **Inventaire en deux volets** (R4 #3) : volet déterministe = source→pages via `sources:` (scriptable) ; volet claims = attribution phrase-par-source produite PAR l'auditeur comme artefact audité (les `sources:` sont page-level — l'attribution fine n'est pas scriptable et n'est pas prétendue déterministe). **L'auditeur rend une disposition pass/fail par source éligible** (la substance a-t-elle survécu à la distillation, R3 #4), stockée séparément : `audit/source-dispositions-<RUN_ID>.jsonl`, schéma `{source, verdict: pass|fail, finding_ids: []}` (R4 #4). Mandat : `^[inferred]` + claims non marqués + relations + omissions/distorsions, evidence = checkout à EVIDENCE_SHA. Sortie : `audit/findings-<RUN_ID>.jsonl` sur la branche framework, schéma élargi (R3 #5/#6) : `{id: "<RUN_ID>-R<round>-F<seq>" (unique, jamais réutilisé), page, source, claim_id, quote, class: wrong|overreach|stale|omission|distortion|unsupported_relation|ambiguous_evidence, severity, verdict, evidence_file?, evidence_line?, note}`.
10. **Corrections** — Claude écrit, chaque commit référence des IDs de findings. MAX 2 rounds ; après chaque round : re-gate 1 + re-audit. Au-delà → échec de la candidate.
11. **Gate humain** — deux vaults ouverts dans Obsidian (baseline `main`@BASE_SHA vs worktree candidat) + rapport de comparaison (inventaires, métriques des critères verrouillés, git diff). Décision enregistrée dans le run report. **Merge allowlist** (R2 #23) : pages finales + `index.md`/`log.md`/`hot.md` + `.manifest.json` ; exclus : `.env` candidat, `_staging/` (vide vérifié), artefacts de run. **Enforcement** (R3 #11) : assertion pré-merge `git diff --name-only BASE_SHA..test/wiki-ingest-promotion` ⊆ allowlist, abort sur tout chemin inattendu. **Lifecycle `draft → reviewed`** : commit séparé post-approbation, validé mécaniquement (le diff ne touche que `lifecycle`/`lifecycle_changed`/`updated` des pages approuvées — pas de re-run complet des gates, R2 #22). Perdant : branche archivée. Si wiki-ingest perd → candidate `okf-export`. Nettoyage du worktree après merge (rollback = SHAs du run report).

## Key decisions & tradeoffs

- **Worktree isolé + staged writes** (R1 #11/#12/#13/#36) ; **cross-linker avant les gates, contenu gelé ensuite** (R1 #28) ; **séquentiel par communauté** (R1 #9/#10, déviation Step 0 documentée R2 #3).
- **EVIDENCE_SHA = `built_at_commit` de graph.json** (R2 #6) — l'alignement graphe↔code est prouvé par l'artefact lui-même, pas supposé.
- **Prédicat trivia = source_file vide, énuméré et justifié fichier par fichier** (R2 #7/#8) — le seul critère sémantiquement juste ET implémentable depuis les données réelles ; le degré est écarté (exclurait des nœuds architecturaux à faible degré).
- **Cross-linker en mode EXTRACTED only** (R2 #19) — la précision prime sur le rappel pour un run d'expérimentation ; les liens INFERRED reviendront dans la vie normale du vault.
- **Deux branches candidates jamais écrasées ; QA déterministe avant LLM ; auditeur ≠ générateur** — inchangés.

## Findings tempérés (arbitrage Claude, loggé)

- R1 #31 : décision enregistrée dans le run report, pas d'apparat de signature. R1 #34 : un seul run report markdown.
- R2 #19 : « approbation manuelle de chaque lien INFERRED » remplacée par la désactivation pure des liens INFERRED ce run (plus simple, plus strict).

## Risks / open questions

- Comportement réel de distillation de `wiki-ingest` sur ce type de source — l'inconnue que le run mesure.
- Coût tokens Claude du run (annoncé avant l'étape 5).
- Le plan de pages global (étape 4) est produit par Claude — sa qualité conditionne la distillation ; le gate humain final le voit via le rapport de comparaison.

## Out of scope

- Candidate OKF (branche + plan séparés si activée). Issue #2 (corrections baseline) : traitée après le gate humain selon le gagnant. Staging en lecture seule. Issue #1 (Docker/wiki-setup). Plugin Obsidian Git.
