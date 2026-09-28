# Codex Implementation Handoff

Target repository: <owner/repository>  
Base branch/ref: <branch or commit>  
Plan index: <path to PLAN_INDEX file>  
Implementation mode: <single continuous run / staged>

## Mission

Implement the complete plan described by the index and its ordered plan-part files.

Read the index first, then read all prerequisite parts before editing dependent code.

## Required behavior

1. Inspect the current repository before editing.
2. Verify that plan assumptions still match the current base.
3. Implement in dependency order.
4. Treat planning-file subdivisions as planning boundaries, not automatically as separate implementation sessions.
5. Keep the repository coherent and buildable through the implementation.
6. Run the validation required by each plan part.
7. Fix regressions introduced by the implementation.
8. Do not redesign unrelated systems.
9. Do not silently revive superseded architecture.
10. Record any material deviation from the plan and the repository evidence that required it.

## Ordered plan files

Read and implement:

1. `<path/to/01-plan.md>`
2. `<path/to/02A-plan.md>`
3. `<path/to/02B-plan.md>`

## Validation

Required final checks:

- <build command>
- <test command>
- <integration check>
- <manual/runtime check if needed>

## Completion report

At the end, report:

- files changed;
- important architectural changes;
- tests/builds executed and results;
- deviations from the plan;
- unresolved blockers;
- follow-up work, only if genuinely required.
