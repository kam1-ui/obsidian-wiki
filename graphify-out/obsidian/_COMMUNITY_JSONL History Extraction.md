---
type: community
members: 20
---

# JSONL History Extraction

**Members:** 20 nodes

## Members
- [[Claude History Ingest Skill]] - code - .skills/claude-history-ingest/SKILL.md
- [[Codex History Ingest Skill]] - code - .skills/codex-history-ingest/SKILL.md
- [[Copilot History Ingest Skill]] - code - .skills/copilot-history-ingest/SKILL.md
- [[Cross-Linker Skill]] - code - .skills/cross-linker/SKILL.md
- [[LLM Wiki Core Pattern]] - concept - .skills/llm-wiki/SKILL.md
- [[Namespace_1]] - code
- [[Parse one JSONL conversation file and return the compact representation.      Re]] - rationale - scripts/extract-jsonl.py
- [[Return True if the source JSONL should be (re)extracted.      Idempotent stalene]] - rationale - scripts/extract-jsonl.py
- [[Return plain text from a message content field.      content is either a bare st]] - rationale - scripts/extract-jsonl.py
- [[_text_from_content()]] - code - scripts/extract-jsonl.py
- [[canonical()]] - code - scripts/extract-jsonl.py
- [[default_history_path()]] - code - scripts/extract-jsonl.py
- [[default_output_dir()]] - code - scripts/extract-jsonl.py
- [[extract-jsonl.py]] - code - scripts/extract-jsonl.py
- [[extract_conversation()]] - code - scripts/extract-jsonl.py
- [[is_skipped()]] - code - scripts/extract-jsonl.py
- [[main()_8]] - code - scripts/extract-jsonl.py
- [[needs_extraction()]] - code - scripts/extract-jsonl.py
- [[run()]] - code - scripts/extract-jsonl.py
- [[skip_patterns()]] - code - scripts/extract-jsonl.py

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/JSONL_History_Extraction
SORT file.name ASC
```

## Connections to other communities
- 1 edge to [[_COMMUNITY_Manifest CLI]]

## Top bridge nodes
- [[Claude History Ingest Skill]] - degree 3, connects to 1 community