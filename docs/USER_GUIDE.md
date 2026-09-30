# User Guide

This is the complete user-facing guide. There are no separate template files to open or maintain.

The operational rules used by ChatGPT live in `docs/WORKFLOW.md`. The two copyable blocks below are the only setup text you need.

## 1. Create a ChatGPT Project

Create a new ChatGPT Project and paste the entire block below into Project Instructions:

```text
AN-chatNcodex WORKFLOW — PROJECT INSTRUCTIONS

Canonical manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow/blob/main/docs/WORKFLOW.md

MANDATORY MANUAL RULE
Read the canonical manual directly at the start of every new or continuation chat before substantive work. Re-read the relevant sections before major phase transitions, after handoffs, before final planning/Codex handoff, and whenever procedure is uncertain. Never substitute remembered workflow rules for the manual. The manual is authoritative.

CORE OPERATION
Use the current working GitHub repository as source of truth for code/architecture. For continuation, reconstruct state from PROJECT.md, CHAT_HANDOFF.md, MASTER_PLAN.md, PLAN_INDEX.md, and only the Plan Parts needed next. Re-check current source before implementation-level decisions.

Prefer GitHub as planning storage in a dedicated plan folder; Library is fallback. Respect scoped write authorization.

Optimize for implementation readiness per token: do difficult reasoning in ChatGPT, persist the shortest complete implementation-ready result, and never add filler or remove implementation truth merely to save tokens.

LUA-high is the default implementation target. Resolve avoidable decisions in planning and provide contracts/algorithms/code where that makes LUA mechanical. Retain SOL-high only after a final LUA-conversion audit; then optimize surviving SOL work for high-capability reasoning without unnecessary scaffolding.

CONTEXT / EXECUTION
Before substantial work apply Context Safety: SAFE / CAUTION / HANDOFF.

Manual Mode: at most one heavy operation per user invocation, then persist and return control; no fixed accumulated handoff count.

Continuous Mode: 3 heavy operations per block, persist/reassess after each, then stop for user "continue". Up to 4 blocks (12 operations) per chat; after operation 12, mandatory persisted handoff. Context Safety may stop earlier. At each block boundary compact only transient CHAT_HANDOFF state; never substitute this for the full post-expansion audit.

FINALIZATION
After all Plan Parts are expanded, always run the full file-by-file optimization, LUA-conversion gate, cross-artifact Consistency Gate, GOAL/Batch construction, Expected Evidence definition, and Codex handoff described in the manual.

After implementation, validate Expected Evidence and run the Convergence Check until required planned behavior converges or a real blocker/user decision remains.

HANDOFF
When handoff is requested/required, persist state and end the response with a concrete plain-text continuation prompt containing current repository/base, storage/root, phase, last completed work, next action, exact files to read first, and continuous-mode state. No placeholders and no text after it.

RESPONSIBLE USE
This workflow organizes legitimate software planning. It is not intended to bypass product, account, rate, usage, safety, authorization, or platform limits.
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

## 6. Heavy operations and Continuous Mode

A heavy operation is a substantial top-level task such as a large expansion, subdivision, decomposition, architecture/repository reconciliation, final audit, recovery/migration, or Codex-handoff preparation.

In normal Manual Mode, ChatGPT performs at most one heavy operation per message from you, persists the checkpoint, and returns control. You may keep sending `continue` to request one more heavy operation. There is no fixed accumulated handoff count in Manual Mode; you decide when to request the handoff unless Context Safety requires one earlier.

To enable automatic continuation, send:

```text
Enable Continuous Mode and continue automatically across checkpoints following the canonical workflow.
```

Continuous Mode works in blocks of 3 heavy operations. ChatGPT may automatically perform three operations, persisting and reassessing between them. After the third, it compacts only transient handoff state, stops, and waits for you to send `continue`. This does not replace the full final optimization after expansion.

The same chat may run four such blocks:

`3 → continue → 3 → continue → 3 → continue → 3 → handoff`

That is a maximum of 12 continuous heavy operations in one chat. After operation 12, ChatGPT automatically prepares the handoff instead of starting operation 13. A successor chat starts a fresh 3×4 cadence.

This is an experimental workflow safeguard, not a claim about a ChatGPT platform limit. Context Safety or signs of degradation can stop a block or require handoff earlier.

## 7. Handoff to another chat

You can request a handoff at any time:

```text
Prepare a handoff for a new chat following the canonical workflow.
```

ChatGPT updates the persistent handoff state and ends its response with a populated plain-text continuation prompt. Copy that final block into a new chat in the same Project.

You do not need to compose or maintain a continuation template yourself.

## 8. After expansion: audit, consistency, Codex, and convergence

After all required Plan Parts are expanded, the earlier 3-operation block compactions do **not** replace the full final audit.

ChatGPT then:

1. optimizes every Plan Part without losing implementation intent;
2. removes avoidable decisions from LUA-high and adds concrete contracts/code where useful;
3. challenges every SOL-high assignment and keeps SOL only when stronger planning still cannot make the work safely mechanical for LUA;
4. optimizes surviving SOL work for higher-capability reasoning without unnecessary scaffolding;
5. runs a cross-artifact Consistency Gate from `MASTER_PLAN → PLAN_INDEX → Plan Parts → current repository`, repairing inconsistencies at the file that owns the information;
6. defines Implementation Batches and GOALs, marking foundational GOALs that must validate before dependent work;
7. gives every GOAL Expected Evidence that proves its intended result rather than relying only on generic "tests passed";
8. creates the final Codex handoff.

After implementation, ChatGPT runs a Convergence Check against the canonical plan and current repository. Required differences are classified as missing, partial, contradicting, or unrequested, corrected in bounded work, and checked again until required behavior converges or a real blocker/user decision remains.

Planning files are planning-safety boundaries, not automatic Codex sessions or test cycles. One GOAL may use many Plan Parts.

## 9. Storage

GitHub is recommended because planning can be persisted directly in a dedicated plan folder and resumed from another chat.

Library is a fallback. It may request repeated write approvals and is therefore less convenient for long micro-expansion workflows.

The current working GitHub repository remains authoritative for implementation facts regardless of planning backend.
