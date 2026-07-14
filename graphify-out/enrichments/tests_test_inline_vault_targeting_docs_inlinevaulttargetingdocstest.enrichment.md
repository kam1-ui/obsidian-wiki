---
node: tests_test_inline_vault_targeting_docs_inlinevaulttargetingdocstest
title: "InlineVaultTargetingDocsTest"
community: "Inline Vault Targeting Tests"
source_file: "tests/test_inline_vault_targeting_docs.py"
tags: [graphify/enrichment]
claim_provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
---

# InlineVaultTargetingDocsTest

<!-- graphify:begin — bloc auto-régénéré, ne pas éditer -->
**Communauté:** Inline Vault Targeting Tests · **Fichier:** `tests/test_inline_vault_targeting_docs.py` · **Degré:** 8

### Connexions (EXTRACTED — depuis graph.json)
- ←contains— [[test_inline_vault_targeting_docs.py]] `[EXTRACTED]` (L10)
- —method→ [[.read()]] `[EXTRACTED]` (L11)
- —method→ [[.test_agent_bootstrap_files_mention_named_vault_routing()]] `[EXTRACTED]` (L34)
- —method→ [[.test_central_protocol_documents_inline_override_before_fallbacks()]] `[EXTRACTED]` (L14)
- —method→ [[.test_core_skill_descriptions_include_named_vault_examples()]] `[EXTRACTED]` (L54)
- —method→ [[.test_readme_says_all_supported_agents_inherit_named_vault_routing()]] `[EXTRACTED]` (L48)
- —method→ [[.test_skill_resolution_summaries_include_inline_override()]] `[EXTRACTED]` (L23)
- —method→ [[.test_wiki_query_does_not_prefer_default_over_inline_override()]] `[EXTRACTED]` (L65)
<!-- graphify:end -->

## Définition

`InlineVaultTargetingDocsTest` est une classe `unittest.TestCase` qui lit les documents du dépôt et vérifie que le routage `@name` est décrit avant les mécanismes de repli, présent dans les fichiers d’amorçage, illustré dans les skills principaux et correctement formulé dans le README. Elle vérifie également que `wiki-query` ne donne pas priorité au vault par défaut lorsqu’un override inline est fourni.

Cette suite protège la cohérence documentaire du protocole de ciblage entre [[LLM Wiki Skill]], [[Obsidian Wiki Agent Context]] et les différentes intégrations d’agents. ^[inferred]

## Voir aussi

- [[LLM Wiki Skill]]
- [[Obsidian Wiki Agent Context]]
