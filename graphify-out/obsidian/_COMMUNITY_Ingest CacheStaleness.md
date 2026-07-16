---
type: community
members: 55
---

# Ingest Cache/Staleness

**Members:** 55 nodes

## Members
- [[._run()_1]] - code - tests/test_cache.py
- [[.test_cache_check_new()]] - code - tests/test_cache.py
- [[.test_cache_check_pretty()]] - code - tests/test_cache.py
- [[.test_cache_hash_file()]] - code - tests/test_cache.py
- [[.test_cache_hash_missing_exits_nonzero()]] - code - tests/test_cache.py
- [[.test_cache_update_then_check_unchanged()]] - code - tests/test_cache.py
- [[.test_cache_update_with_pages()]] - code - tests/test_cache.py
- [[.test_compute_hash_dispatches()]] - code - tests/test_cache.py
- [[.test_empty_source_list()]] - code - tests/test_cache.py
- [[.test_hash_file_alias()]] - code - tests/test_cache.py
- [[.test_missing_path()]] - code - tests/test_cache.py
- [[.test_modified_after_content_change()]] - code - tests/test_cache.py
- [[.test_multiple_sources()]] - code - tests/test_cache.py
- [[.test_new_source()]] - code - tests/test_cache.py
- [[.test_preserves_other_manifest_entries()]] - code - tests/test_cache.py
- [[.test_records_correct_hash()]] - code - tests/test_cache.py
- [[.test_records_last_ingested_timestamp()]] - code - tests/test_cache.py
- [[.test_records_pages_produced()]] - code - tests/test_cache.py
- [[.test_sha256_dir_changes_on_edit()]] - code - tests/test_cache.py
- [[.test_sha256_dir_deterministic()]] - code - tests/test_cache.py
- [[.test_sha256_file_changes_on_edit()]] - code - tests/test_cache.py
- [[.test_sha256_file_deterministic()]] - code - tests/test_cache.py
- [[.test_timestamp_irrelevant()]] - code - tests/test_cache.py
- [[.test_unchanged_after_update()]] - code - tests/test_cache.py
- [[.test_update_overwrites_old_hash()]] - code - tests/test_cache.py
- [[.test_writes_manifest()]] - code - tests/test_cache.py
- [[CheckResult]] - code - obsidian_wiki/cache.py
- [[Classify each source as new  modified  unchanged vs. the manifest.      Also r]] - rationale - obsidian_wiki/cache.py
- [[Content-hash cache for wiki-ingest source tracking.  Provides a reliable, platfo]] - rationale - obsidian_wiki/cache.py
- [[Just compute and return the hash — no manifest IO.]] - rationale - obsidian_wiki/cache.py
- [[Path_9]] - code
- [[Record the current hash of source_path in the manifest. Returns the hash.]] - rationale - obsidian_wiki/cache.py
- [[Return the hex SHA-256 digest of path without loading it all into RAM.]] - rationale - obsidian_wiki/cache.py
- [[SourceEntry]] - code - obsidian_wiki/cache.py
- [[Stable SHA-256 over all files in a directory tree (sorted by relative path).]] - rationale - obsidian_wiki/cache.py
- [[TestCacheCLI]] - code - tests/test_cache.py
- [[TestCheckSources]] - code - tests/test_cache.py
- [[TestHashing]] - code - tests/test_cache.py
- [[TestUpdateSource]] - code - tests/test_cache.py
- [[Tests for the content-hash cache module.]] - rationale - tests/test_cache.py
- [[TypedDict]] - code
- [[_load_manifest()]] - code - obsidian_wiki/cache.py
- [[_manifest_path()]] - code - obsidian_wiki/cache.py
- [[_save_manifest()]] - code - obsidian_wiki/cache.py
- [[cache.py]] - code - obsidian_wiki/cache.py
- [[check_sources()]] - code - obsidian_wiki/cache.py
- [[compute_hash()]] - code - obsidian_wiki/cache.py
- [[hash_file()]] - code - obsidian_wiki/cache.py
- [[sha256_dir()]] - code - obsidian_wiki/cache.py
- [[sha256_file()]] - code - obsidian_wiki/cache.py
- [[src_dir()]] - code - tests/test_cache.py
- [[src_file()]] - code - tests/test_cache.py
- [[test_cache.py]] - code - tests/test_cache.py
- [[update_source()]] - code - obsidian_wiki/cache.py
- [[vault()_1]] - code - tests/test_cache.py

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Ingest_Cache/Staleness
SORT file.name ASC
```

## Connections to other communities
- 6 edges to [[_COMMUNITY_Batch DiscoveryPlanning]]
- 6 edges to [[_COMMUNITY_CLI Command Layer]]

## Top bridge nodes
- [[update_source()]] - degree 22, connects to 2 communities
- [[check_sources()]] - degree 18, connects to 2 communities
- [[compute_hash()]] - degree 10, connects to 1 community
- [[hash_file()]] - degree 8, connects to 1 community