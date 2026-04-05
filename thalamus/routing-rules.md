# Thalamic Routing Rules

> Input classification and region activation guide. The thalamus routes — the executive orchestrates.

## How This Works

The thalamus classifies incoming input and decides which regions to activate. This is reasoning-driven routing, not numerical weighting. The dispatch subagent reads the input, checks session state, and determines activation by reasoning — matching input signals to region roles, then adjusting for what just happened in the session.

The executive receives the dispatch and:
1. Fires all activated regions
2. Decides execution mode (parallel vs. sequential vs. fan-out)

---

## Input Classification → Region Activation

| If input contains… | Activate |
|--------------------|---------|
| "bug", "error", "broken", "fails" | left-execute, amygdala, hippocampus |
| "urgent", "critical", "ASAP", "down" | amygdala, left-execute |
| "design", "concept", "architecture" | right-scope, corpus-callosum, left-execute |
| "remember", "note", "gotcha", "lesson" | hippocampus |
| "refactor", "reorganize", "clean" | falsificator, left-execute, right-scope |
| "plan", "strategy", "roadmap" | prefrontal, right-scope, left-execute |
| "both perspectives", "analyze and create" | corpus-callosum, left-execute, right-scope |
| Research / analysis / synthesis | right-scope, left-execute, hippocampus |
| Named entity / subject for evaluation | domain-skill, left-execute, hippocampus |
| Default / unclear | prefrontal (ask one focused question) |

*Add domain-specific rows for your workflow.*

---

## Context-Adjustment Rules

Apply these when reasoning in Step 3 of dispatch-skill.md:

| Context signal | Adjustment |
|---------------|-----------|
| Region just succeeded on similar task | Strengthen — treat as a clear signal |
| Region just failed on this task type | Drop unless clearly required |
| User expressed frustration or is stuck | Drop right-scope and corpus-callosum unless task is explicitly creative |
| Active named entity in session context | Include hippocampus |
| Correction just received | Hippocampus is mandatory |
| "Just run it" / urgency | Left-execute only; suppress all scoping |
| User names a region or skill explicitly | Include it regardless |

---

## Return Navigation

→ [Back to Executive](../cortex/prefrontal/executive.md)
