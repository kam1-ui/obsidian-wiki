---
type: community
members: 6
---

# Batch Plan CLI Tests

**Members:** 6 nodes

## Members
- [[._run()]] - code - tests/test_batch.py
- [[.test_max_files_respected()]] - code - tests/test_batch.py
- [[.test_missing_source_dir_exits_nonzero()]] - code - tests/test_batch.py
- [[.test_outputs_json()]] - code - tests/test_batch.py
- [[.test_pretty_flag()]] - code - tests/test_batch.py
- [[TestBatchPlanCLI]] - code - tests/test_batch.py

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Batch_Plan_CLI_Tests
SORT file.name ASC
```

## Connections to other communities
- 1 edge to [[_COMMUNITY_Batch DiscoveryPlanning]]

## Top bridge nodes
- [[TestBatchPlanCLI]] - degree 6, connects to 1 community