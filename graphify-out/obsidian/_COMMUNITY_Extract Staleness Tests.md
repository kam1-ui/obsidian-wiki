---
type: community
members: 12
---

# Extract Staleness Tests

**Members:** 12 nodes

## Members
- [[._run()_2]] - code - tests/test_extract_staleness.py
- [[._set_mtimes()]] - code - tests/test_extract_staleness.py
- [[.setUp()]] - code - tests/test_extract_staleness.py
- [[.tearDown()]] - code - tests/test_extract_staleness.py
- [[.test_first_run_extracts()]] - code - tests/test_extract_staleness.py
- [[.test_missing_output_is_reextracted()]] - code - tests/test_extract_staleness.py
- [[.test_missing_output_reextracted_despite_since_gate()]] - code - tests/test_extract_staleness.py
- [[.test_output_newer_is_skipped()]] - code - tests/test_extract_staleness.py
- [[.test_source_newer_is_reextracted()]] - code - tests/test_extract_staleness.py
- [[ExtractStalenessTest]] - code - tests/test_extract_staleness.py
- [[The extractor must be idempotent based on output-file staleness.      Regression]] - rationale - tests/test_extract_staleness.py
- [[test_extract_staleness.py]] - code - tests/test_extract_staleness.py

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Extract_Staleness_Tests
SORT file.name ASC
```
