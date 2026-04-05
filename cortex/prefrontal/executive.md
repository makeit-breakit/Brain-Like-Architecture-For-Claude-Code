---
name: brain-architecture
description: Meta-cognitive framework governing how Claude approaches complex tasks. Unified parallel+sequential activation, dual-hemisphere processing, pattern recognition, memory consolidation, and cleanup discipline. Entry point for all complex tasks. Domain-specific skills plug into this framework via the routing tables.
---

# Executive — Prefrontal Cortex

Meta-cognitive layer governing HOW to think, not WHAT to do. Read this before any complex task.

---

## Neural Architecture

```
Thalamus (input gate)
    ↓ activation weights
Executive (orchestrator) ←──────────────────┐
    ↓ fires regions above threshold          │
    ├── cortex/left/          (analytical)   │
    ├── cortex/right/         (creative)     │  ← task-directed
    ├── cortex/default-mode/  (DMN)          │  ← idle/undirected; not thalamus-routed
    ├── connections/          (bridges)      │
    ├── limbic/hippocampus/   (memory)       │
    ├── limbic/amygdala/      (urgent)       │
    └── automation/           (routines) ───→┘
```

**Memory layers:**
| Layer | File | Purpose | Written when |
|-------|------|---------|-------------|
| Short-term | `limbic/hippocampus/context-state.md` | Session buffer — overwritten each session | Session end; before compaction; after major task state change |
| Long-term episodic | `limbic/hippocampus/log.md` | Append-only chronological record | Task completes with significant output; insight filed; session end |
| Long-term semantic | `limbic/hippocampus/gotchas.md` | Lessons, anti-patterns, hard rules | Immediately on correction; after bug autopsy; when new anti-pattern emerges |
| High-conviction | `limbic/hippocampus/insights/` | Verified synthesis, validated decisions | After full verification; entry also appended to log.md |

---

## Unified Routing Model

Activation is **parallel by default, sequential when dependent, with fan-out when needed**.

1. **Thalamus** (dispatch subagent) reads the input and session state, reasons about which regions to activate, and returns a structured dispatch block
2. **Executive** fires all regions in the dispatch; follows the execution mode specified for each
3. **Execution mode** per region:
   - **Parallel** — Independent regions that don't feed each other fire simultaneously
   - **Sequential** — When region A's output is input to region B, A runs first, then activates B directly
   - **Fan-out** — One region activates multiple downstream regions on completion (e.g., analysis-complete → verification + hippocampus logging)
4. **Any region** may, upon completion, directly activate one or more downstream regions rather than returning to executive — provided the dependency is explicit

Routing is reasoning-driven, not score-based. The dispatch subagent decides by matching input signals to region roles and adjusting for session context.

---

## Thalamic Dispatch Protocol

At the start of every complex task, invoke the dispatch subagent before doing any work:

**Skill:** `thalamus/dispatch-skill.md`
**Agent type:** `general-purpose`
**Input:** the user's task prompt

The dispatch subagent reads `context-state.md`, classifies the input, reasons about which regions to activate given the session state, and returns a structured `=== THALAMIC DISPATCH ===` block listing every activated region, every latent region (not activating and why), and the execution mode for each.

Follow the dispatch output exactly — do not re-derive routing independently.

**Skip dispatch for:** unambiguous single-signal tasks where intent is fully specified ("just run it," named entity with clear evaluation intent, one-word go). Execute directly.

The base priors and delta rules used by the dispatch subagent are in `thalamus/routing-rules.md` and `thalamus/dispatch-skill.md`.

---

## Routing Guide — Input

| Signal | Activate |
|--------|---------|
| Research / analysis / synthesis question | right-scope, left-execute, hippocampus |
| Named entity / subject under evaluation | domain-skill, left-execute, hippocampus |
| External lookup / database / pipeline | left-execute, hippocampus |
| Bug / error / broken / fails | left-execute, amygdala, hippocampus |
| Urgent / critical / ASAP / down | amygdala, left-execute |
| Design / architecture / concept | right-scope, left-execute, corpus-callosum |
| Refactor / clean / reorganize | falsificator, left-execute, right-scope |
| Plan / strategy / roadmap | prefrontal, right-scope, left-execute |
| Multiple domains at once | corpus-callosum, right-scope, left-execute |
| User frustrated or stuck | amygdala, prefrontal, right-scope |
| Unclear / ambiguous | prefrontal (ask one focused question) |
| "Just do it" / one-word go | left-execute only — suppress all scoping |
| "Think freely" / "let it sit" / idle | DMN — fires outside dispatch; do not route through thalamus |

*Add domain-specific rows here for your workflow (e.g., "Pull request review", "Named candidate for evaluation", "Document for summarization").*

## Routing Guide — Mid-Task

| Current state | Activate |
|---------------|---------|
| Analysis complete | right-scope (gap check), corpus-callosum, verification, falsificator |
| Pattern discovered | corpus-callosum, right-scope, hippocampus |
| Stuck / looping >2 attempts | DMN (incubation), prefrontal (reframe), hippocampus |
| Task done, output ready | verification, falsificator, hippocampus |
| Verification failed | left-execute (targeted fix), hippocampus |
| User corrects approach | hippocampus (mandatory, immediately), prefrontal (replan), right-scope |
| Novel cross-domain insight | right-scope, corpus-callosum, hippocampus, left-execute (verify) |
| Domain-specific finding | hippocampus, left-execute (evidence check), right-scope, corpus-callosum |

---

## Integration Cycle (Corpus Callosum)

Standard cycle for complex tasks. Phases can overlap; for simple tasks compress 1 and 3 into quick checks.

1. **Explore (right)** — Divergent thinking. Scope the space. What patterns exist? What's adjacent? What would be surprising?
2. **Structure (left)** — Execute the analytical workflow. Verify each step. Apply evidence tiers. Run the domain skill.
3. **Review (right)** — Challenge the left hemisphere's output. What's missing? What doesn't fit? What would a contrarian say? For major outputs, this step invokes an external challenge agent (define one for your domain) — before delivery, not after. Accept valid corrections in place. The user sees one coherent output.
4. **Deliver (left)** — Verification checklist. Cleanup. Clean output.

See `connections/corpus-callosum.md` for detailed integration patterns and co-activation clusters.

---

## Core Directives

1. **Verify before complete** — Run verification checklist before any delivery
2. **Context decay** — Re-read any file before editing after 10+ messages
3. **Log mistakes immediately** — Write to `limbic/hippocampus/gotchas.md` on correction; don't wait
4. **Cross-hemisphere always** — Complex tasks need both left AND right perspectives
5. **File insights** — High-conviction, verified synthesis → `limbic/hippocampus/insights/`; append to `log.md`
6. **Fragility-first verification** — Verify claims where being wrong changes the outcome most

---

## Anti-Patterns (Amygdala Alerts)

When detected, interrupt and redirect.

| Anti-pattern | Signal | Redirect |
|-------------|--------|----------|
| Left-only loop | Analytical → analytical without creative check; going in circles | Force right-hemisphere scan |
| Surface-level terminal answer | Generic label as final explanation (e.g., "race condition", "cache miss", "network issue") without resolving to the specific component, call site, or mechanism | Resolve to specificity: which function, module, service, data structure, line |
| Urgency + exploration | Crisis but brainstorming instead of acting | Amygdala override: action first |
| Pattern without verification | Intuition drives conclusion without analytical check | Left hemisphere: verify with evidence |
| Echo chamber | All sources agree; no contrarian angle sought | Run adversary |
| Scope creep | Adding beyond what was asked | Prefrontal check: does this serve the stated task? |
| Context amnesia | Editing a file from stale memory after >10 messages | Re-read the file. Always. |

---

## Dual Encoding Rule

For any significant output, both hemispheres contribute:
- **Left**: Structured analysis, evidence tiers, code, verification
- **Right**: Pattern connections, what's missing, intuition check, adversary challenge

---

## Quick Links

- 🧠 [Memory index](../../limbic/hippocampus/index.md)
  - [context-state.md](../../limbic/hippocampus/context-state.md) — Short-term session buffer
  - [log.md](../../limbic/hippocampus/log.md) — Long-term episodic log
  - [gotchas.md](../../limbic/hippocampus/gotchas.md) — Long-term semantic lessons
  - [insights/](../../limbic/hippocampus/insights/) — High-conviction filed knowledge
- 🌀 [Default Mode Network](../default-mode/dmn.md) — Idle-state insight; incubation queue
- ⚡ [Urgent (amygdala)](../../limbic/amygdala/urgent.md)
- 🔗 [Corpus callosum](../../connections/corpus-callosum.md) — Integration patterns, co-activation clusters
- 🔗 [Activation patterns](../../connections/activation-patterns.md) — High-frequency circuits
- 🤖 [Falsificator](../../automation/falsificator.md) — Cleanup discipline
- 🤖 [Mirror neurons](../../automation/mirror-neurons.md) — Pattern library
- 🤖 [Routines](../../automation/routines.md) — Session protocols
- 📥 [Dispatch skill](../../thalamus/dispatch-skill.md) — Invoke this to get the activation set for any task
- 📥 [Thalamus routing table](../../thalamus/routing-rules.md) — Base priors and context-delta rules (used by dispatch skill)
