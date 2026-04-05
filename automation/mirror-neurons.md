# Mirror Neurons — Pattern Library

> When X happens, do Y. Recognized trigger → response patterns. When a pattern matches, execute it — don't reinvent.

---

## Active Patterns

### Research / Analysis Pattern
**Trigger:** Research question, paper, synthesis, or analysis request
**Response:** dispatch-skill (routing) → scoping (right hemisphere) → structured analytical workflow (left hemisphere) → adversarial review (Integration Cycle Phase 3) → verification checklist

### Evaluation Pattern
**Trigger:** Named entity or subject handed to you for evaluation (compound, candidate, PR, proposal, design)
**Response:** input validation → domain evaluation workflow → adversarial review → verification

### External Lookup Pattern
**Trigger:** Request requiring external database, API, or resource query
**Response:** input validation → query → parse results → left-execute (integrate findings) → hippocampus

### Debugging Pattern
**Trigger:** Bug report with error log
**Response:** Reproduce → Isolate → Fix → Verify → Log to `limbic/hippocampus/gotchas.md`

### Refactoring Pattern
**Trigger:** File >300 LOC, architectural smell, or explicit "refactor"
**Response:** Delete dead code first → Restructure → Verify → Commit separately

### Context Compaction Pattern
**Trigger:** >15 messages or context warning
**Response:** Update `limbic/hippocampus/context-state.md` → compact → Continue

### Dual-Hemisphere Pattern
**Trigger:** Complex task requiring both analysis and creativity
**Response:** Right: Explore, visualize → Left: Structure, implement → Corpus callosum: integrate → Verify

### Correction Received Pattern
**Trigger:** User corrects approach, says "no," redirects
**Response:** Log to `limbic/hippocampus/gotchas.md` immediately (extract rule + reason + how to apply) → Replan → Apply going forward

### Same Question Twice Pattern
**Trigger:** User asks something that was already answered
**Response:** Check if prior answer was unclear → hippocampus: store communication pattern → Restate more precisely

### Context Decay Pattern
**Trigger:** >10 messages since last file read, about to edit
**Response:** Re-read the file → Compact if approaching limits → Never edit from stale memory

---

## Adding New Patterns

When a workflow recurs ≥3 times:
1. Name the trigger precisely
2. Document the response sequence
3. Test on next occurrence
4. Refine and commit here

---

## Failed Patterns (Avoid)

- ~~Over-documentation~~ → Leads to ignored instructions (brevity = adherence)
- ~~Trailing summaries~~ → User reads the diff; skip recaps
- ~~Probabilistic routing without exit condition~~ → Agent loops indefinitely; always define termination

---

## Routing After Pattern Match

When a pattern fires, the matched region activates. If the pattern specifies a sequence, each step activates the next directly (sequential chaining). If steps are independent, they activate in parallel. Return to executive when the full pattern is complete.

→ [Back to Executive](../cortex/prefrontal/executive.md)
