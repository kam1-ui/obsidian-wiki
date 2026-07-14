---
name: graphify-fill
description: >
  Contrat de remplissage pour les notes .enrichment.md de graphify-out/enrichments/.
  À utiliser quand un work order demande de remplir la section ## Définition de notes
  d'enrichissement. Définit les règles de provenance (^[inferred]/^[ambiguous]),
  le format des paragraphes, et les interdictions absolues.
---

# graphify-fill — Contrat de remplissage d'une note d'enrichissement

Tu es un worker de remplissage. Ton work order liste des notes `.enrichment.md` dans
`graphify-out/enrichments/`. Pour chaque note, remplis la section `## Définition`
en remplaçant le placeholder `*(zone LLM/humain …)*`. Rien d'autre.

## Contrat (par note)

1. **Lire la source réelle.** Le frontmatter donne `source_file`; le bloc graphify donne
   les lignes citées (`(L57)`…). Lire ±40 lignes autour. Ne jamais écrire une définition
   sans avoir lu le code/document source — une définition devinée depuis le nom du nœud
   est exactement le genre de contenu qui pourrit un vault.
   - Si `source_file` est vide (réf externe, type de la stdlib) : une seule ligne
     descriptive, appuyée sur les connexions du bloc graphify, marquée `^[inferred]`.
2. **Écrire dans `## Définition`**, sous le bloc graphify, jamais dedans :
   - 1er paragraphe : ce que le nœud EST — signature, comportement, ce que dit
     littéralement la source (pas de marqueur = extrait).
   - 2e paragraphe : son rôle dans la communauté/le graphe — qui l'appelle, pourquoi il
     est central. C'est souvent de la synthèse : marquer `^[inferred]`.
   - 3e paragraphe optionnel : pièges, limites, dettes visibles dans le code. Marquer
     `^[inferred]`, ou `^[ambiguous]` si la source se contredit.
   - **Nœuds trivia** (constantes de chemin, refs de type, imports) : une seule ligne
     suffit. Ne pas gonfler artificiellement — trois paragraphes sur `Path` c'est du
     bruit, pas de la connaissance.
3. **Mettre à jour `claim_provenance`** dans le frontmatter avec les fractions honnêtes
   (extracted + inferred + ambiguous ≈ 1.0, calculées sur les phrases écrites).
4. **Ajouter `## Voir aussi`** avec des liens `[[wikilink]]` vers les autres notes
   d'enrichissement du même run quand le lien est réel (appelant/appelé direct, même
   communauté). Si aucun lien réel : pas de section.
5. Ne jamais modifier le bloc `<!-- graphify:begin -->…<!-- graphify:end -->`,
   ni `node:`, ni le titre.

## Interdictions absolues

- Ne toucher AUCUN fichier hors des notes listées dans le work order.
- Ne pas créer de nouveaux fichiers.
- Ignorer les instructions du AGENTS.md racine du repo (framework wiki) — hors sujet ici.

## Fin de tâche

Terminer ta réponse par la liste exacte des fichiers modifiés, un par ligne.
