# ChatGPT Planning Protocol

Use this protocol together with WORKFLOW.md and the templates.

## Manual Context Rule

Keep the canonical workflow manual as an active reference throughout all phases.

Read it at the beginning of every new or continuation chat.

Refresh the relevant sections before major workflow transitions, after handoffs, before finalizing a phase, and whenever workflow procedure is uncertain.

If remembered workflow behavior conflicts with Project Instructions, CHAT_HANDOFF.md, planning artifacts, or the manual itself, re-read the manual before proceeding.

Do not substitute remembered workflow rules for direct consultation of the canonical manual.

## Start behavior

1. Read the ChatGPT Project instructions.
2. Read the canonical workflow repository.
3. Determine whether this is a new workflow or continuation.
4. If continuation artifacts exist, recover from persistent files before asking the user to repeat information.
5. If the working GitHub repository is unknown, ask for it.
6. Verify the repository and inspect its relevant current state.
7. If planning storage is unknown, run the Storage Gate.

Do not assume repository state from conversation memory.

## New project behavior

Before the implementation-planning gate, help the user develop the complete MASTER_PLAN.

The user may send requirements in several invocations. Preserve decisions without prematurely turning every idea into an implementation part.

Use web research when current or external information materially affects the plan.

Use repository inspection whenever design decisions depend on existing code.

Before consolidating or materially revising MASTER_PLAN.md, refresh the relevant manual sections.

The master plan should remain navigable and compact. Split the backbone if necessary.

## Implementation-planning gate

Do not cross this gate implicitly.

Wait until the user indicates the master plan is ready for implementation planning.

Refresh the relevant manual sections, then persist the approved plan, preserve the original backup, and decompose.

## Decomposition behavior

Read the whole approved master plan and create a dependency-oriented PLAN_INDEX.

Think in microsteps, but do not expand them yet.

For each microstep determine purpose, prerequisites, outputs, affected system, preliminary agent assignment, and provisional plan filename.

Prefer more small planning units over a few unsafe giant units. This does not imply separate implementation runs.

## Agent assignment

Use LUA-high as the default implementation candidate.

Use SOL-high when the work remains complex after strong preparation.

Use UNASSIGNED only while information is insufficient.

Do not assign SOL merely because a task is broad. First ask whether better planning, contracts, algorithms, code sketches, repository evidence, or subdivision can make it straightforward enough for LUA.

Minimize final agent switching across GOALs.

## Expansion preflight

Before entering expansion, refresh the relevant manual sections.

Before beginning any substantial expansion:

1. perform a Context Safety Check;
2. estimate expected output size/complexity;
3. subdivide before drafting if needed;
4. re-read the relevant current GitHub source.

Do not begin an unsafe operation and hope it fits.

## Expansion requirements

Expanded plan parts should leave implementation decisions as explicit as practical.

Use verified repository paths and symbols when possible.

Resolve ownership, interfaces, state/data flow, algorithms, lifecycle, compatibility, failure behavior, cleanup/migration, tests, and definition of done.

Provide useful pseudocode or code where doing so materially reduces implementation-agent thinking, but do not invent production details contradicted by the live repository.

Re-check source before every part, even if a nearby part was expanded recently.

## Expansion response behavior

The persisted file is the primary output.

Do not echo or summarize the expansion into the chat unless asked.

Return only continuity information needed by the user: completed/subdivided files, permissions, blockers, next action, Context Safety, or handoff.

This is a context-preservation rule.

## File-size rule

Target approximately 1,200-1,600 lines for implementation-planning files.

Around 1,700-1,800 lines, strongly consider preventive subdivision.

Do not intentionally exceed about 2,000 lines.

Complex work may need to be split well below these numbers.

Size is checked prospectively during reasoning, not only after writing.

## Context Safety

Use SAFE / CAUTION / HANDOFF before substantial operations.

SAFE: proceed.

CAUTION: finish the current bounded action; do not automatically begin another large one.

HANDOFF: persist operational state and move to a successor chat before more substantial work.

If unsure, hand off.

Do not claim an exact percentage of context remaining.

## Handoff behavior

When handoff is appropriate:

1. finish or stop at a safe artifact boundary;
2. persist/update CHAT_HANDOFF.md;
3. make sure PROJECT.md and PLAN_INDEX.md point to the correct state;
4. give the user CHAT_CONTINUATION_PROMPT;
5. do not start the next large operation.

The successor chat must re-read the manual before continuing.

## Final audit

Before final optimization, refresh the relevant manual sections.

Review every plan part again. Improve implementation readiness, split unsafe files, remove stale assumptions, eliminate UNASSIGNED, and aggressively reconsider SOL-high work for LUA-high.

Then form Implementation Batches and continuous GOALs.

Planning-file boundaries are not automatic build/test boundaries.

## Codex handoff

Before producing CODEX_HANDOFF.md, refresh the relevant manual sections.

Do not generate the handoff from remembered workflow behavior alone.

## GitHub write scope

When GITHUB storage was explicitly selected and the user authorized the dedicated planning folder, maintain planning artifacts inside that folder without repeatedly requesting permission.

Do not extend that authorization to unrelated repository files.

When LIBRARY storage was selected, warn before Library writes because the UI may require explicit approval.

Final publication from Library to GitHub requires user authorization.
