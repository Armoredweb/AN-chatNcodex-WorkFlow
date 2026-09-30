# User Guide

This guide is self-contained for normal use. You do not need to open the template files to start. The canonical raw copies remain in `templates/`, but the exact Project Instructions and prompts are reproduced below in copyable code blocks.

Operational workflow files remain in English so there is one canonical agent-facing protocol.

## Responsible use and intent

This workflow is not a way to bypass ChatGPT, Codex, Work, account, rate, usage, safety, or platform limits. Checkpoints, multiple chats, persistent planning, and continuous mode are used to divide legitimate software-planning work into bounded pieces and to preserve state safely.

The goal is to use ChatGPT efficiently for difficult architecture and planning, then reserve Codex/Work resources for implementation or autonomous execution that actually needs them. Product limits, safeguards, authorization boundaries, and platform rules always take precedence.

Persistent planning also makes the workload explicit: another reviewer can see that the repeated operations are bounded software-planning tasks rather than an attempt to evade limits.

## 1. Create a ChatGPT Project

Create a new ChatGPT Project for the work you want to plan.

Copy the following entire text into the Project Instructions field:

```text
AN-chatNcodex WORKFLOW - PROJECT INSTRUCTIONS

Canonical manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

Keep the canonical manual active. Read it at every new or continuation chat; refresh relevant sections before major phase changes, after handoffs, and whenever procedure is uncertain. Do not rely only on remembered workflow rules.

RESPONSIBLE USE

This workflow is for legitimate software planning and resource-efficient orchestration. It is not intended to bypass ChatGPT, Codex, Work, account, rate, usage, safety, or platform limits. Respect all product limits, safeguards, authorization boundaries, and platform rules.

Checkpointing, handoffs, multiple chats, and continuous mode exist to divide work safely and preserve planning state, not to evade enforcement or obtain capacity beyond what the product permits. Use ChatGPT for heavy planning so Codex/Work resources can be reserved for implementation or autonomous work that actually needs them. Keep persistent artifacts clear enough that the workload is visibly bounded software-planning work.

START OR RESUME

1. Read these instructions and the canonical manual.
2. Determine whether this is new work or a continuation.
3. If present, read PROJECT.md and CHAT_HANDOFF.md, then MASTER_PLAN.md and PLAN_INDEX.md.
4. Inventory remaining plan files, but load only what the next operation needs.
5. Before substantial work, refresh the relevant manual sections.

WORKING REPOSITORY

If PROJECT.md does not identify the working GitHub repository, ask for it. Verify access and current state before repository-specific planning.

Software facts: current repository/active architecture > newest canonical plan > newer implementation plans/macroblocks > historical notes. Workflow procedure: canonical manual.

STORAGE

After confirming the repository, offer GITHUB (recommended) or LIBRARY (fallback) and record mode/root in PROJECT.md.

LIBRARY may require repeated approvals. GITHUB should use an existing plans convention or plans/<plan-name>/ with scoped authorization. Avoid micro-commits where practical, but do not change planning granularity or create artificial local batching just to reduce commits. Writes outside the authorized planning folder require separate approval.

MASTER PLAN

Brainstorm, research, inspect code, and refine decisions as needed. MASTER_PLAN.md is a compact backbone of requirements, architecture, constraints, dependencies, non-goals, major systems, and expected results. Do not turn it into a giant implementation document. Do not begin decomposition until the user explicitly approves implementation planning. At that gate, persist the project and preserve backup/MASTER_PLAN.original.md.

FILE SAFETY AND TOKEN EFFICIENCY

Line counts are safety references, not quotas, minimums, or goals. A complete subplan may be very small; that is preferable when the solution is simple.

Never add filler, repeated context, tutorials, generic rationale, or prose merely to approach a line count. For larger files, about 1,200-1,600 lines is a normal working range. A coherent file around 1,600-1,700 lines does not need rewriting solely for that small overage. Consider subdivision around 1,700-1,800 lines and do not intentionally exceed about 2,000. Split earlier when complexity or context risk warrants it.

Optimize for implementation readiness per token. Do the difficult reasoning in ChatGPT, then write only what the implementation agent needs: verified paths/symbols, concrete contracts, state/data flow, algorithms, constraints, concise pseudocode/code, tests, and definition of done. Explain why only when needed to preserve a constraint, compatibility rule, failure mode, or non-obvious architectural decision.

CONTEXT SAFETY

Before every substantial operation use SAFE / CAUTION / HANDOFF.

SAFE: continue.
CAUTION: finish only the current bounded operation; do not automatically start another substantial one.
HANDOFF: persist state and move to a successor chat before more substantial work.

There is no reliable exact remaining-context counter. Judge risk from conversation size, loaded material, reasoning/output, repository work, failures, lost details, incompleteness, or interface warnings.

CONTINUOUS EXPANSION MODE

Enable only when the user requests automatic continuation across checkpoints.

After each bounded heavy operation, persist its checkpoint and continue only if Context Safety remains SAFE and no user decision is required.

Hard cap: 4 heavy operations per chat. Complete operation 4, persist state, update CHAT_HANDOFF.md, and return a populated handoff prompt. Never start operation 5 in that chat.

A heavy operation is a substantial top-level task consuming meaningful context/reasoning/research/repository/tool/artifact work. If it independently warrants a Context Safety Check, normally count 1 unit. Examples: substantial expansion, structural subdivision, major decomposition or MASTER_PLAN consolidation, research/repository-heavy reconciliation, substantial audit, Codex-handoff preparation, or large recovery/migration.

Count the parent operation once; its required reads, verification, reasoning, persistence, and routine PLAN_INDEX.md / CHAT_HANDOFF.md synchronization are included. The counter is per chat; "continue" does not reset it. Successor chat starts at 0/4. Safety/degradation may force earlier handoff.

CHAT HANDOFF

CHAT_HANDOFF.md records phase, storage/root, repository/base, last completed item, next action, blockers, decomposition changes, continuous-mode state, and safe continuation point.

When handoff is requested/required or continuous mode reaches 4/4, persist/update state and END the response with a populated plain-text continuation prompt. No placeholders and no text after it.

DECOMPOSITION

After the approved master plan is persisted/backed up, define ordered macroblocks/microsteps, dependencies, outputs, provisional files, and preliminary agent assignment in PLAN_INDEX.md. Decomposition and expansion are separate.

Use LUA-high by default, SOL-high only where work remains genuinely complex after preparation, and UNASSIGNED only temporarily. No UNASSIGNED may remain in the final handoff.

PLANNING VS EXECUTION

Plan Part = safe planning artifact. Micro Step = logical implementation unit. Implementation Batch = compatible work before broad validation. GOAL = continuous autonomous mission for one implementation agent. Many plan files may belong to one GOAL; minimize agent switching.

EXPANSION

Before each substantial part:
1. Perform Context Safety Check.
2. Re-read relevant current code.
3. Reconcile repository reality with master plan, index, dependencies, and prior interfaces.
4. Resolve implementation questions from evidence.
5. Write the smallest implementation-ready plan: direct instructions, required contracts/code/tests, no filler.
6. Persist result and update index/handoff as needed.

Never rely solely on memory, old repository inspection, handoff text, or planning files for current implementation facts. The persisted plan is the primary output; do not duplicate its detail in chat unless asked.

FINAL AUDIT

Refresh the manual, then audit expanded files for missing implementation detail, stale assumptions, unsafe size, overlap/gaps, UNASSIGNED work, and SOL-high work that can become LUA-high. Remove unnecessary prose as well as missing detail. Define final Implementation Batches and GOALs, then prepare CODEX_HANDOFF.md.

CORE RULE

Spend reasoning to simplify implementation. Deliver the minimum complete, evidence-based plan the implementation agent needs; do not confuse heavy thinking with large output.

```

The Project Instructions are intentionally plain text and must stay within ChatGPT's 8,000-character Project Instructions limit.

## 2. Start the first chat

Open a new chat inside that ChatGPT Project and send:

```text
Read the instructions configured for this ChatGPT Project first.

Then read the canonical workflow manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

Keep that manual as an active reference throughout the workflow and refresh the relevant sections before major phase transitions or whenever workflow behavior is uncertain.

Follow the manual for this project.

Determine whether this is a new workflow or an existing one with persistent planning state.

If the working GitHub repository is not already known from persistent project state, ask me for it. Verify the repository before making repository-specific planning decisions.

Do not assume current code or architecture from conversation memory. Use the working GitHub repository as the source of truth for implementation facts.

If this is a new workflow, run the required Storage Gate after the working repository has been verified.
```

ChatGPT should read the Project Instructions and this workflow repository, then determine whether the project is new or a continuation.

For a new workflow it asks for the working GitHub repository if it is not already known, verifies that repository, and then runs the Storage Gate.

The workflow repository and the working repository are different:

- workflow repository: this reusable public manual;
- working repository: the software project being planned and implemented.

## 3. Keep the manual active throughout the workflow

The manual is not only an initialization document.

ChatGPT must re-read it at every new or continuation chat and refresh the relevant sections before major phase transitions, after handoffs, and whenever there is uncertainty about workflow procedure.

This is important because a long conversation should not rely on remembered workflow rules.

The current working GitHub repository remains the source of truth for current software implementation facts.

## 4. Choose planning storage

After the working repository is verified, ChatGPT offers GITHUB or LIBRARY. GITHUB is the recommended planning backend when it is available; LIBRARY is a fallback when GitHub storage is unavailable or unsuitable.

### GitHub — recommended

Choose GitHub for normal use. It provides durable planning without repeated Library approval dialogs.

### Library — fallback

Library remains supported, but it can become tiring during long expansion work because persistent writes may trigger permission prompts repeatedly, sometimes several times around a small expansion. Use it mainly when GitHub storage is unavailable or when planning must stay outside the repository until final publication.

If Library is selected, keep the interface available to approve write requests. If the native mobile app cannot display them, use ChatGPT in a desktop or mobile web browser.

### GitHub planning folder and commits

Use the repository's existing plans/planning convention when present; otherwise use a dedicated `plans/<plan-name>/` folder.

ChatGPT inspects the repository for an existing plans/planning convention and always creates a new folder for this independent plan. If there is no better convention, the default is:

```text
plans/<plan-name>/
```

ChatGPT explains that planning writes may create commits and asks for authorization to maintain planning files inside that folder.

After that scoped authorization, routine planning writes inside the approved folder do not require a new confirmation every time. Writes outside the approved folder require separate authorization.

Micro-expansion remains the planning unit: ChatGPT may continue preparing each small expansion in memory and persisting it independently. However, it should avoid micro-commits for tiny adjustments. Related writes for one expansion should preferably be consolidated into one or two commits. Do not create a local file tree or artificial batching workflow solely to reduce commit count.

## 5. Build the master plan

Describe the full project or change across as many messages as needed.

Use brainstorming, questions, research, comparisons, repository inspection, and design discussion.

The first canonical artifact is `MASTER_PLAN.md`. It is a compact backbone containing requirements, architecture decisions, constraints, dependencies, non-goals, major systems, and expected results.

It should not become a giant implementation document or contain large production-code examples.

If necessary, ChatGPT may split the master-plan backbone into coherent subfiles while preserving a compact top-level `MASTER_PLAN.md`.

## 6. Approve the implementation-planning gate

Stay in brainstorming/refinement mode until you believe the master plan is ready.

When you explicitly approve it for implementation planning, ChatGPT persists the project, creates or updates `PROJECT.md`, preserves `backup/MASTER_PLAN.original.md`, and begins decomposition.

The backup is the approved semantic baseline.

## 7. Decomposition comes before expansion

ChatGPT first identifies macroblocks, dependencies, and ordered microsteps.

It creates `PLAN_INDEX.md` and small plan skeletons when useful.

It does not fully expand implementation details yet.

Each microstep receives an initial assignment:

- LUA-high: preferred/default;
- SOL-high: stronger and more expensive, for work that remains genuinely complex;
- UNASSIGNED: temporary while more planning evidence is needed.

No UNASSIGNED work may remain in the final handoff.

## 8. Expansion

Only after decomposition is complete does detailed expansion begin.

Normally ChatGPT expands one substantial plan file per invocation. Several clearly small files may be handled together when safe.

Before each expansion it performs a Context Safety Check and re-reads the relevant current code directly from the working GitHub repository.

Line counts are safety references, not output goals. A complete subplan may be far shorter than 1,200 lines, and that is preferable when the implementation can be specified clearly with less text. For larger files, about 1,200-1,600 lines is a normal working range. A coherent file around 1,600-1,700 lines does not need rewriting solely for that small overage; consider subdivision around 1,700-1,800 lines and do not intentionally exceed about 2,000 lines.

### Efficient expansion

Expansion is judged by implementation readiness per token, not by document size. ChatGPT should perform the difficult reasoning, then write the smallest plan that lets the implementation agent act correctly.

Prefer verified paths/symbols, direct instructions, concrete contracts, concise algorithms/pseudocode, implementation-ready code where useful, tests, and definition of done. Avoid filler, repeated context, generic tutorials, and explanations of obvious choices. Rationale belongs in the plan only when it preserves a constraint, compatibility rule, known failure mode, or non-obvious architectural decision.

A difficult problem can legitimately produce a very small subplan once the difficult decisions have been resolved.

### Continuous expansion mode

If you want ChatGPT to continue expanding without waiting for a new "continue" message after every checkpoint, explicitly enable Continuous Expansion Mode.

In this mode, ChatGPT still performs one bounded top-level operation at a time and persists a checkpoint after each one. The counter measures heavy ChatGPT work, not just expansion files: a substantial expansion, structural subdivision, major decomposition or consolidation, research/repository-heavy reconciliation, substantial audit, handoff preparation, or large recovery/migration task normally counts as one unit.

As a practical rule, if a top-level task independently warrants a Context Safety Check, it normally counts as one heavy-operation unit. Supporting reads, source verification, reasoning, persistence, and routine index/handoff synchronization are included in that unit rather than counted again.

For safety, a single chat may complete at most 4 heavy operations. After the 4th, ChatGPT must stop, persist the current state, and return a populated handoff prompt for a successor chat instead of starting a 5th. The counter resets only in the successor chat. Context Safety or signs of degradation can trigger an earlier handoff.

### Chat output during expansion

The persistent plan file is the main output.

ChatGPT should not repeat or summarize the detailed expansion in the chat unless you ask.

The chat response should normally contain only continuity information such as:

- file completed, updated, or subdivided;
- required storage permission;
- blocker or decision requiring you;
- next file/action;
- Context Safety warning;
- handoff recommendation.

## 9. Context Safety and chat changes

ChatGPT has no exact trustworthy counter for remaining conversation context.

Before substantial operations it uses:

- SAFE: continue;
- CAUTION: finish only the current bounded operation, then reassess;
- HANDOFF: do not begin the next substantial operation in this chat.

If it is uncertain whether the next large operation can finish safely, it should prefer a planned handoff.

This rule applies during master-plan consolidation, decomposition, expansion, research, final audit, and Codex handoff preparation.

## 10. Continue in a new chat

When you request a handoff, or ChatGPT determines one is required, it first updates `CHAT_HANDOFF.md`.

The same response must end with a plain-text copyable prompt already filled with the current project state. Copy that final box directly into the new chat. There must be no explanatory text after it.

The raw template is:

```text
Continue the AN-chatNcodex planning workflow from the persisted handoff.

First read the ChatGPT Project Instructions and the canonical workflow manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

Working repository:
<owner/repository>

Working base:
<branch/ref>

Planning storage:
<LIBRARY | GITHUB>

Planning root:
<path>

Current phase:
<phase>

Last completed:
<concrete artifact/action>

Next action:
<concrete next safe action>

Read first:
- <PROJECT.md path>
- <CHAT_HANDOFF.md path>
- <MASTER_PLAN.md path>
- <PLAN_INDEX.md path>
- <only additional plan files required for the next action>

Do not rely on previous-chat memory. Reconstruct state from persistent artifacts and keep the canonical manual active.

Inventory remaining planning files, but load only those needed for the next operation.

Before implementation-level decisions or another expansion, verify the relevant current source directly in the working GitHub repository.

Continue from the safe continuation point recorded in CHAT_HANDOFF.md and follow File Safety and Context Safety rules.

If CHAT_HANDOFF.md says Continuous Expansion Mode is ACTIVE, resume it automatically after reconstruction. Start this successor chat with a fresh 0/4 heavy-operation counter. Count every substantial top-level ChatGPT process according to the canonical manual, not just expansions or subdivisions, and hand off again after the 4th heavy operation or earlier if Context Safety requires it.
```

During a real handoff, ChatGPT replaces every placeholder with concrete values: repository/base, planning storage/root, phase, last completed work, next action, and exact files to read first.

The successor chat reconstructs state from persistent files instead of asking you to reproduce the previous conversation.

It should start with `PROJECT.md`, `CHAT_HANDOFF.md`, `MASTER_PLAN.md`, and `PLAN_INDEX.md`, inventory the other plan files, and load only those required for the next operation.

It must also re-read the workflow manual and re-check relevant live source code.

## 11. Final optimization audit

After all plan parts are expanded, ChatGPT audits them file by file.

It looks for missing detail, stale assumptions, useful contracts/code/pseudocode/tests, further safe subdivision, overlaps or gaps, UNASSIGNED work, and SOL-high work that can now become LUA-high.

## 12. Implementation Batches and GOALs

Planning-file count does not determine Codex execution count.

A Plan Part is a safe planning artifact. A Micro Step is a logical work unit. An Implementation Batch groups compatible work before broad validation. A GOAL is a continuous autonomous mission assigned to one implementation agent.

Many plan files may belong to one GOAL.

ChatGPT should minimize manual agent switching and prepare as much work as possible for LUA-high.

Testing should happen at meaningful technical boundaries rather than automatically after every tiny plan file.

## 13. Codex handoff

After the final audit, ChatGPT prepares `CODEX_HANDOFF.md`.

In GitHub storage mode, the planning package already lives in the working repository.

In Library mode, ChatGPT asks for authorization before publishing the completed package to a dedicated plan folder in the working repository.

Implementation agents then execute the planned GOALs.

## Canonical raw templates

The embedded copies above are the normal user path. Raw canonical copies are also available at:

- `templates/PROJECT_INSTRUCTIONS.txt`
- `templates/START_PROMPT.txt`
- `templates/CHAT_CONTINUATION_PROMPT.txt`

When these templates change, the embedded copies in both user guides must be updated to remain identical.

Canonical manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git
