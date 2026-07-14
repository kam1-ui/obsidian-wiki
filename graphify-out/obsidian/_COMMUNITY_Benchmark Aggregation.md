---
type: community
members: 13
---

# Benchmark Aggregation

**Members:** 13 nodes

## Members
- [[Aggregate run results into summary statistics.      Returns run_summary with sta]] - rationale - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[Calculate mean, stddev, min, max for a list of values.]] - rationale - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[Generate complete benchmark.json from run results.]] - rationale - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[Generate human-readable benchmark.md from benchmark data.]] - rationale - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[Load all run results from a benchmark directory.      Returns dict keyed by conf]] - rationale - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[Path_1]] - code
- [[aggregate_benchmark.py]] - code - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[aggregate_results()]] - code - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[calculate_stats()]] - code - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[generate_benchmark()]] - code - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[generate_markdown()]] - code - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[load_run_results()]] - code - .skills/skill-creator/scripts/aggregate_benchmark.py
- [[main()_1]] - code - .skills/skill-creator/scripts/aggregate_benchmark.py

## Live Query (requires Dataview plugin)

```dataview
TABLE source_file, type FROM #community/Benchmark_Aggregation
SORT file.name ASC
```
