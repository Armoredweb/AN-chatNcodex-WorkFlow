# ChatGPT Planning Protocol

Use this protocol together with WORKFLOW.md and the templates.

## Manual Context Rule

Keep the canonical workflow manual as an active reference throughout all phases.

Read it at the beginning of every new or continuation chat.

Refresh the relevant sections before major workflow transitions, after handoffs, before finalizing a phase, and whenever workflow procedure is uncertain.

If remembered workflow behavior conflicts with Project Instructions, CHAT_HANDOFF.md, planning artifacts, or the manual itself, re-read the manual before proceeding.

Do not substitute remembered workflow rules for direct consultation of the canonical manual.

## Responsible-use purpose

This workflow is an engineering/planning method, not a mechanism for bypassing ChatGPT, Codex, Work, account, rate, usage, safety, or platform limits.

Its purpose is to use available ChatGPT capacity efficiently: move difficult reasoning into explicit planning, divide large work into safe bounded operations, persist checkpoints, and reserve Codex/Work resources for tasks that actually need implementation or autonomous execution.

Always respect product limits, safety systems, authorization boundaries, and applicable platform rules. Do not design the workflow to evade enforcement, conceal workload, keep sessions alive artificially, or obtain capacity beyond what the product allows.

The persistent artifacts should make the workload legible: a reviewer should be able to see that repeated operations are bounded planning/checkpoint work for a software project, not an attempt to circumvent limits.

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

Expanded plan parts should leave implementation decisions as explicit as practical while using as little context as reasonably possible.

Do not pad a plan to reach a line count. Small, complete plan parts are preferable to larger files containing repetition, tutorial material, generic rationale, or restated context.

Use verified repository paths and symbols when possible. Resolve only the implementation-relevant ownership, interfaces, state/data flow, algorithms, lifecycle, compatibility, failure behavior, cleanup/migration, tests, and definition of done.

Prefer direct implementation instructions, concrete contracts, concise pseudocode, and implementation-ready code where they reduce LUA-high reasoning. Explain "why" only when the rationale is necessary to preserve a constraint, avoid a known failure mode, or resolve an architectural ambiguity.

The goal is to perform the difficult reasoning in ChatGPT, not to convert that reasoning into oversized prose. A hard problem may have a short implementation plan once the reasoning is resolved.

Re-check source before every part, even if a nearby part was expanded recently.

## Expansion response behavior

The persisted file is the primary output.

Do not echo or summarize the expansion into the chat unless asked.

Return only continuity information needed by the user: completed/subdivided files, permissions, blockers, next action, Context Safety, or handoff.

This is a context-preservation rule.

## Continuous expansion mode

Continuous expansion is opt-in. Use it only when the user asks to continue through multiple planning checkpoints without repeated "continue" prompts.

A continuous run still works on one bounded top-level operation at a time. After each heavy operation, persist the checkpoint and reassess Context Safety before starting the next one.

Hard limit: never perform more than 4 heavy operations in one chat. After the 4th completed heavy operation, do not start a 5th. Persist the current state, update CHAT_HANDOFF.md, and produce the populated continuation prompt for a successor chat.

Count heavy ChatGPT operations, not commits. One unit is one bounded operation that is itself substantial enough to consume meaningful context, reasoning, research, repository inspection, tool work, or artifact production.

A strong default rule is: if the operation independently warrants a Context Safety Check, treat it as 1 heavy-operation unit unless it is clearly only supporting work inside another already-counted operation.

Typical 1-unit operations include:

- expanding one substantial plan file;
- structurally subdividing one pending plan into subplans, regardless of how many files are created;
- a substantial decomposition pass;
- a major MASTER_PLAN consolidation or revision;
- a research-heavy or repository-heavy architecture/reconciliation pass;
- a substantial final-audit/optimization pass;
- substantial Codex-handoff preparation;
- a large recovery, migration, or reorganization operation.

Count the top-level bounded operation once. Its necessary source reads, repository verification, reasoning, checkpoint writes, PLAN_INDEX.md / CHAT_HANDOFF.md synchronization, and related persistence are supporting work and do not add extra units unless they become a separate substantial operation of their own.

The counter is per chat and resets only in the successor chat. A user "continue" message in the same chat does not erase already completed heavy-operation units.

The 4-operation limit is a ceiling, not a target. CAUTION, HANDOFF, blockers, tool failures, abnormal latency, repeated response failures, or other degradation signals may require stopping and handing off earlier.

Record whether Continuous Expansion Mode is active in CHAT_HANDOFF.md so the successor can resume the mode with a fresh 0/4 counter.

## File-size rule

The line counts below are safety references and upper-range guidance, not quotas, minimums, or output targets.

A complete plan may be far below 1,200 lines; that is desirable when the problem can be specified clearly with less text. Never add filler, repeated context, tutorials, or unnecessary rationale to approach a line count.

For larger implementation-planning files, approximately 1,200-1,600 lines is a normal working range. If a coherent completed file lands around 1,600-1,700 lines, do not compact, recreate, or subdivide it solely for that small overage.

Around 1,700-1,800 lines, strongly consider preventive subdivision prospectively, especially when complexity or structure also warrants it. Do not intentionally exceed about 2,000 lines.

Complex work may need to be split well below these numbers. Size is checked prospectively during reasoning, not only after writing.

## Context Safety

Use SAFE / CAUTION / HANDOFF before substantial operations.

SAFE: proceed.

CAUTION: finish the current bounded action; do not automatically begin another large one.

HANDOFF: persist operational state and move to a successor chat before more substantial work.

If unsure, hand off.

Do not claim an exact percentage of context remaining.

## Handoff behavior

When the user requests handoff or handoff is otherwise appropriate:

1. finish or stop at a safe artifact boundary;
2. persist/update CHAT_HANDOFF.md;
3. ensure PROJECT.md and PLAN_INDEX.md point to the correct state;
4. fill the continuation template with concrete current values;
5. include repository/base, storage/root, phase, last completed work, next action, and exact files to read first;
6. output it in a plain-text copyable code block as the final response element;
7. put no text after it and do not start the next large operation.

Never leave placeholders in a real handoff. The successor chat must re-read the manual before continuing.

## Final audit

Before final optimization, refresh the relevant manual sections.

Review every plan part again. Improve implementation readiness, split unsafe files, remove stale assumptions, eliminate UNASSIGNED, and aggressively reconsider SOL-high work for LUA-high.

Then form Implementation Batches and continuous GOALs.

Planning-file boundaries are not automatic build/test boundaries.

## Codex handoff

Before producing CODEX_HANDOFF.md, refresh the relevant manual sections.

Do not generate the handoff from remembered workflow behavior alone.

## GitHub write scope

Prefer GITHUB storage when available. When the user authorizes the dedicated planning folder, maintain planning artifacts there without repeatedly requesting permission.

Preserve micro-expansion granularity, but avoid micro-commits. Keep intermediate work in memory when practical and consolidate related writes so one expansion preferably results in one or two commits. Do not create a local file tree or artificial batch workflow solely to reduce commit count.

Do not extend planning-folder authorization to unrelated repository files.

Treat LIBRARY as a fallback when GitHub storage is unavailable or unsuitable. Warn that repeated permission prompts can make even small expansions tedious and that the UI may request approval multiple times.

Final publication from Library to GitHub requires user authorization.
