# Canonical Workflow

This document defines the canonical lifecycle for converting a large project/change into implementation-ready work for Codex.

## 1. Roles

ChatGPT is the planning and orchestration layer. It performs architecture reasoning, research, repository inspection, decomposition, expansion, optimization, context recovery, and implementation review.

The working GitHub repository is the source of truth for current code and active architecture.

Persistent planning storage may be either ChatGPT Library or a dedicated plan folder in the working GitHub repository.

Codex agents implement prepared GOALs, test, debug, validate, and report material deviations.

## 2. Manual Context Rule

The canonical workflow manual must remain an active reference throughout the entire planning lifecycle.

ChatGPT must:

- read the manual at the beginning of every new or continuation chat;
- refresh the relevant sections before major phase transitions;
- refresh it after a handoff before continuing substantial work;
- re-read it whenever workflow behavior is uncertain or apparently conflicts with conversation memory, Project Instructions, handoff state, or planning artifacts.

Do not rely solely on remembered workflow rules when the canonical manual can be read directly.

For workflow procedure, this manual is authoritative.

For software implementation facts, the current working GitHub repository remains authoritative.

## 3. Source precedence

For software facts, when sources conflict:

1. current working repository code and active architecture;
2. newest canonical/consolidated plan;
3. newer implementation plan parts and macroblocks;
4. historical plans and notes.

Do not revive superseded architecture merely because an older document contains more detail.

## 4. Initialization

A ChatGPT Project should contain the generic plain-text PROJECT_INSTRUCTIONS template.

The first chat uses START_PROMPT.

ChatGPT reads the local instructions and this canonical manual.

If the working repository is unknown, ask for it. Verify access and inspect its current state before project planning becomes repository-specific.

Before advancing into a major phase, refresh the relevant manual sections.

## 5. Storage Gate

After the working repository is known, offer GITHUB or LIBRARY and record the choice and planning root in PROJECT.md.

GITHUB is the recommended planning backend when available. LIBRARY is a fallback when GitHub storage is unavailable, unsuitable, or the user explicitly wants unfinished planning outside the repository.

### LIBRARY — fallback

Library permission prompts can make long planning sessions tedious. Small expansions may trigger repeated approvals, sometimes several around a single write sequence. Warn the user before writes. If native mobile UI cannot present approval requests, use a web browser.

### GITHUB — recommended

Inspect the working repository for an existing planning convention.

Always create a new folder for each independent plan. Reuse an existing plans/planning parent directory when appropriate. Otherwise default to plans/<plan-name>/.

Explain that planning writes may create incremental commits and obtain authorization to maintain planning files inside that folder.

After scoped authorization, routine writes inside that folder do not need a new confirmation. Writes outside it do.

Avoid micro-commits without changing planning granularity. Continue working on one micro-expansion at a time and keep intermediate drafting in memory when practical. Consolidate related planning writes so one expansion preferably creates only one or two commits. Do not create a local file tree or artificial batch process solely to reduce commit count.

GitHub mode requires no final publication step because the plan is already persistent in the repository.

## 6. Master-plan phase

The user may provide requirements over many invocations. Brainstorm, research, inspect code, compare alternatives, and refine decisions.

Before consolidating or materially revising MASTER_PLAN.md, refresh the relevant manual guidance.

MASTER_PLAN.md is the first canonical planning artifact. It is a compact backbone, not an implementation expansion.

Capture requirements/outcomes, architecture decisions, constraints/invariants, non-goals, major systems, high-level dependencies, compatibility expectations, and unresolved decisions that truly require user input.

Avoid large production-code examples and file-by-file implementation detail.

Split the master plan into coherent subfiles if necessary, but preserve a compact top-level MASTER_PLAN.md.

Do not begin implementation decomposition until the user explicitly approves the master plan for implementation planning.

## 7. Implementation-planning gate

At user approval:

1. refresh the relevant manual sections;
2. establish persistent project storage if not already established;
3. create/update PROJECT.md;
4. preserve backup/MASTER_PLAN.original.md;
5. start decomposition.

The original backup is an immutable semantic baseline. Git history does not replace its purpose.

## 8. Decomposition phase

Decomposition and expansion are separate.

First define macroblocks, ordered microsteps, dependencies, outputs, preliminary agent assignment, and provisional plan files.

Create PLAN_INDEX.md and small skeleton files where useful.

Do not fully expand implementation details during decomposition.

Each microstep is LUA-high, SOL-high, or UNASSIGNED. UNASSIGNED is temporary and forbidden in the final handoff.

## 9. File Safety

Implementation-planning files should normally target about 1,200-1,600 lines.

A small overage into roughly 1,600-1,700 lines is acceptable. Do not compact, recreate, or subdivide an already coherent and manageable file solely because it landed slightly above the normal target.

Consider preventive subdivision prospectively around 1,700-1,800 lines, especially when complexity or structure also warrants it.

Do not intentionally produce a plan file above approximately 2,000 lines.

The ceiling is not a target. High reasoning complexity, research, tool usage, repository inspection, or dense implementation detail may require splitting much earlier.

Estimate size and complexity before drafting. Recursively subdivide when needed.

## 10. Context Safety Check

File size and conversation-context pressure are independent constraints.

Before every substantial planning operation assess whether the current chat can finish it cleanly.

SAFE - continue normally.

CAUTION - complete only the current bounded operation; reassess before starting another large operation.

HANDOFF - do not start the next substantial operation; persist state and move to a successor chat.

There is no reliable exact remaining-context counter. Use observable risk factors: accumulated conversation size, recently loaded material, required repository inspection, expected reasoning/output, repeated tool/response failures, loss of earlier details, abnormal incompleteness, or interface warnings.

When uncertain, prefer a planned handoff.

This applies during master-plan consolidation, decomposition, expansion, research, audits, and final Codex handoff preparation.

## 11. Expansion phase

Before entering the expansion phase, refresh the relevant manual sections.

Expand one substantial plan part at a time unless several parts are clearly small and safe.

Before every expansion:

1. perform a Context Safety Check;
2. inspect the relevant current source code directly in the working GitHub repository;
3. reconcile it with the master plan, index, dependencies, and previously expanded interfaces;
4. resolve architectural questions that repository evidence can answer;
5. expand the part into concrete implementation instructions;
6. persist the result;
7. update PLAN_INDEX.md and CHAT_HANDOFF.md when state changes require it.

Planning files are not evidence of current code state. Conversation memory and old repository inspections are not substitutes for current source.

An expanded plan should provide verified paths/symbols when available, state ownership, interfaces/contracts, data flow, algorithms, invariants, compatibility rules, error behavior, migration/cleanup requirements, validation, and definition of done.

Useful pseudocode or implementation code may be included when it materially reduces implementation-agent reasoning.

### Continuous Expansion Mode

Continuous Expansion Mode is an opt-in execution style for the expansion phase. Enable it when the user explicitly asks ChatGPT to continue across checkpoints without waiting for repeated "continue" messages.

The planning granularity does not change: perform one bounded expansion or subdivision at a time, persist its checkpoint, reassess Context Safety, and only then proceed automatically.

A hard per-chat ceiling applies: at most 4 continuous planning operations may be completed in one chat. After operation 4, ChatGPT must not begin operation 5. It must persist/update the operational state, update CHAT_HANDOFF.md, and end with a populated continuation prompt for a successor chat.

For this counter, use semantic operations rather than commit count:

- completing one plan-file expansion counts as 1;
- structurally subdividing one pending plan into subplans counts as 1, even if several subfiles are created;
- repository inspection, source re-verification, checkpoint persistence, and routine PLAN_INDEX.md or CHAT_HANDOFF.md synchronization do not count separately.

The counter belongs to the chat, not to an individual user invocation. A manual "continue" in the same chat does not reset it. The successor chat begins at 0/4.

This ceiling does not override Context Safety. CAUTION, HANDOFF, blockers, tool failures, abnormal latency, repeated response failures, or other signs of degradation may force an earlier handoff.

CHAT_HANDOFF.md must record whether Continuous Expansion Mode remains active so the successor can continue automatically after reconstructing state.

## 12. Minimal chat output during expansion

The persisted plan file is the primary output.

Do not reproduce or summarize the expanded content in chat unless the user asks.

Chat output should normally contain only continuity information: completed/updated/subdivided file, storage permission needed, blocker/user decision, next file/action, Context Safety warning, or handoff status.

Avoid spending context twice on the same implementation content.

## 13. Chat Handoff

CHAT_HANDOFF.md is an operational checkpoint, not a conversation transcript.

Maintain enough information to resume from a new chat: phase, storage mode/root, working repository/base, last completed item, next item, recent non-canonical decisions, blockers, decomposition changes, and safe continuation point.

When the user requests a handoff, or a planned/emergency handoff is needed, persist/update CHAT_HANDOFF.md and generate the continuation prompt in the same response.

The prompt must be dynamically populated, not returned as an unfilled template. Include working repository/base, storage mode/root, current phase, last completed work, next safe action, and exact persistent files to read first.

Place it in a plain-text copyable code block as the final element of the response. Put no explanatory text after it.

The successor chat must re-read the manual, then read PROJECT.md, CHAT_HANDOFF.md, MASTER_PLAN.md, and PLAN_INDEX.md, inventory the plan directory, load only the files required for the next operation, and re-verify relevant code against the current repository.

## 14. Final optimization audit

Before starting the final audit, refresh the relevant manual sections.

After every plan part is expanded, inspect the complete plan file by file.

Look for unresolved ambiguity, stale repository assumptions, missing interfaces/contracts/algorithms/tests, opportunities to provide more implementation-ready code/pseudocode, unsafe file sizes, overlaps/gaps, incorrect dependencies, UNASSIGNED work, and SOL-high work that can become LUA-high after preparation.

The final audit may subdivide parts again.

Only after this audit should PLAN_INDEX.md be considered implementation-ready.

## 15. Execution model

Keep four concepts distinct:

Plan Part - safely sized ChatGPT planning artifact.

Micro Step - logical unit of work.

Implementation Batch - compatible microsteps implemented before a broad validation boundary.

GOAL - continuous autonomous mission assigned to one implementation agent.

Planning granularity must not dictate execution or test granularity.

Many plan files may belong to one GOAL. Minimize agent switches. Prefer broad coherent implementation and validation at meaningful technical boundaries rather than full test cycles after every small part.

## 16. Codex handoff

Before preparing CODEX_HANDOFF.md, refresh the relevant manual sections.

Prepare it only after final optimization.

It must identify working repository/base, plan root, authoritative plan index, GOAL order, assigned agent for each GOAL, plan files/batches included, cross-GOAL dependencies, required validation, and deviation-reporting rules.

In GITHUB storage mode, the plan is already available to implementation agents.

In LIBRARY mode, ask the user for authorization before publishing the completed planning package into a new plan folder in the working repository.

## 17. Review loop

After implementation, review the current repository rather than extending old assumptions.

Classify findings as implementation defect, planning defect, newly discovered repository constraint, optional improvement, or follow-up work.

Any follow-up plan begins from the repository state that exists at that time.
