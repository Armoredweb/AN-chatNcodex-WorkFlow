# Canonical Workflow

This document defines the canonical lifecycle for converting a large project/change into implementation-ready work for Codex.

## 1. Roles

ChatGPT is the planning and orchestration layer. It performs architecture reasoning, research, repository inspection, decomposition, expansion, optimization, context recovery, and implementation review.

The working GitHub repository is the source of truth for current code and active architecture.

Persistent planning storage may be either ChatGPT Library or a dedicated plan folder in the working GitHub repository.

Codex agents implement prepared GOALs, test, debug, validate, and report material deviations.

## 2. Source precedence

When information conflicts:

1. current working repository code and active architecture;
2. newest canonical/consolidated plan;
3. newer implementation plan parts and macroblocks;
4. historical plans and notes.

Do not revive superseded architecture merely because an older document contains more detail.

## 3. Initialization

A ChatGPT Project should contain the generic PROJECT_INSTRUCTIONS template.

The first chat uses START_PROMPT.

ChatGPT reads the local instructions and this canonical manual.

If the working repository is unknown, ask for it. Verify access and inspect its current state before project planning becomes repository-specific.

## 4. Storage Gate

After the working repository is known, ask the user to choose LIBRARY or GITHUB.

Record the choice and planning root in PROJECT.md.

### LIBRARY

Use a dedicated persistent Library project folder after the implementation-planning gate.

Before a Library write, warn the user that a permission request may appear. If native mobile UI cannot present the request, use a web browser.

Library mode keeps unfinished planning separate from the working repository.

### GITHUB

Inspect the working repository for an existing planning convention.

Always create a new folder for each independent plan. Reuse an existing plans/planning parent directory when appropriate. Otherwise default to plans/<plan-name>/.

Explain that planning writes may create incremental commits and obtain authorization to maintain planning files inside that folder.

After scoped authorization, routine writes inside that folder do not need a new confirmation. Writes outside it do.

GitHub mode requires no final publication step because the plan is already persistent in the repository.

## 5. Master-plan phase

The user may provide requirements over many invocations. Brainstorm, research, inspect code, compare alternatives, and refine decisions.

MASTER_PLAN.md is the first canonical planning artifact. It is a compact backbone, not an implementation expansion.

Capture:

- requirements and outcomes;
- architecture decisions;
- constraints and invariants;
- non-goals;
- major systems;
- high-level dependencies;
- compatibility expectations;
- unresolved decisions that truly require user input.

Avoid large production-code examples and file-by-file implementation detail.

Split the master plan into coherent subfiles if necessary, but preserve a compact top-level MASTER_PLAN.md.

Do not begin implementation decomposition until the user explicitly approves the master plan for implementation planning.

## 6. Implementation-planning gate

At user approval:

1. establish persistent project storage if not already established;
2. create/update PROJECT.md;
3. preserve backup/MASTER_PLAN.original.md;
4. start decomposition.

The original backup is an immutable semantic baseline. Git history does not replace its purpose.

## 7. Decomposition phase

Decomposition and expansion are separate.

First define:

- macroblocks;
- ordered microsteps;
- dependencies;
- outputs;
- preliminary agent assignment;
- provisional plan files.

Create PLAN_INDEX.md and small skeleton files where useful.

Do not fully expand implementation details during decomposition.

Each microstep is LUA-high, SOL-high, or UNASSIGNED. UNASSIGNED is temporary and forbidden in the final handoff.

## 8. File Safety

Implementation-planning files should normally target about 1,200-1,600 lines.

Consider preventive subdivision around 1,700-1,800 lines.

Do not intentionally produce a plan file above approximately 2,000 lines.

The ceiling is not a target. High reasoning complexity, research, tool usage, repository inspection, or dense implementation detail may require splitting much earlier.

Estimate size and complexity before drafting. Recursively subdivide when needed.

## 9. Context Safety Check

File size and conversation-context pressure are independent constraints.

Before every substantial planning operation assess whether the current chat can finish it cleanly.

Use three operational states:

SAFE - continue normally.

CAUTION - complete only the current bounded operation; reassess before starting another large operation.

HANDOFF - do not start the next substantial operation; persist state and move to a successor chat.

There is no reliable exact remaining-context counter. Use observable risk factors: accumulated conversation size, recently loaded material, required repository inspection, expected reasoning, expected output, repeated tool/response failures, loss of earlier details, abnormal incompleteness, or interface warnings.

When uncertain, prefer a planned handoff.

This check applies during master-plan consolidation, decomposition, expansion, research, audits, and final Codex handoff preparation.

## 10. Expansion phase

Expand one substantial plan part at a time unless several parts are clearly small and safe.

Before every expansion:

1. inspect the relevant current source code directly in the working GitHub repository;
2. reconcile it with the master plan, index, dependencies, and previously expanded interfaces;
3. resolve architectural questions that repository evidence can answer;
4. expand the part into concrete implementation instructions;
5. persist the result;
6. update PLAN_INDEX.md and CHAT_HANDOFF.md when state changes require it.

Planning files are not evidence of current code state. Conversation memory and old repository inspections are not substitutes for current source.

An expanded plan should provide verified paths/symbols when available, state ownership, interfaces/contracts, data flow, algorithms, invariants, compatibility rules, error behavior, migration/cleanup requirements, validation, and definition of done.

Useful pseudocode or implementation code may be included when it materially reduces implementation-agent reasoning.

## 11. Minimal chat output during expansion

The persisted plan file is the primary output.

Do not reproduce or summarize the expanded content in chat unless the user asks.

Chat output should normally contain only continuity information:

- completed/updated/subdivided file;
- storage permission needed;
- blocker or user decision;
- next file/action;
- Context Safety warning;
- handoff status.

Avoid spending context twice on the same implementation content.

## 12. Chat Handoff

CHAT_HANDOFF.md is an operational checkpoint, not a conversation transcript.

Maintain enough information to resume from a new chat: phase, storage mode/root, working repository/base, last completed item, next item, recent non-canonical decisions, blockers, decomposition changes, and safe continuation point.

When a planned or emergency handoff is needed, persist/update it and provide CHAT_CONTINUATION_PROMPT.

The successor chat reads PROJECT.md, CHAT_HANDOFF.md, MASTER_PLAN.md, and PLAN_INDEX.md, inventories the plan directory, loads only the files required for the next operation, and re-verifies relevant code against the current repository.

## 13. Final optimization audit

After every plan part is expanded, inspect the complete plan file by file.

Look for:

- unresolved ambiguity;
- stale repository assumptions;
- missing interfaces/contracts/algorithms/tests;
- opportunities to provide more implementation-ready code/pseudocode;
- unsafe file sizes;
- overlaps and gaps;
- incorrect dependencies;
- UNASSIGNED work;
- SOL-high work that can become LUA-high after preparation.

The final audit is allowed to subdivide parts again.

Only after this audit should PLAN_INDEX.md be considered implementation-ready.

## 14. Execution model

Keep four concepts distinct:

Plan Part - safely sized ChatGPT planning artifact.

Micro Step - logical unit of work.

Implementation Batch - compatible microsteps implemented before a broad validation boundary.

GOAL - continuous autonomous mission assigned to one implementation agent.

Planning granularity must not dictate execution or test granularity.

Many plan files may belong to one GOAL. Minimize agent switches. Prefer broad coherent implementation and validation at meaningful technical boundaries rather than full test cycles after every small part.

## 15. Codex handoff

Prepare CODEX_HANDOFF.md only after final optimization.

It must identify:

- working repository/base;
- plan root;
- authoritative plan index;
- GOAL order;
- assigned agent for each GOAL;
- plan files/batches included;
- cross-GOAL dependencies;
- required validation;
- deviation-reporting rules.

In GITHUB storage mode, the plan is already available to implementation agents.

In LIBRARY mode, ask the user for authorization before publishing the completed planning package into a new plan folder in the working repository.

## 16. Review loop

After implementation, review the current repository rather than extending old assumptions.

Classify findings as implementation defect, planning defect, newly discovered repository constraint, optional improvement, or follow-up work.

Any follow-up plan begins from the repository state that exists at that time.
