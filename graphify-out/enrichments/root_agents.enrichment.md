---
node: root_agents
title: "Obsidian Wiki Agent Context"
community: "Agent Context Files"
source_file: "AGENTS.md"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# Obsidian Wiki Agent Context

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Agent Context Files · **Fichier:** `AGENTS.md` · **Degré:** 7

### Connexions (EXTRACTED — depuis graph.json)
- ←references— [[Hermes Agent Context]] `[EXTRACTED]`
- ←references— [[Antigravity Rules]] `[EXTRACTED]`
- ←references— [[Antigravity Workflows]] `[EXTRACTED]`
- ←references— [[Copilot Instructions]] `[EXTRACTED]`
- ←references— [[Kiro Steering Rules]] `[EXTRACTED]`
- ←references— [[Claude Agent Context]] `[EXTRACTED]`
- ←references— [[Gemini Agent Context]] `[EXTRACTED]`
<!-- graphify:end -->

## Définition

`AGENTS.md` fournit aux agents le contexte du framework Obsidian Wiki : résolution du vault, structure attendue, routage des intentions vers les skills, usages inter-projets, visibilité et principes de maintenance. Il impose notamment que l’override inline `@name` précède les recherches de configuration locale et globale, puis que le fichier `AGENTS.md` propre au vault soit lu s’il existe.

Ce document est le point d’amorçage commun dont les fichiers de contexte propres aux différents agents reprennent les conventions et le catalogue de capacités. ^[inferred]

## Voir aussi

- [[LLM Wiki Skill]]
- [[InlineVaultTargetingDocsTest]]
