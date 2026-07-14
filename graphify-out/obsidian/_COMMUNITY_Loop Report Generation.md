---
type: community
members: 32
---

# Loop Report Generation

**Members:** 32 nodes

## Members
- [[Call Claude to improve the description based on eval results.]] - rationale - .skills/skill-creator/scripts/improve_description.py
- [[Find the project root by walking up from cwd looking for .claude.      Mimics h]] - rationale - .skills/skill-creator/scripts/run_eval.py
- [[Generate HTML report from loop output data. If auto_refresh is True, adds a meta]] - rationale - .skills/skill-creator/scripts/generate_report.py
- [[Parse a SKILL.md file, returning (name, description, full_content).]] - rationale - .skills/skill-creator/scripts/utils.py
- [[Path_2]] - code
- [[Path_4]] - code
- [[Path_5]] - code
- [[Path_6]] - code
- [[Run `claude -p` with the prompt on stdin and return the text response.      Prom]] - rationale - .skills/skill-creator/scripts/improve_description.py
- [[Run a single query and return whether the skill was triggered.      Creates a co]] - rationale - .skills/skill-creator/scripts/run_eval.py
- [[Run the eval + improvement loop.]] - rationale - .skills/skill-creator/scripts/run_loop.py
- [[Run the full eval set and return results.]] - rationale - .skills/skill-creator/scripts/run_eval.py
- [[Shared utilities for skill-creator scripts.]] - rationale - .skills/skill-creator/scripts/utils.py
- [[Split eval set into train and test sets, stratified by should_trigger.]] - rationale - .skills/skill-creator/scripts/run_loop.py
- [[_call_claude()]] - code - .skills/skill-creator/scripts/improve_description.py
- [[find_project_root()]] - code - .skills/skill-creator/scripts/run_eval.py
- [[generate_html()_1]] - code - .skills/skill-creator/scripts/generate_report.py
- [[generate_report.py]] - code - .skills/skill-creator/scripts/generate_report.py
- [[improve_description()]] - code - .skills/skill-creator/scripts/improve_description.py
- [[improve_description.py]] - code - .skills/skill-creator/scripts/improve_description.py
- [[main()_2]] - code - .skills/skill-creator/scripts/generate_report.py
- [[main()_3]] - code - .skills/skill-creator/scripts/improve_description.py
- [[main()_5]] - code - .skills/skill-creator/scripts/run_eval.py
- [[main()_6]] - code - .skills/skill-creator/scripts/run_loop.py
- [[parse_skill_md()]] - code - .skills/skill-creator/scripts/utils.py
- [[run_eval()]] - code - .skills/skill-creator/scripts/run_eval.py
- [[run_eval.py]] - code - .skills/skill-creator/scripts/run_eval.py
- [[run_loop()]] - code - .skills/skill-creator/scripts/run_loop.py
- [[run_loop.py]] - code - .skills/skill-creator/scripts/run_loop.py
- [[run_single_query()]] - code - .skills/skill-creator/scripts/run_eval.py
- [[split_eval_set()]] - code - .skills/skill-creator/scripts/run_loop.py
- [[utils.py]] - code - .skills/skill-creator/scripts/utils.py

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Loop_Report_Generation
SORT file.name ASC
```
