---
type: community
members: 19
---

# Manifest Delta Tests

**Members:** 19 nodes

## Members
- [[._delta()]] - code - tests/test_manifest_delta.py
- [[._keys_after_normalize()]] - code - tests/test_manifest_delta.py
- [[._write_manifest()]] - code - tests/test_manifest_delta.py
- [[._write_manifest()_1]] - code - tests/test_manifest_delta.py
- [[.setUp()_1]] - code - tests/test_manifest_delta.py
- [[.setUp()_2]] - code - tests/test_manifest_delta.py
- [[.tearDown()_1]] - code - tests/test_manifest_delta.py
- [[.tearDown()_2]] - code - tests/test_manifest_delta.py
- [[.test_absolute_key_still_matches()]] - code - tests/test_manifest_delta.py
- [[.test_absolute_keys_still_dedup_and_canonicalize()]] - code - tests/test_manifest_delta.py
- [[.test_relative_key_older_ingest_is_modified_not_new()]] - code - tests/test_manifest_delta.py
- [[.test_relative_key_preserved_regardless_of_cwd()]] - code - tests/test_manifest_delta.py
- [[.test_relative_key_recent_ingest_is_unchanged()]] - code - tests/test_manifest_delta.py
- [[.test_unknown_file_is_new()]] - code - tests/test_manifest_delta.py
- [[ManifestDeltaRelativeKeyTest]] - code - tests/test_manifest_delta.py
- [[ManifestNormalizeRelativeKeyTest]] - code - tests/test_manifest_delta.py
- [[cmd_delta must recognize sources stored under relative keys.      Real vaults ke]] - rationale - tests/test_manifest_delta.py
- [[cmd_normalize must not corrupt relative source keys.      canonical() resolves a]] - rationale - tests/test_manifest_delta.py
- [[test_manifest_delta.py]] - code - tests/test_manifest_delta.py

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Manifest_Delta_Tests
SORT file.name ASC
```
