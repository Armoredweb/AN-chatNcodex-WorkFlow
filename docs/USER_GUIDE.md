# User Guide

This is the complete user-facing guide. You do not need to open any template files.

The operational rules used by ChatGPT live in `docs/WORKFLOW.md`. The two copyable blocks below are the only setup text you need.

## 1. Create a ChatGPT Project

Create a new ChatGPT Project and paste the entire block below into Project Instructions:

```text
AN-chatNcodex WORKFLOW - PROJECT INSTRUCTIONS

Canonical workflow:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow/blob/main/docs/WORKFLOW.md

Read the canonical workflow at every new or continuation chat and refresh relevant sections before major phase changes or whenever procedure is uncertain.

PURPOSE

Use ChatGPT as the heavy architecture/planning layer, GitHub as the current-code source of truth and preferred planning store, and Codex agents for prepared implementation work.

This workflow is not intended to bypass ChatGPT, Codex, Work, account, rate, usage, safety, or platform limits. Checkpoints, handoffs, multiple chats, and continuous mode only divide legitimate work into bounded operations. Respect all product limits, safeguards, authorization boundaries, and platform rules.

START / RECOVERY

For a continuation, reconstruct state from PROJECT.md, CHAT_HANDOFF.md, MASTER_PLAN.md, and PLAN_INDEX.md. Inventory other plan files but load only what the next operation needs. Re-check relevant current repository source before implementation-level decisions.

If the working repository is unknown, ask for it and verify access.

STORAGE

Prefer GitHub planning storage in a dedicated plan-specific folder using the repository's existing convention or plans/<plan-name>/. Obtain scoped authorization for routine planning writes there. Library is a fallback when GitHub is unavailable or unsuitable; warn that repeated approvals may make it tedious.

MASTER PLAN / DECOMPOSITION

Keep MASTER_PLAN.md compact. Do not begin decomposition until the user explicitly approves implementation planning. At that gate preserve backup/MASTER_PLAN.original.md.

Decomposition and expansion are separate. Create dependency-oriented microsteps and provisional plan files first. LUA-high is the default implementation role; keep SOL-high only when strong preparation cannot remove substantial reasoning. UNASSIGNED is temporary only.

PLANNING EFFICIENCY

Optimize for implementation readiness per token. Do the difficult reasoning in ChatGPT, then write the smallest complete plan the implementation agent needs.

Do not add filler, repeated context, tutorials, generic explanation, or prose to reach a line count. Small complete subplans are good.

Line counts are safety guidance only. For larger files, about 1,200-1,600 lines is a normal working range; a coherent 1,600-1,700-line file does not need rewriting only for size. Consider subdivision around 1,700-1,800 and do not intentionally exceed about 2,000.

Prefer verified paths/symbols, direct instructions, concrete contracts, concise algorithms/code/pseudocode, relevant tests, and definition of done. Explain rationale only when needed to preserve a non-obvious constraint, compatibility rule, failure mode, or architecture decision.

CONTEXT SAFETY

Before every substantial operation use SAFE / CAUTION / HANDOFF.

SAFE: proceed.
CAUTION: finish only the current bounded operation, persist it, then reassess.
HANDOFF: do not start another substantial operation; persist state and move to a successor chat.

CONTINUOUS MODE

Enable only when the user explicitly requests automatic continuation across checkpoints.

Count heavy top-level ChatGPT operations, not commits/files. A task that independently warrants Context Safety normally counts as 1 unit. Required reads, verification, reasoning, persistence, and routine index/handoff updates are included in that parent unit.

Hard limit: 4 heavy operations per chat. After operation 4, never start operation 5. Persist state, update CHAT_HANDOFF.md, and end with a populated continuation prompt. A user "continue" in the same chat does not reset the counter; the successor starts at 0/4. Safety/degradation may force earlier handoff.

EXPANSION

Before each substantial expansion: Context Safety, re-read relevant current source, reconcile dependencies/interfaces, resolve questions from evidence, write the smallest implementation-ready plan, persist it, and update index/handoff only as needed.

The persisted plan is the primary output. Do not duplicate detailed implementation content in chat unless asked.

HANDOFF

When requested/required or continuous mode reaches 4/4, persist operational state and END the response with a concrete plain-text continuation prompt. Include repository/base, storage/root, phase, last completed work, next safe action, exact files to read first, and continuous-mode state. No placeholders and no text after the prompt.

FINAL AUDIT

Before Codex handoff, remove stale assumptions, gaps, unnecessary prose, UNASSIGNED work, and avoidable SOL-high work. Finalize Implementation Batches and GOALs only after that audit.

CORE RULE

Spend reasoning to simplify implementation. Heavy thinking is not a reason for large output.

```

## 2. Start the first chat

Open a chat inside that Project and send:

```text
Read the instructions configured for this ChatGPT Project first.

Then read the canonical workflow:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow/blob/main/docs/WORKFLOW.md

Follow it for this project.

Determine whether this is a new workflow or a continuation with persistent planning state.

If continuing, reconstruct state from persistent artifacts instead of asking me to repeat prior work.

If the working GitHub repository is not already known, ask me for it and verify it before repository-specific planning.

Do not assume current code or architecture from conversation memory. Use the working repository as the source of truth.

For a new workflow, run the Storage Gate after verifying the repository.

```

ChatGPT will ask for the working GitHub repository if it is not already known, verify it, and then establish planning storage.

## 3. Responsible use

The workflow is for legitimate software planning. It does not exist to bypass ChatGPT/Codex/Work limits, rate limits, safety systems, account rules, or authorization boundaries.

Multiple chats, checkpoints, handoffs, and continuous mode divide work into bounded operations and preserve state. Platform limits always take precedence.

The intended efficiency is to do expensive architecture/planning reasoning in ChatGPT, write only the implementation-relevant result, and reserve Codex/Work for tasks that genuinely need implementation or autonomous execution.

## 4. Build the master plan

Describe the project/change across as many messages as needed. ChatGPT may research, inspect the repository, compare alternatives, and refine requirements.

Useful prompt:

```text
Build/refine the master plan with me. Keep it compact, verify repository-dependent assumptions against current source, and do not begin implementation decomposition until I explicitly approve it.
```

When ready:

```text
MASTER_PLAN approved. Begin implementation planning using the canonical workflow.
```

At that gate ChatGPT preserves the approved master-plan baseline and starts decomposition.

## 5. Decomposition and expansion

Decomposition first defines macroblocks, microsteps, dependencies, provisional plan files, and preliminary LUA-high/SOL-high assignments. Detailed expansion comes later.

Expansion is optimized for implementation readiness per token. A difficult problem does not need a large plan. Small complete subplans are desirable.

Line counts are safety guidance only. ChatGPT must not pad files with tutorials, repeated background, generic rationale, or filler.

## 6. Continuous mode

If you want ChatGPT to continue automatically after each checkpoint, say:

```text
Enable Continuous Mode and continue automatically across checkpoints following the canonical workflow.
```

Continuous mode still performs one bounded heavy operation at a time.

A heavy operation is a substantial top-level task such as a large expansion, subdivision, decomposition, architecture/repository reconciliation, final audit, recovery/migration, or Codex-handoff preparation.

The hard limit is 4 heavy operations per chat. After operation 4, ChatGPT persists state and returns a handoff prompt for a successor chat instead of starting operation 5. The successor starts at 0/4. Context Safety may force an earlier handoff.

## 7. Handoff to another chat

You can request a handoff at any time:

```text
Prepare a handoff for a new chat following the canonical workflow.
```

ChatGPT updates the persistent handoff state and ends its response with a populated plain-text continuation prompt. Copy that final block into a new chat in the same Project.

You do not need to compose or maintain a continuation template yourself.

## 8. Final audit and Codex

After all required plan parts are expanded, ChatGPT performs a final optimization audit:

- remove ambiguity and stale assumptions;
- remove unnecessary prose;
- resolve UNASSIGNED work;
- convert SOL-high work to LUA-high where better preparation makes that safe;
- define Implementation Batches and GOALs;
- prepare the final Codex handoff.

Planning files are safety boundaries for planning, not automatic Codex sessions or test boundaries. One GOAL may use many plan files.

## 9. Storage

GitHub is recommended because planning can be persisted directly in a dedicated plan folder and resumed from another chat.

Library is a fallback. It may request repeated write approvals and is therefore less convenient for long micro-expansion workflows.

The current working GitHub repository remains authoritative for implementation facts regardless of planning backend.
