# Falsificator — Cerebellar Cleanup

> Autonomous error detection and clutter removal. Runs unconsciously.

## Purpose

Like the cerebellum fine-tunes motor output, the falsificator scans and cleans workspace artifacts. Question everything: *"Does this need to exist?"*

## Trigger Conditions

Run when:
- End of session
- Context compaction imminent
- >10 files in thalamus/ or working directories
- >10 working files accumulated in working output directories
- Explicit: "falsify" or "clean up"

## Falsification Rules

| If... | Then... |
|-------|---------|
| File has `temp-`, `debug-`, `scratch-` prefix | **Delete** |
| Superseded by newer version | **Delete** |
| Content duplicated elsewhere | **Consolidate** |
| >7 days old and unreferenced | **Archive** or **Delete** |
| Empty (0 bytes) | **Delete** |
| Large (>1MB) and reproducible | **Compress** or **Delete** |

## Scan Targets

```
thalamus/           → Delete processed items, keep inbox.md clean
limbic/             → Archive old context-state versions
cortex/left/        → Remove build artifacts, drafts
cortex/right/       → Remove old concept drafts
connections/temp/   → Delete all (temp by definition)
```

## Process

1. **Inventory** — List all files with ages, sizes
2. **Classify** — Mark each: keep / consolidate / archive / delete
3. **Execute** — Perform deletions
4. **Memory Lint** — Run the checks below
5. **Report** — Update hippocampus/context-state.md, append to hippocampus/log.md

## Memory Lint (Step 4)

Check `limbic/hippocampus/` for:

| Check | Action |
|-------|--------|
| Entry in gotchas.md contradicted by newer gotchas entry | Remove the older one |
| Entry in gotchas.md contradicted by current executive.md directives | Flag + reconcile |
| Insight in insights/ not referenced by any log.md entry | Add log entry or delete insight |
| insights/ file with no verification note | Flag for review |
| log.md entries older than 90 days with no corresponding insight or gotcha | Can prune after confirming nothing actionable |
| index.md missing a file that exists in hippocampus/ | Add to index |
| File in hippocampus/ not linked from index.md | Add to index |
| gotchas.md Index section out of sync with actual entries | Rewrite Index — one line per lesson, format: **[Title]** — one-line summary |

## Before Delivery

Scan output for: unnecessary caveats, redundant sections, content that restates what the user already knows. Trim. Ask: "Does this sentence need to exist?"

## Output

```markdown
# Falsification Log — [Date]
- Scanned: [N] files
- Deleted: [N] files ([X] MB)
- Consolidated: [N] → [N] files
- Space reclaimed: [X] MB
```

## Return Navigation

→ [Back to Executive](../cortex/prefrontal/executive.md)
