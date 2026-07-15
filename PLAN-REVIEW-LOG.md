# Plan Review Log: Promotion graphify-enrich → vault via wiki-ingest
Act 1 (grill-with-docs) complete — plan locked, CONTEXT.md created (no ADRs needed). MAX_ROUNDS=5.

## Round 1 — Codex (thread 019f6372-70dd-79a0-9609-60378833bca9, VERDICT: REVISE, 36 findings)

1. **Branch ancestry is contradictory:** Step 1 commits taxonomy to `main`, but Step 2 creates the test branch from the old commit `12fc3d5`, potentially omitting that prerequisite.  
Fix: Pin the post-taxonomy commit SHA and create every candidate branch from exactly that SHA.

2. **Branch names are inconsistent:** the approach uses `test/wiki-ingest-promotion`, while key decisions name `feature/vault-promotion-wiki-ingest`; automation and review may target different branches.  
Fix: Define one canonical vault branch name and use it everywhere.

3. **`tag-taxonomy` cannot bootstrap the missing taxonomy as written:** its precondition is to read an existing `_meta/taxonomy.md`, and adding unknown tags requires user agreement.  
Fix: Add an explicit taxonomy-bootstrap specification and human approval gate before committing it.

4. **Committing taxonomy directly to `main` mutates the control candidate before comparison:** the alleged baseline is no longer the original baseline commit.  
Fix: Create a shared base branch/commit and compare both candidates against the untouched baseline SHA.

5. **The trivia filter is not implementable from the stated schema:** enrichment frontmatter has `node`, `community`, `source_file`, and provenance, but no `kind` or trivia field.  
Fix: Define a deterministic predicate using available fields plus graph metadata, with golden expected inclusions/exclusions.

6. **Community is not a reliable trivia discriminator:** `Namespace` and `Path` references share legitimate communities with architectural nodes.  
Fix: Classify trivia from node kind/degree/source ownership in the graph artifact, not community labels.

7. **The source set is not frozen:** “100 less tests/trivia” can change between planning and execution or differ by checkout.  
Fix: Record the staging commit SHA, sorted eligible paths, exclusions with reasons, and aggregate hashes before ingest.

8. **The page-count assumptions conflict:** CONTEXT says 10–15 pages per community, the skill says 10–15 pages per ingest, and QA caps the entire result at 20 despite 22 communities.  
Fix: Choose one explicit global page budget and minimum community-coverage requirement.

9. **Large-folder behavior creates race conditions:** `wiki-ingest` mandates parallel subagents for over 20 files, while each may concurrently edit `.manifest.json`, `index.md`, `log.md`, `hot.md`, and shared pages.  
Fix: Partition content generation into isolated worktrees/staging outputs and serialize all merges and special-file updates.

10. **Parallel batches undermine cross-source distillation:** independently processed batches cannot reliably consolidate concepts spanning batches and may create duplicate pages.  
Fix: Cluster all eligible notes by community/topic before dispatch, then perform a deterministic global deduplication merge.

11. **The comparison folder is unsupported:** `wiki-ingest` requires category/project placement and integration with existing pages; `projects/obsidian-wiki-v2/ or equivalent` is neither deterministic nor sanctioned by the skill.  
Fix: Use `WIKI_STAGED_WRITES=true` or an isolated cloned vault/worktree rather than inventing a comparison namespace.

12. **“Côte à côte” contaminates the experiment:** duplicate baseline and candidate pages alter link resolution, orphan counts, cross-linking, index entries, and human graph appearance.  
Fix: Compare separate worktrees or vault copies opened independently in Obsidian.

13. **The ingest may modify baseline pages:** the skill explicitly merges into existing pages when concepts already exist, contradicting preservation of the manual baseline.  
Fix: Run against an isolated baseline copy and define an allowlist of writable candidate paths plus special files.

14. **Full mode does not provide idempotence:** rerunning corrections can reprocess all sources, rewrite summaries, duplicate log entries, and churn inferred content.  
Fix: Require a clean worktree reset to the pinned base before every candidate run and compare repeated-run hashes.

15. **QA lacks source coverage:** valid frontmatter and ≤20 pages do not prove every eligible note contributed knowledge.  
Fix: Assert every eligible source has a manifest entry and appears in at least one produced or updated page’s provenance.

16. **Manifest correctness is not gated:** per-source hashes, created/updated page lists, aggregate stats, and stale references can be wrong while the proposed QA passes.  
Fix: Validate manifest schema, hashes, page existence, source coverage, and recomputed statistics.

17. **The QA scope is ambiguous:** “pages produced” does not say whether updated baseline pages, project overview, staged patches, index, or cross-linker modifications count.  
Fix: Derive the candidate file set from the git diff and classify every changed path explicitly.

18. **Required schema validation is incomplete:** the skill also requires `base_confidence`, `lifecycle_changed`, `tier`, and `provenance`, but gate 1 omits them.  
Fix: Validate the complete new-page and updated-page schemas separately, including numeric ranges and provenance sums.

19. **Tag validation is underspecified:** reserved `visibility/*` tags are intentionally outside the taxonomy and would be falsely rejected by “0 tag hors vocabulaire.”  
Fix: Validate canonical domain/type/project tags separately from reserved system tags and enforce the five-tag rule.

20. **`lint_vault()` is treated as stronger than documented:** zero broken links/orphans does not validate duplicate slugs, ambiguous short links, YAML correctness, or semantic link targets.  
Fix: Add deterministic checks for YAML parsing, duplicate filenames/slugs, ambiguous links, relationship targets/types, and index consistency.

21. **The zero-orphan gate may measure the wrong universe:** special files, baseline pages, staged files, or pages excluded by the linter can make the count meaningless.  
Fix: State the exact scan/exclusion rules and independently recompute candidate in/out-degree.

22. **The semantic auditor lacks authoritative evidence:** it is asked to compare inferred claims with source code, but the plan only guarantees access to enrichment notes and does not pin the source-code revision.  
Fix: Supply the exact framework commit and map every `source_file` reference to that immutable checkout.

23. **Empty `source_file` values are unhandled:** at least five enrichment notes have no source file, so code verification cannot be performed uniformly.  
Fix: Exclude them with recorded justification or define alternate authoritative evidence and mark unverifiable claims ambiguous.

24. **The auditor’s mandate is narrower than the ingest output:** checking only `^[inferred]` against code misses omissions, distorted extracted claims, cross-source synthesis, and unsupported relationship types.  
Fix: Audit claim support, completeness, provenance class, relationships, contradictions, and source-to-page traceability.

25. **“Independent” is not operationally guaranteed:** a fresh session does not prove it uses a different model/context or has not inherited generated artifacts as assumptions.  
Fix: Record auditor identity/model, prompt, input set, commit SHA, and machine-readable findings artifact.

26. **Correction ownership is undefined:** the read-only auditor cannot correct files, and the plan does not identify who applies findings or how provenance is preserved.  
Fix: Assign a separate writer and require each correction commit to reference finding IDs.

27. **The correction policy is inconsistent:** gate 1 allows one correction round, while gate 2 permits corrections without a round limit or mandatory re-audit.  
Fix: Define bounded correction rounds and rerun both deterministic QA and an independent semantic audit after every correction.

28. **`cross-linker` runs after both gates and invalidates them:** it edits bodies and relationship frontmatter, adding inferred assertions that were neither linted nor semantically audited.  
Fix: Run cross-linker before the final deterministic and semantic gates, then forbid subsequent content changes.

29. **Cross-linker can modify the baseline:** its documented scope is the complete vault, so the comparison reference will not remain intact.  
Fix: Restrict it to candidate pages plus explicitly approved reciprocal edits, or run it only in the isolated candidate vault.

30. **Cross-linker’s fuzzy matching is risky for this domain:** generic names such as `Path`, `run`, `main`, and `query` can produce confident but wrong links.  
Fix: Add a domain stoplist and require path-qualified targets or manual approval for colliding titles and aliases.

31. **The human gate has no reproducible comparison artifact:** opening one checkout in Obsidian provides no stable diff, scoring rubric, or record of the decision.  
Fix: Generate side-by-side inventories, rendered summaries, metrics, git diffs, and a signed decision record.

32. **Lifecycle promotion is omitted:** CONTEXT reserves `draft → reviewed` for the human, but Step 8 only describes merging the winner.  
Fix: Make lifecycle promotion an explicit post-approval commit limited to approved candidate pages.

33. **Rollback and dirty-worktree handling are absent:** branch checkout or failure can collide with local vault edits and leave partially updated special files.  
Fix: Require a clean status check, backup/worktree isolation, atomic commits per phase, and documented rollback SHAs.

34. **Observability is inadequate:** only a cross-link log entry is specified; no run ID ties filtering, ingest, QA, audit, correction, and human decision together.  
Fix: Introduce a run ID and persist commands, SHAs, source hashes, counts, findings, and gate results in one artifact.

35. **QMD side effects are ignored:** all three skills may refresh a shared external index, contaminating search results across candidate branches even though markdown branches are isolated.  
Fix: Disable QMD during experiments or assign branch-specific collections and verify cleanup.

36. **The simpler sanctioned alternative is missed:** staged writes already provide review isolation without duplicate live pages or arbitrary folders.  
Fix: Run `wiki-ingest` with staged writes in an isolated vault worktree, review, then promote through the staging mechanism.

VERDICT: REVISE

### Claude's response (round 1)

Accepted (structural): #28 cross-linker moved BEFORE gates; #11/#12/#13/#36 side-by-side replaced by isolated git worktree of the vault repo + WIKI_STAGED_WRITES + wiki-stage-commit (sanctioned staging mechanism), human comparison = two separate vaults in Obsidian; #9/#10 parallel subagents disabled — sequential by community; #4/#1 taxonomy commit becomes BASE_SHA, both candidates and the baseline comparison point pin to it; #2 canonical naming section added (framework branch vs vault branch vs worktree).
Accepted (spec): #5/#6/#23 trivia predicate from graph.json kind/degree (not community, not frontmatter), 5 empty-source_file notes excluded with logged justification, golden list before run; #7 frozen source set (sorted list + aggregate sha256 + staging hash); #8 global page budget ≤20, CONTEXT.md corrected; #15/#16/#17/#18/#19/#20/#21 gate 1 expanded (git-diff scope, full schema incl. tier/lifecycle_changed/base_confidence/provenance sums, visibility/* validated separately, slug uniqueness, ambiguous links, manifest validation, explicit orphan scan rules); #22/#24/#25/#26/#27 gate 2 expanded (pinned framework SHA as evidence, broader mandate, auditor identity+prompt+inputs logged, machine-readable findings, Claude writes corrections referencing finding IDs, MAX 2 rounds with re-run of both gates); #29/#30 cross-linker bounded to worktree + domain stoplist; #32 lifecycle draft→reviewed as separate post-approval commit; #33 clean-status precondition + rollback SHAs; #35 QMD verified unset (auto-skip).
Tempered (logged as arbiter): #31 decision recorded in run report, no signature apparatus; #34 one markdown run report as the single observability artifact, no dedicated infrastructure.
PLAN.md rewritten as v2. Re-submitting to same session.

## Round 2 — Codex (same thread, VERDICT: REVISE, 25 findings)

1. **Prior #5/#6 remains unresolved:** `graph.json` has no top-level `kind` or `degree`; kind is under `metadata.kind`, and degree must be computed from links.  
Fix: Specify the exact JSON paths, degree algorithm, thresholds, and golden cases in the plan—not during execution.

2. **Prior #7 is only partially fixed:** “hash du staging” is undefined for a directory and may vary with ordering or metadata.  
Fix: Define it as SHA-256 over sorted `relative-path + NUL + file-content-hash` records.

3. **Prior #9 conflicts with the skill contract:** `wiki-ingest` Step 0 mandates batch planning and parallel subagents for directories over 20 files; the plan silently overrides it.  
Fix: Explicitly document the sanctioned deviation or pass pre-grouped batches as separate ≤20-file invocations.

4. **Vault targeting is not operationalized:** the framework `.env` resolves `OBSIDIAN_VAULT_PATH` to the baseline, so merely saying “cible = worktree candidat” does not redirect either skill.  
Fix: Create an explicit candidate config/profile or candidate-local `.env`, verify the resolved path before every write skill, and log it.

5. **`WIKI_STAGED_WRITES=true` is not operationalized:** it is absent from the current `.env`, while `wiki-stage-commit` refuses to run unless config resolution returns it.  
Fix: Define where the candidate-specific setting is persisted and assert both resolved variables before ingest and stage commit.

6. **The source-code evidence is not necessarily aligned with graphify output:** pinning framework HEAD does not prove `graph.json` and enrichments were generated from that commit.  
Fix: Require `graph.json.built_at_commit == pinned framework SHA` or pin and audit against the recorded graph commit.

7. **The trivia predicate may exclude architectural nodes merely for low degree:** CONTEXT defines trivia semantically as constants/imports/type refs, not all low-degree nodes.  
Fix: Make eligible kinds primary and degree only a tie-breaker, with explicit preservation cases for low-degree files/functions.

8. **Excluding all five empty-`source_file` notes is overbroad:** some are standard-library references, but exclusion may also discard useful synthesized knowledge without examining their identities.  
Fix: Enumerate the five files and justify each exclusion individually in the frozen run report.

9. **Community-by-community ingestion can still defeat global distillation:** sequential awareness does not guarantee later communities merge overlapping pages or avoid the 20-page cap.  
Fix: Produce one global page plan across all communities before any staged page is written.

10. **The page budget has no lower bound or coverage distribution:** one page could technically pass while flattening all communities.  
Fix: Add minimum coverage criteria for each retained community and a reasonable global page-count range.

11. **“Manifest AND page provenance” is schema-ambiguous:** page `provenance` stores fractions, not source identities; source identities live in `sources`.  
Fix: Require each eligible canonical source path in the manifest and in at least one page’s `sources`, with reciprocal manifest page mapping.

12. **Staged-write bookkeeping is internally hazardous:** `wiki-ingest` updates `index.md` immediately for staged pages, while `wiki-stage-commit` updates it again upon acceptance.  
Fix: Add a reconciliation step that rebuilds and deduplicates `index.md` from accepted live pages after stage commit.

13. **Rejected or skipped staged files are unhandled:** Step 5 says “promotion” but does not require an empty staging queue or account for rejected files in source coverage.  
Fix: Require zero skipped/rejected files, or recalculate eligibility, manifest, index, and coverage after documented rejection.

14. **Stage review authority is unclear:** `wiki-stage-commit` is explicitly interactive human approval, but the plan’s only human gate occurs later.  
Fix: State who accepts each staged file and distinguish this content-safety approval from the final candidate-selection gate.

15. **The QA schema incorrectly treats new and updated pages identically:** `wiki-ingest` preserves lifecycle on updates and does not require backfilling every new-page field.  
Fix: Define separate exact schemas based on the skill’s new-page versus updated-page rules.

16. **Relationship validation from prior #20 is missing:** Gate 1 checks links but not allowed relationship types, direction format, duplicates, or target existence.  
Fix: Add deterministic validation of every `relationships[]` entry.

17. **Index and special-file consistency from prior #20 remains incomplete:** changed files are classified, but `index.md`, `log.md`, and `hot.md` correctness is not gated.  
Fix: Rebuild-check the index, validate parseable run-linked log entries, and verify hot-cache freshness after final content changes.

18. **The cross-linker is not actually scoped to candidate changes:** “borné au worktree” still means it scans and edits every baseline page inside that worktree.  
Fix: Define an edit allowlist of candidate pages plus explicitly approved reciprocal baseline edits, and fail on any other modification.

19. **The stoplist does not prevent false semantic links:** cross-linker can add `related_to` links based only on shared tags or directory affinity.  
Fix: Disable affinity-only additions for this run or require manual approval for every INFERRED link.

20. **Audit omissions are impossible to assess without expected coverage:** “omissions” against dozens of source files has no defined required-claim set.  
Fix: Generate a source-to-claims inventory before audit and require the auditor to classify every retained source.

21. **Machine-readable findings lack a schema and stable location:** later correction commits cannot reliably reference IDs otherwise.  
Fix: Define the JSON/JSONL schema, repository path, unique ID format, and allowed verdict states.

22. **Content is not truly frozen after validation:** lifecycle promotion edits frontmatter after both gates.  
Fix: Either exempt and mechanically validate that exact transition or rerun deterministic QA after the lifecycle commit.

23. **Merge behavior is unspecified:** merging the candidate branch may include experimental logs, rejected raw files, staging debris, and run-specific configuration.  
Fix: Define the exact merge allowlist and require `_staging/`, rejected `_raw/`, temporary config, and audit artifacts to be absent or intentionally retained.

24. **QMD verification is too weak:** checking only the framework `.env` misses candidate-local, global, or inline config values used by Config Resolution Protocol.  
Fix: Log the fully resolved candidate configuration’s relevant variables before each skill invocation.

25. **Preflight currently cannot pass:** the framework worktree already contains untracked plan/context files and another unrelated untracked path.  
Fix: Define whether planned documentation files are committed first and stop specifically on unrelated dirt rather than requiring an impossible blanket-clean state.

VERDICT: REVISE

### Claude's response (round 2)

Accepted with data verification: #1 metadata.kind is absent on 666/677 nodes in the actual graph.json — the "kinds primary" fix is NOT implementable; predicate redefined on real data: tests by filename + empty source_file (stdlib type-refs), degree dropped entirely (would exclude legitimate low-degree architectural nodes). #8 the 5 empty-source_file notes enumerated and individually justified in the plan (4 non-test: Path×3, Namespace×1); eligible set = 67 notes, frozen.
Accepted: #2 staging hash defined (SHA-256 over sorted relpath\0content-hash records); #3 Step 0 deviation documented with the skill's own pre-partitioned wording; #4/#5/#24 candidate-local .env at worktree root + CWD=worktree + resolved-config logging before every write skill + stop on wrong resolution (real blocker, thanks); #6 EVIDENCE_SHA = graph.json built_at_commit (2cc6426, verified present) with dedicated read-only checkout; #9/#10 global page plan before any write, budget 8–20, ≥1 page per retained community; #11 coverage = manifest entry + sources: presence + reciprocal mapping; #12 index reconciliation after stage-commit; #13 empty _staging/ required, rejections documented + recomputed; #14 stage review = Claude content-safety review, human gate stays final (documented adaptation); #15 separate new/updated schemas; #16 relationships[] validation; #17 index rebuild-check + run-tagged log entries + hot freshness; #18 cross-linker edit allowlist + fail on out-of-list modification; #20 source-to-claims inventory before audit; #21 findings JSONL schema + path audit/findings-<RUN_ID>.jsonl; #22 lifecycle commit validated mechanically (diff touches only the 3 fields); #23 merge allowlist defined; #25 preflight = commit plan docs first, stop only on unacknowledged dirt (stray file acknowledged).
Tempered: #19 instead of manual approval per INFERRED link, INFERRED/affinity-only additions are disabled entirely this run (stricter and simpler); EXTRACTED only.
PLAN.md rewritten as v3. Re-submitting to same session.

## Round 3 — Codex (same thread, VERDICT: REVISE, 12 findings)

1. **The frozen hashes are contradictory:** the eligible 67-file set and the complete 100-file staging cannot have “ce même hash.”  
Fix: Record two separately named hashes using the same algorithm: `ELIGIBLE_HASH` and `STAGING_HASH`.

2. **EVIDENCE_SHA comparison is underspecified:** `graph.json` stores the full SHA, while the plan defines the abbreviated `2cc6426`; literal equality fails.  
Fix: Resolve `2cc6426^{commit}` to the full SHA and compare full commit IDs.

3. **Gate 1 lost its acceptance thresholds:** v3 invokes `lint_vault()` and degree recomputation but no longer explicitly requires zero broken links and zero candidate orphans.  
Fix: Restore explicit pass/fail thresholds for every lint and graph metric.

4. **The “source→claims inventory” is only source→pages:** listing pages from `sources:` does not identify claims or demonstrate that each source’s substance survived distillation.  
Fix: Map each source to concrete page claim IDs/quotes and record an audited pass/fail disposition for every eligible source.

5. **The findings schema cannot represent the stated audit:** `wrong|overreach|stale` lacks omission, distortion, unsupported relation, ambiguous evidence, and per-source pass states.  
Fix: Expand the enum and add `source`, `claim_id`, `severity`, `verdict`, and nullable evidence fields.

6. **Finding IDs still have no defined uniqueness rule:** merely including `id` does not make correction references stable across re-audits.  
Fix: Define IDs such as `<RUN_ID>-R<round>-F<sequence>` and prohibit reuse.

7. **Cross-linker restrictions are not implementable through its documented workflow:** it has no allowlist, dry-run, or EXTRACTED-only option and writes links immediately.  
Fix: Require a preview phase that computes proposed edits, filters them deterministically, obtains approval for baseline edits, then applies only the approved patch set.

8. **“EXTRACTED” cross-linker links are not actually source-extracted:** that label is score-derived and can result from exact text plus tag/directory heuristics.  
Fix: For this run, accept only literal unlinked mentions with an unambiguous registry target and disable all score-only semantic connections.

9. **The trivia requirement is weakened rather than fulfilled:** the replacement correctly handles the four unverifiable stdlib nodes, but it does not prove that no source-backed constants/imports/type references remain among the 67 eligible notes.  
Fix: Add a deterministic audit listing eligible node titles/source files and assert that no remaining note matches the CONTEXT trivia definition.

10. **Rejected staging semantics remain unsafe:** recalculating eligibility after Claude rejects a page could silently redefine the frozen source set to make coverage pass.  
Fix: Keep eligibility immutable; a rejection must trigger replanning/reingestion or fail the candidate.

11. **The merge allowlist is descriptive, not enforced:** a normal branch merge includes every tracked branch change, regardless of the listed paths.  
Fix: Add a pre-merge `git diff --name-only BASE_SHA..candidate` allowlist assertion and abort on any unexpected path.

12. **Acknowledging unrelated dirt is insufficient isolation:** the existing stray framework path could still be accidentally included in commits or reports.  
Fix: Require it to remain untracked and explicitly excluded from every staged commit, or move it outside the repository before the run.

VERDICT: REVISE

### Claude's response (round 3)

All 12 accepted (cheap, precise spec fixes): #1 two named hashes ELIGIBLE_HASH/STAGING_HASH; #2 EVIDENCE_SHA resolved to full SHA via rev-parse, strict equality; #3 explicit thresholds restored (0 broken links, 0 candidate orphans, recount included); #4 inventory now source→pages+exact citing sentences, auditor renders per-source pass/fail disposition; #5 findings enum expanded (omission/distortion/unsupported_relation/ambiguous_evidence) + source/claim_id/severity/verdict/nullable evidence fields; #6 ID format <RUN_ID>-R<round>-F<seq>, never reused; #7 cross-linker split into preview (compute+filter, no writes) then apply (approved patch set only); #8 'EXTRACTED only' replaced by 'literal unlinked mention with unambiguous registry target, no score-only links'; #9 deterministic no-residual-trivia audit over the 67 (label+source_file vs CONTEXT trivia definition); #10 eligibility immutable — rejection triggers replan/reingest or candidate failure, never set recomputation; #11 pre-merge git diff --name-only allowlist assertion with abort; #12 stray file moved out of the repo before the run.
PLAN.md rewritten as v4. Re-submitting to same session (round 4 of MAX 5).

## Round 4 — Codex (same thread, VERDICT: REVISE, 7 findings)

1. **EVIDENCE_SHA contradiction remains:** Naming requires full-SHA equality, but preflight still says `built_at_commit == 2cc6426`.  
Fix: Make preflight compare against the resolved full `EVIDENCE_SHA` variable only.

2. **Residual-trivia detection is not deterministic:** “patterns stdlib et imports purs” provides no exact fields, regexes, or expected result set.  
Fix: Define the precise predicates and freeze the resulting eligible-node inventory before ingest.

3. **Source→claim mapping is not scriptable from current pages:** `sources:` is page-level, so exact sentences cannot be attributed to one source when a page combines several notes.  
Fix: Require claim-level source IDs during ingestion, or make the mapping an audited LLM artifact rather than calling it deterministic.

4. **Per-source pass dispositions have no storage schema:** the findings JSONL requires a failure `class`, so it cannot represent sources that pass.  
Fix: Define a separate per-source audit JSONL, or allow records with `verdict: pass` and nullable `class/page/quote`.

5. **Updated-page QA is too weak for the ingest contract:** `wiki-ingest` requires updated pages to retain/update `summary`, `sources`, `provenance`, and confidence when sources materially change, but v4 only checks lifecycle and timestamp.  
Fix: Validate required updated-page fields, provenance sums, source additions, summary freshness, and confidence recomputation conditions.

6. **Manifest reconciliation after staging is missing:** staged paths may remain in `pages_created/pages_updated` after files move to final locations.  
Fix: Explicitly rewrite manifest page paths after stage commit before running manifest QA.

7. **RUN_ID-linked logs are required but not produced by the skill templates:** standard `INGEST`, `STAGE_COMMIT`, and `CROSS_LINK` entries contain no RUN_ID.  
Fix: Specify a deterministic post-operation annotation or extend each emitted log entry with `run_id=<RUN_ID>`.

VERDICT: REVISE

### Claude's response (round 4)

All 7 accepted: #1 preflight now asserts against the resolved full EVIDENCE_SHA only; #2 residual-trivia predicates made exact (source_file exists at EVIDENCE_SHA + label ∉ frozen stdlib denylist, inventory frozen before ingest, 67/67 expected); #3 inventory split into a deterministic source→pages part and an auditor-produced claim-attribution artifact (no longer claimed deterministic); #4 per-source dispositions get their own JSONL (source-dispositions-<RUN_ID>.jsonl, verdict pass|fail + finding_ids); #5 updated-page QA extended to the ingest contract (summary coherence, sources additions, provenance sums, base_confidence recomputation condition); #6 manifest staged→final path rewrite before manifest QA; #7 run_id=<RUN_ID> suffix appended to each skill-emitted log entry as a deterministic post-operation annotation.
PLAN.md rewritten as v5. Re-submitting to same session (round 5 of MAX 5 — final round).

## Round 5 — Codex (same thread, VERDICT: APPROVED)

All seven round-4 blockers are adequately addressed. No new execution-blocking or gate-invalidating issue remains.

VERDICT: APPROVED

### Resolution
Converged in 5 rounds (36 → 25 → 12 → 7 → 0 findings). Plan locked as PLAN.md v5. Awaiting human sign-off before any implementation.
