---
type: community
members: 51
---

# Batch Discovery/Planning

**Members:** 51 nodes

## Members
- [[._files()]] - code - tests/test_batch.py
- [[.test_all_files_present_in_batches()]] - code - tests/test_batch.py
- [[.test_batch_kinds_tallied()]] - code - tests/test_batch.py
- [[.test_batch_total_bytes_correct()]] - code - tests/test_batch.py
- [[.test_empty_dir_gives_zero_batches()]] - code - tests/test_batch.py
- [[.test_empty_input()]] - code - tests/test_batch.py
- [[.test_excludes_code_by_default()]] - code - tests/test_batch.py
- [[.test_finds_markdown()]] - code - tests/test_batch.py
- [[.test_image()]] - code - tests/test_batch.py
- [[.test_includes_code_when_flag_set()]] - code - tests/test_batch.py
- [[.test_json_serialisable()]] - code - tests/test_batch.py
- [[.test_markdown()]] - code - tests/test_batch.py
- [[.test_no_cache_flag_includes_unchanged()]] - code - tests/test_batch.py
- [[.test_pdf()]] - code - tests/test_batch.py
- [[.test_python_code()]] - code - tests/test_batch.py
- [[.test_returns_required_keys()]] - code - tests/test_batch.py
- [[.test_returns_size()]] - code - tests/test_batch.py
- [[.test_single_batch_small()]] - code - tests/test_batch.py
- [[.test_single_file_single_batch()]] - code - tests/test_batch.py
- [[.test_skip_binary()]] - code - tests/test_batch.py
- [[.test_skip_lockfile()]] - code - tests/test_batch.py
- [[.test_skips_binary()]] - code - tests/test_batch.py
- [[.test_skips_hidden_dirs()]] - code - tests/test_batch.py
- [[.test_skips_node_modules()]] - code - tests/test_batch.py
- [[.test_skips_unchanged_after_cache_update()]] - code - tests/test_batch.py
- [[.test_splits_on_byte_limit()]] - code - tests/test_batch.py
- [[.test_splits_on_file_count()]] - code - tests/test_batch.py
- [[Any]] - code
- [[Batch planner for parallel wiki-ingest subagent dispatch.  When ingesting a larg]] - rationale - obsidian_wiki/batch.py
- [[Discover sources, filter unchanged, and split into batches.]] - rationale - obsidian_wiki/batch.py
- [[Path_8]] - code
- [[Path_14]] - code
- [[Remove files whose hash matches the manifest. Returns (to_ingest, skipped_count)]] - rationale - obsidian_wiki/batch.py
- [[Split files into batches respecting size and file-count limits.]] - rationale - obsidian_wiki/batch.py
- [[TestClassify]] - code - tests/test_batch.py
- [[TestDiscoverSources]] - code - tests/test_batch.py
- [[TestMakeBatches]] - code - tests/test_batch.py
- [[TestPlanBatches]] - code - tests/test_batch.py
- [[Tests for the batch planning module.]] - rationale - tests/test_batch.py
- [[Walk source_dir and return a list of ingestible file dicts.      Each dict {pat]] - rationale - obsidian_wiki/batch.py
- [[_classify()]] - code - obsidian_wiki/batch.py
- [[_file_size()]] - code - obsidian_wiki/batch.py
- [[_filter_unchanged()]] - code - obsidian_wiki/batch.py
- [[_make_batches()]] - code - obsidian_wiki/batch.py
- [[_write()]] - code - tests/test_batch.py
- [[batch.py]] - code - obsidian_wiki/batch.py
- [[discover_sources()]] - code - obsidian_wiki/batch.py
- [[plan_batches()]] - code - obsidian_wiki/batch.py
- [[source_dir()]] - code - tests/test_batch.py
- [[test_batch.py]] - code - tests/test_batch.py
- [[vault()]] - code - tests/test_batch.py

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Batch_Discovery/Planning
SORT file.name ASC
```

## Connections to other communities
- 6 edges to [[_COMMUNITY_Ingest CacheStaleness]]
- 2 edges to [[_COMMUNITY_CLI Command Layer]]
- 1 edge to [[_COMMUNITY_Batch Plan CLI Tests]]

## Top bridge nodes
- [[test_batch.py]] - degree 15, connects to 2 communities
- [[plan_batches()]] - degree 18, connects to 1 community
- [[batch.py]] - degree 10, connects to 1 community
- [[_filter_unchanged()]] - degree 5, connects to 1 community
- [[.test_skips_unchanged_after_cache_update()]] - degree 4, connects to 1 community