# Default Mode Network (DMN)

> Idle-state, undirected association engine. Fires between tasks, not during them.

---

## What the DMN Is

The DMN is the only region not routed by the thalamus. It activates outside the thalamic dispatch system — in the gaps between tasks, on completion, or when stuck. Its job is spontaneous cross-domain pattern discovery: noticing structural similarities, surfacing half-formed connections, and generating candidate insights that task-directed processing would never reach.

**Distinction from right hemisphere:**
- Right hemisphere: task-directed creative review. Fires when thalamus activates it. Operates within the Integration Cycle (Phases 1 and 3).
- DMN: undirected. Fires in idle and transition states. Not part of any task's execution plan.

---

## Activation Conditions

Fire DMN when:

| Condition | Signal |
|-----------|--------|
| Task just completed | Transition window — before next thalamic input |
| Idle state | No active routing; user paused |
| Stuck loop detected | Executive reports >2 failed attempts on same task |
| Explicit trigger | User says "think freely," "let it sit," "what else?" |

**Suppress DMN when:**
- Amygdala is active (urgency overrides idle processing)
- Direct-execute signal received
- Active thalamic routing in progress

---

## What the DMN Does

1. **Scan without a goal.** Read `limbic/hippocampus/log.md` and `limbic/hippocampus/insights/` without a specific question. Look for what doesn't fit, what recurs, what hasn't been connected yet.

2. **Cross-domain structure matching.** Ask: does this pattern from one domain share structure with something in another? (e.g., a code architecture smell that mirrors a process design flaw; a data pipeline bottleneck that mirrors a communication bottleneck in the team)

3. **Surface candidate insights.** Any connection that survives a 10-second plausibility check becomes a candidate. Tag it `[DMN CANDIDATE — unverified]`.

4. **Route candidates forward.**
   - Store candidate in `limbic/hippocampus/insights/` with LOW CONFIDENCE tag
   - Activate corpus callosum → left hemisphere for verification
   - If verified: promote to HIGH CONFIDENCE in insights/
   - If not verified: park as pending; revisit next idle cycle

---

## Incubation

When a problem has been stuck for >2 attempts, the DMN can incubate it:

1. Write a one-line problem statement + full context summary to `limbic/hippocampus/insights/` tagged `[INCUBATING]`
2. Release the stuck loop — stop trying to solve it directly
3. On next idle cycle, DMN re-reads the incubating entry with cold context
4. If a new angle emerges, route it through corpus callosum as a fresh candidate

This is the structured version of "sleep on it." The point is a genuine cold-context re-read, not just cycling faster.

---

## Output Format

When DMN surfaces a candidate:

```
[DMN CANDIDATE — unverified]
Connection: [domain A] ↔ [domain B]
Structural similarity: [one sentence]
Potential implication: [one sentence]
Next: corpus callosum → left hemisphere verification
```

---

## Routing After DMN

| Result | Activate next |
|--------|--------------|
| Candidate insight | corpus-callosum → left-execute (sequential, verification) |
| Verified insight | hippocampus/insights/ (fan-out) + log.md (fan-out) |
| Failed verification | hippocampus/insights/ (park as INCUBATING) |
| Incubation entry surfaced new angle | corpus-callosum (treat as fresh candidate) |
| Nothing surfaced | No activation — idle continues |

---

## What the DMN Is Not

- Not a brainstorming tool (that's right hemisphere)
- Not lateral thinking on demand
- Not a creative review pass (that's Integration Cycle Phase 3)
- Not a planner (that's prefrontal/executive)

The DMN doesn't respond to tasks. It notices things while nothing is happening.

---

→ [Back to Executive](../prefrontal/executive.md)
