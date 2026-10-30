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

Whenever ChatGPT already needs to read implementation source for the current operation, use that same reading pass to look for material bugs, architecture inconsistencies, dead/obsolete paths, unnecessary complexity, avoidable hot-path work, and clear optimization opportunities. Do not start extra unrelated source browsing merely to hunt for issues; inspect only minimal adjacent context needed to classify a discovered issue.

Prefer GitHub as planning storage in a dedicated plan folder; Library is fallback. Respect scoped write authorization. For a bounded heavy operation that updates several related planning files, prefer one coherent commit when tooling allows; especially avoid Pass A/B micro-commits.

Optimize for implementation readiness per token: do difficult reasoning in ChatGPT, persist the shortest complete implementation-ready result, and never add filler or remove implementation truth merely to save tokens.

EXPANSION QUALITY
Before every substantial Plan Part expansion, re-read the applicable workflow rules, inspect current source, and actually perform targeted internet research for comparable solutions/techniques. Form specific questions, examine the returned sources, compare meaningful alternatives/trade-offs, and choose the direction that best fits approved goals, architecture, repository and resource targets. Research is for ideas/techniques—not copying external code—and remembered URLs/generic tables do not count as research.

Expansion must explain how non-trivial mechanisms are built: verified repository references, current→desired behavior, contracts, data/state/ownership, algorithms/flows, implementation order, relevant failure/concurrency/resource behavior, tests and objective completion evidence. Detail must be proportional to difficulty; concision must not create planning gaps.

Before marking a Plan Part expanded, perform the Implementation Readiness Self-Check from the manual and repair material gaps. Persist related Plan Part/index/project/handoff updates in one coherent heavy-operation commit when safe/tooling permits.

Luna is the default implementation target. Resolve avoidable decisions in planning and provide contracts/algorithms/code where that makes Luna mechanical. Retain SOL only after a final Luna-conversion audit; then optimize surviving SOL work for high-capability reasoning without unnecessary scaffolding. Never encode Luna/SOL assignment in Plan Part filenames or paths; assignments belong in indexes/metadata/references so they can change without renaming plans.

DECOMPOSITION AUDIT
After the initial decomposition/PLAN_INDEX is persisted, always stop and return control to the user, even in Continuous Mode. The next stage is an iterative Decomposition Audit Gate: freshly re-read persisted MASTER_PLAN.md and PLAN_INDEX.md, check the master plan item by item against the index and the index back against approved intent, correct material gaps in a bounded pass, then repeat the audit from fresh reads. Do not trust conversation memory. Expansion may start only after a complete audit pass finds no material correction.

CONTEXT / EXECUTION
Before substantial work apply Context Safety: SAFE / CAUTION / HANDOFF.

Manual Mode: at most one heavy operation per user invocation, then persist and return control; no fixed accumulated handoff count.

Continuous Mode: 3 heavy operations per block, persist/reassess after each, then stop for user "continue". Up to 4 blocks (12 operations) per chat; after operation 12, mandatory persisted handoff. Context Safety may stop earlier. At each block boundary compact only transient CHAT_HANDOFF state; never substitute this for the full post-expansion audit.

FINALIZATION
After all Plan Parts are expanded, always run the full file-by-file optimization, Luna-conversion gate, cross-artifact Consistency Gate, GOAL/Batch construction, Expected Evidence definition, and Codex handoff described in the manual.

After implementation, validate Expected Evidence and run the Convergence Check until required planned behavior converges or a real blocker/user decision remains.

CODEX ACTIVE MODEL AND PAUSES
CODEX_HANDOFF.md::ACTIVE_MODEL is the sole authoritative persisted model record (Luna or SOL; high effort implicit). Every GOAL reads it directly; NEVER infer the active model from chat context, memory, old user prompts, agent self-identification, previous GOALs or recommendations.

CHANGE ACTIVE_MODEL ONLY when the CURRENT user message explicitly confirms/selects Luna or SOL or requests that update. Older prompts and earlier confirmations expire as authorization; a later "continue" does not authorize replay. Without explicit current-message authorization, leave the field unchanged, even if apparently stale. On an authorized request, persist/verify the one field. If unavailable, report failure and ask for a fresh explicit selection later; never defer/replay the old instruction.

A paused GOAL cannot resume autonomously. Before a planned pause, ask whether the user wants to resume/change models. A model-selection message alone does not resume a GOAL. If still paused, tell the user to resume manually. If updating was blocked during the pause, require a NEW explicit selection message after resumption before writing the field.

After convergence, ChatGPT—not Codex—performs Cleanup Preparation under the same Context Safety/heavy-operation rules, resolves cleanup decisions, and prepares a mechanical CODEX_CLEAN_HANDOFF.md for one Luna Cleanup GOAL. Cleanup never starts automatically: stop and wait for the user to explicitly start that GOAL. Luna executes the prepared cleanup; it does not design the cleanup. The closed cycle leaves a concise CLEANUP_FINDINGS.md for the next planning cycle.

HANDOFF
When handoff is requested/required, persist state and end the response with a concrete plain-text continuation prompt containing current repository/base, storage/root, phase, last completed work, next action, exact files to read first, and continuous-mode state. If expansion remains active, explicitly preserve the requirement to re-apply current-source inspection, actual external research/trade-off comparison, technical-depth/readiness checking and coherent persistence. No placeholders and no text after it.

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

If CLEANUP_FINDINGS.md exists from a previous closed cycle, read it early and reconcile its still-live findings into the new planning cycle.

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

## 5. Decomposition, audit, and expansion

Decomposition first defines macroblocks, microsteps, dependencies, provisional plan files, and preliminary Luna/SOL assignments.

Plan filenames remain agent-neutral: they describe the work, not whether the current assignment is Luna or SOL. Agent changes update the index/header/GOAL metadata without forcing plan-file renames or breaking references.

After the first decomposition and `PLAN_INDEX.md` are persisted, ChatGPT **stops and returns control to you**, even if Continuous Mode is active. Expansion does not start yet.

On your next `continue`, ChatGPT performs the Decomposition Audit Gate. It freshly reads `MASTER_PLAN.md` and `PLAN_INDEX.md` from persistent storage and checks the master plan item by item against the index, then checks the index back against approved intent. It must not trust conversation memory.

If the audit finds material gaps, ordering/dependency errors, duplicated responsibility, missing coverage, or orphaned index work, ChatGPT tells you that another index-correction pass is required; it does not need to print every finding unless a decision is needed. It corrects the index, persists it, then repeats the audit from fresh file reads.

The loop continues:

`fresh audit → correction → fresh audit`

until a complete pass finds no material decomposition correction. Only then may Plan Part expansion begin.

Expansion is optimized for implementation readiness per token, but concision cannot justify missing technical planning. A short Plan Part is not complete merely because it contains the expected headings.

For every substantial expansion, ChatGPT must re-read the applicable workflow rules, inspect current source, formulate specific technical questions, actually research comparable external solutions/techniques, examine the returned sources, compare meaningful alternatives/trade-offs, and select what best fits the project's canonical direction and constraints. Remembered URLs, generic reference lists, or decorative comparison tables do not count as completed research. Research is not for copying external code.

The Plan Part must be technically deep enough for its real implementation difficulty: verified current-code references, current→desired behavior, contracts, structures/states/ownership, algorithms/flows, implementation order, relevant failure/concurrency/resource behavior, tests/instrumentation and objective completion criteria where applicable. Complex mechanisms must explain how to build them so the implementation agent does not need to redo major planning.

Before marking the Plan Part expanded, ChatGPT performs the manual's Implementation Readiness Self-Check and repairs material gaps. Only implementation-relevant research conclusions enter the Plan Part; research transcripts and unnecessary source summaries stay out.

Line counts remain safety guidance only. ChatGPT must neither pad plans nor over-compress required technical detail.

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

After all required Plan Parts are expanded, the earlier 3-operation block compactions do **not** replace the full final audit. During Pass A and Pass B, ChatGPT should group related edits into a coherent commit per bounded heavy-operation unit when practical instead of creating micro-commits for every small file edit. Pass A also treats over-compressed plans, undefined mechanisms/algorithms, missing required research, unverified repository assumptions, or avoidable implementation reasoning as planning gaps that must be repaired.

ChatGPT then:

1. optimizes every Plan Part without losing implementation intent;
2. removes avoidable decisions from Luna and adds concrete contracts/code where useful;
3. challenges every SOL assignment and keeps SOL only when stronger planning still cannot make the work safely mechanical for Luna;
4. optimizes surviving SOL work for higher-capability reasoning without unnecessary scaffolding;
5. runs a cross-artifact Consistency Gate from `MASTER_PLAN → PLAN_INDEX → Plan Parts → current repository`, repairing inconsistencies at the file that owns the information;
6. defines Implementation Batches and GOALs, marking foundational GOALs that must validate before dependent work;
7. gives every GOAL Expected Evidence that proves its intended result rather than relying only on generic "tests passed";
8. creates the final Codex handoff.

After implementation, ChatGPT runs a Convergence Check against the canonical plan and current repository. Required differences are classified as missing, partial, contradicting, or unrequested, corrected in bounded work, and checked again until required behavior converges or a real blocker/user decision remains.

Planning files are planning-safety boundaries, not automatic Codex sessions or test cycles. One GOAL may use many Plan Parts.

## 9. Active implementation model and paused GOALs

The current plan's `CODEX_HANDOFF.md` contains the only authoritative `ACTIVE_MODEL` variable: `Luna` or `SOL` (high effort implicit). GOAL assignments are recommendations, not runtime-model proof; all other artifacts point to this variable instead of duplicating it.

After selecting a model in the app, explicitly state `Luna selecionado` or `SOL selecionado` in your **current message**. Only that current message authorizes writing the field. The agent must never infer a model from chat context or memory, and previous selection messages **cannot be replayed** to update it in later turns (including after `continue`). If no new explicit selection is given, the variable stays unchanged even if earlier messages suggest another model. Sending the message alone does not change the app's model selector.

A GOAL may pause, but the agent cannot resume it autonomously. Before a planned pause, it asks if you want to continue/change models. A selection message does not resume a paused GOAL: you may still need to **manually resume/continue** it. If writing is blocked during the pause, the agent must report that no update was made and request a **fresh explicit selection** after resumption; it cannot apply the old message later.

## 10. Cycle Closure and cleanup

A successful Convergence Check makes the cycle eligible for cleanup; it does not start
cleanup.

ChatGPT performs Cleanup Preparation as planning work. Substantial preparation obeys the
same Context Safety, Manual/Continuous Mode, checkpoint, coherent-commit and handoff rules
as other heavy planning. ChatGPT resolves architecture precedence, deletion/preservation
rules, local build/generated cleanup, findings format and clean validation, then prepares
`CODEX_CLEAN_HANDOFF.md` specifically so Luna can execute it mechanically.

Once that handoff is ready, ChatGPT stops. You explicitly start the Cleanup GOAL when you
want it to run.

The Cleanup GOAL is one continuous Luna mission. It reconciles permanent architecture,
checks implementation against the final plan, removes completed planning/history and
classified obsolete/build/generated residue, rebuilds from a clean state, removes its own
temporary handoff, and leaves `CLEANUP_FINDINGS.md` containing only architecture
reconciliations and real unresolved implementation divergences.

The next planning cycle reads those findings early, absorbs/resolves/rejects/defers them,
and does not keep old findings as an archive.

The intended loop is:

`Plan -> Implement -> Converge -> Clean -> feed findings into the next Plan`

## 11. Storage

GitHub is recommended because planning can be persisted directly in a dedicated plan folder and resumed from another chat.

Library is a fallback. It may request repeated write approvals and is therefore less convenient for long micro-expansion workflows.

The current working GitHub repository remains authoritative for implementation facts regardless of planning backend.
