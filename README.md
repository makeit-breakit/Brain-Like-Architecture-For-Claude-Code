# Brain — Network Architecture

A workspace organized like a brain, not a hierarchy.

## Structure

```
                    [thalamus/]           ← Input gateway
                         ↓
              ┌─────────────────────┐
              │   cortex/prefrontal/ │ ← executive.md — Executive
              │     (executive.md)   │    Planning, decisions
              └─────────────────────┘
                         │
         ┌───────────────┼───────────────┐
         ↓               ↓               ↓
  [cortex/left/]   [connections/]   [cortex/right/]
   Analytical        Bridges        Creative (task-directed)
   Logic, code     Corpus callosum    Synthesis, review
         ↘             ↓               ↙
              [limbic/] — Memory & Urgency
              ├─ hippocampus/ → Long-term memory
              └─ amygdala/    → Critical alerts
                         ↓
               [automation/] — Routines

  [cortex/default-mode/]  ← DMN — fires outside thalamic routing
   Idle-state association      Candidate insights → corpus callosum
   Incubation queue            Not part of dispatch
```

## Principles

1. **Dual Encoding** — Important items exist in both hemispheres (analytical + creative)
2. **Hub Architecture** — Prefrontal (executive.md) connects to all regions
3. **No Deep Nesting** — Max 2 levels (like cortex layers)
4. **Cross-References** — Files link to related regions
5. **Plasticity** — Structure evolves with use

## Quick Start

1. Start: `cortex/prefrontal/executive.md`
2. Memory: `limbic/hippocampus/`
3. Urgent: `limbic/amygdala/`
4. Input: `thalamus/inbox.md`

## Customizing for Your Domain

The routing tables in `cortex/prefrontal/executive.md`, `thalamus/routing-rules.md`, and `automation/mirror-neurons.md` contain generic patterns. Add rows for your specific task types (e.g., "Pull request review", "Named candidate for evaluation", "Document summarization") and define the corresponding region activation sequence.

The adversary reference in `connections/corpus-callosum.md` and `automation/mirror-neurons.md` is a placeholder for a domain-specific challenge agent — replace it with whatever critical-review mechanism fits your workflow.
