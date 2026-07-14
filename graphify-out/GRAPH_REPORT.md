# Graph Report - .  (2026-07-12)

## Corpus Check
- 117 files · ~151,714 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 677 nodes · 1204 edges · 48 communities (26 shown, 22 thin omitted)
- Extraction: 97% EXTRACTED · 3% INFERRED · 0% AMBIGUOUS · INFERRED: 31 edges (avg confidence: 0.62)
- Token cost: 221,820 input · 6,440 output

## Community Hubs (Navigation)
- Graph Analysis Engine
- GraphRAG Query System
- Ingest Cache/Staleness
- CLI Command Layer
- Batch Discovery/Planning
- AST Extraction
- Loop Report Generation
- Skill Eval Review Viewer
- Browser Extension Popup
- Extension Manifest
- JSONL History Extraction
- Wiki Lint Checks
- Manifest Delta Tests
- Extension Background Script
- Manifest CLI
- Benchmark Aggregation
- Wiki Skills Reference Pages
- Doctor CLI Tests
- Extract Staleness Tests
- Wiki Ops Skills
- Wiki Skill Definitions A
- Skill Packaging
- Inline Vault Targeting Tests
- OKF Link Roundtrip Tests
- Agent Context Files
- Query CLI Tests
- Batch Plan CLI Tests
- Brain Vault Capture Assets
- Daily Update Script
- Wiki Notify Script
- Setup Script
- Capture Stop Script
- Package Init
- Obsidian Layout Skill
- Wiki Export/Import Skills
- Brain Icon 128
- Brain Icon 16
- Brain Icon 48
- Obsidian Wiki Vault Node
- obsidian-wiki Root
- Skill Creator Skill
- README (English)
- README (Traditional Chinese)
- Setup Guide
- Wiki Dashboard Skill
- Wiki Dedup Skill
- Wiki Digest Skill

## God Nodes (most connected - your core abstractions)
1. `parse_vault_graph()` - 26 edges
2. `build_index()` - 25 edges
3. `update_source()` - 22 edges
4. `query()` - 19 edges
5. `extract_file()` - 18 edges
6. `plan_batches()` - 18 edges
7. `check_sources()` - 18 edges
8. `build_parser()` - 17 edges
9. `analyse_vault()` - 17 edges
10. `_write()` - 16 edges

## Surprising Connections (you probably didn't know these)
- `_install_all_skills()` --calls--> `list_skills()`  [EXTRACTED]
  tests/test_doctor.py → obsidian_wiki/cli.py
- `Hermes Agent Context` --references--> `Obsidian Wiki Agent Context`  [EXTRACTED]
  .hermes.md → AGENTS.md
- `Antigravity Rules` --references--> `Obsidian Wiki Agent Context`  [EXTRACTED]
  .agent/rules/obsidian-wiki.md → AGENTS.md
- `Antigravity Workflows` --references--> `Obsidian Wiki Agent Context`  [EXTRACTED]
  .agent/workflows/obsidian-wiki.md → AGENTS.md
- `Copilot Instructions` --references--> `Obsidian Wiki Agent Context`  [EXTRACTED]
  .github/copilot-instructions.md → AGENTS.md

## Import Cycles
- None detected.

## Hyperedges (group relationships)
- **Agent Bootstrap Layer** — root_hermes, root_agents, root_claude, root_gemini, agent_rules_obsidian_wiki, kiro_steering_obsidian_wiki, github_copilot_instructions [EXTRACTED 1.00]
- **History Ingestion Skills** — skills_claude_history_ingest_skill, skills_codex_history_ingest_skill, skills_copilot_history_ingest_skill [EXTRACTED 0.90]
- **Wiki Maintenance and Ingestion Flow** — root_obsidian_wiki_skills_daily_update_skill, root_obsidian_wiki_skills_hermes_history_ingest_skill, root_obsidian_wiki_skills_openclaw_history_ingest_skill, root_obsidian_wiki_skills_pi_history_ingest_skill, root_obsidian_wiki_skills_tag_taxonomy_skill [EXTRACTED 0.90]
- **Obsidian UI and Visualization Customization** — root_obsidian_wiki_skills_graph_colorize_skill, root_obsidian_wiki_skills_obsidian_layout_adjustment_skill [INFERRED 0.80]
- **Obsidian Wiki Agent Skills** — skills_wiki_ingest_skill, skills_wiki_query_skill, skills_wiki_capture_skill, skills_wiki_lint_skill, skills_wiki_dashboard_skill, skills_wiki_export_skill, skills_wiki_import_skill [EXTRACTED 1.00]
- **Agent History Ingestion Flow** — skills_wiki_history_ingest_skill, skills_wiki_agent_skill, skills_wiki_ingest_skill [EXTRACTED 0.90]
- **Obsidian Wiki Core Skills** — skills_wiki_setup_skill, skills_wiki_status_skill, skills_wiki_update_skill, skills_wiki_research_skill, skills_wiki_synthesize_skill [EXTRACTED 1.00]
- **Brain Capture Extension Components** — extensions_brain_capture_readme, extensions_brain_capture_popup_html, extensions_brain_capture_assets_obsidian_brain [EXTRACTED 1.00]

## Communities (48 total, 22 thin omitted)

### Community 0 - "Graph Analysis Engine"
Cohesion: 0.06
Nodes (37): analyse_vault(), _build_degree_tables(), dead_ends(), detect_communities(), detect_communities_greedy(), god_nodes(), isolated(), _label_community() (+29 more)

### Community 1 - "GraphRAG Query System"
Cohesion: 0.07
Nodes (23): build_index(), classify_query(), find_path(), Any, Path, query(), rank_candidates(), GraphRAG query index for wiki-query.  Builds a compact in-memory index from vaul (+15 more)

### Community 2 - "Ingest Cache/Staleness"
Cohesion: 0.08
Nodes (24): check_sources(), CheckResult, compute_hash(), hash_file(), _load_manifest(), _manifest_path(), Path, Content-hash cache for wiki-ingest source tracking.  Provides a reliable, platfo (+16 more)

### Community 3 - "CLI Command Layer"
Cohesion: 0.11
Nodes (49): ArgumentParser, _add_setup_args(), bootstrap_dir(), build_parser(), _check_stale(), cmd_ast_extract(), cmd_batch_plan(), cmd_cache_check() (+41 more)

### Community 4 - "Batch Discovery/Planning"
Cohesion: 0.08
Nodes (20): _classify(), discover_sources(), _file_size(), _filter_unchanged(), _make_batches(), plan_batches(), Any, Path (+12 more)

### Community 5 - "AST Extraction"
Cohesion: 0.07
Nodes (21): Edge, extract(), extract_directory(), extract_file(), _file_id(), Graph, LangSpec, Node (+13 more)

### Community 6 - "Loop Report Generation"
Cohesion: 0.11
Nodes (27): generate_html(), main(), Generate HTML report from loop output data. If auto_refresh is True, adds a meta, _call_claude(), improve_description(), main(), Path, Run `claude -p` with the prompt on stdin and return the text response.      Prom (+19 more)

### Community 7 - "Skill Eval Review Viewer"
Cohesion: 0.15
Nodes (19): BaseHTTPRequestHandler, build_run(), embed_file(), find_runs(), _find_runs_recursive(), generate_html(), get_mime_type(), _kill_port() (+11 more)

### Community 8 - "Browser Extension Popup"
Cohesion: 0.11
Nodes (18): buildMarkdown(), captureButton, chooseFolder, copyStatus, escapeYaml(), folderStatus, getUniqueFileHandle(), init() (+10 more)

### Community 9 - "Extension Manifest"
Cohesion: 0.09
Nodes (21): action, default_icon, default_popup, default_title, background, service_worker, 128, 16 (+13 more)

### Community 10 - "JSONL History Extraction"
Cohesion: 0.15
Nodes (19): canonical(), default_history_path(), default_output_dir(), extract_conversation(), is_skipped(), main(), needs_extraction(), Namespace (+11 more)

### Community 11 - "Wiki Lint Checks"
Cohesion: 0.23
Nodes (17): _iter_pages(), lint_vault(), _parse_frontmatter_values(), _parse_page(), Any, Path, Vault lint checks for wiki structure and metadata hygiene., _slug() (+9 more)

### Community 12 - "Manifest Delta Tests"
Cohesion: 0.18
Nodes (4): ManifestDeltaRelativeKeyTest, ManifestNormalizeRelativeKeyTest, cmd_delta must recognize sources stored under relative keys.      Real vaults ke, cmd_normalize must not corrupt relative source keys.      canonical() resolves a

### Community 13 - "Extension Background Script"
Cohesion: 0.17
Nodes (10): buildMarkdown(), escapeYaml(), extractPage(), extractPageFromTab(), flashBadge(), getUniqueFileHandle(), loadRawHandle(), openDb() (+2 more)

### Community 14 - "Manifest CLI"
Cohesion: 0.24
Nodes (15): canonical(), cmd_delta(), cmd_normalize(), load_manifest(), main(), manifest_path(), _match_relative(), _newest() (+7 more)

### Community 15 - "Benchmark Aggregation"
Cohesion: 0.23
Nodes (12): aggregate_results(), calculate_stats(), generate_benchmark(), generate_markdown(), load_run_results(), main(), Path, Aggregate run results into summary statistics.      Returns run_summary with sta (+4 more)

### Community 16 - "Wiki Skills Reference Pages"
Cohesion: 0.18
Nodes (12): Daily Update Skill, Graph Colorize Skill, Hermes Data Format Reference, Hermes History Ingest Skill, Implementation Validator Skill, Karpathy's LLM Wiki Pattern, LLM Wiki Skill, Memory Bridge Skill (+4 more)

### Community 17 - "Doctor CLI Tests"
Cohesion: 0.48
Nodes (11): _install_all_skills(), _make_vault(), CompletedProcess, Path, Tests for the doctor CLI command., _run(), test_doctor_fails_on_invalid_manifest(), test_doctor_json_clean_install() (+3 more)

### Community 19 - "Wiki Ops Skills"
Cohesion: 0.20
Nodes (11): Config Resolution Protocol, Staged Writes, Wiki Insights, Wiki Research Skill, Wiki Setup Skill, Wiki Stage Commit Skill, Wiki Status Skill, Wiki Switch Skill (+3 more)

### Community 20 - "Wiki Skill Definitions A"
Cohesion: 0.20
Nodes (10): QMD Search Index, Vault Skill Factory, Wiki Agent, Wiki Capture, Wiki Context Pack, Wiki History Ingest, Wiki Ingest, Wiki Lint (+2 more)

### Community 21 - "Skill Packaging"
Cohesion: 0.29
Nodes (8): main(), package_skill(), Path, Check if a path should be excluded from packaging., Package a skill folder into a .skill file.      Args:         skill_path: Path t, should_exclude(), Basic validation of a skill, validate_skill()

### Community 23 - "OKF Link Roundtrip Tests"
Cohesion: 0.28
Nodes (5): export_okf_link_path(), import_okf_link_target(), OkfSameNameLinkRoundTripTest, Model wiki-import Step 4-OKF's .md path -> page id reversal., Model wiki-export Step 3.5's required target-file relpath behavior.

### Community 24 - "Agent Context Files"
Cohesion: 0.25
Nodes (8): Antigravity Rules, Antigravity Workflows, Copilot Instructions, Kiro Steering Rules, Obsidian Wiki Agent Context, Claude Agent Context, Gemini Agent Context, Hermes Agent Context

### Community 25 - "Query CLI Tests"
Cohesion: 0.46
Nodes (7): _page(), CompletedProcess, Path, Tests for the high-level query CLI., _run(), test_query_cli_requires_vault_when_unconfigured(), test_query_cli_uses_configured_vault()

### Community 27 - "Brain Vault Capture Assets"
Cohesion: 0.67
Nodes (3): Obsidian Brain Logo, Brain Vault Capture Popup, Brain Vault Capture README

## Knowledge Gaps
- **73 isolated node(s):** `wiki-stop-capture.sh script`, `manifest_version`, `name`, `description`, `version` (+68 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **22 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `analyse_vault()` connect `Graph Analysis Engine` to `CLI Command Layer`?**
  _High betweenness centrality (0.089) - this node is a cross-community bridge._
- **Why does `query()` connect `GraphRAG Query System` to `CLI Command Layer`?**
  _High betweenness centrality (0.083) - this node is a cross-community bridge._
- **Why does `extract()` connect `AST Extraction` to `CLI Command Layer`?**
  _High betweenness centrality (0.066) - this node is a cross-community bridge._
- **What connects `wiki-stop-capture.sh script`, `manifest_version`, `name` to the rest of the system?**
  _73 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Graph Analysis Engine` be split into smaller, more focused modules?**
  _Cohesion score 0.060153776571687016 - nodes in this community are weakly interconnected._
- **Should `GraphRAG Query System` be split into smaller, more focused modules?**
  _Cohesion score 0.06612021857923497 - nodes in this community are weakly interconnected._
- **Should `Ingest Cache/Staleness` be split into smaller, more focused modules?**
  _Cohesion score 0.08350168350168351 - nodes in this community are weakly interconnected._