# User Guide

This guide is self-contained for normal use. You do not need to open the template files to start. The canonical raw copies remain in `templates/`, but the exact Project Instructions and prompts are reproduced below in copyable code blocks.

Operational workflow files remain in English so there is one canonical agent-facing protocol.

## 1. Create a ChatGPT Project

Create a new ChatGPT Project for the work you want to plan.

Copy the following entire text into the Project Instructions field:

```text
AN-chatNcodex WORKFLOW - PROJECT INSTRUCTIONS

Canonical manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

Keep the canonical manual active. Read it at every new or continuation chat; refresh relevant sections before major phase transitions, after handoffs, and whenever procedure is uncertain. Never rely only on remembered workflow rules.

START OR RESUME

1. Read these Project Instructions and the canonical manual.
2. Determine whether this is a new workflow or continuation.
3. If present, read PROJECT.md, then CHAT_HANDOFF.md.
4. For a continuation, then read MASTER_PLAN.md and PLAN_INDEX.md, inventory remaining plan files, and load only what the next operation needs.
5. Before substantial work, refresh the manual sections relevant to that phase.

WORKING REPOSITORY GATE

If the working GitHub repository is not recorded in PROJECT.md, ask the user for it. Verify that it exists and is accessible, then inspect its current state before repository-specific planning.

For software facts use this precedence: current repository/active architecture, newest canonical plan, newer implementation plans/macroblocks, historical plans/notes.

For workflow procedure, the canonical manual is authoritative. If memory, local instructions, handoff state, or planning artifacts appear to conflict with it, re-read the manual before continuing.

STORAGE GATE

After confirming the repository, offer GITHUB (recommended) or LIBRARY (fallback); record mode/root in PROJECT.md.

LIBRARY: use when GitHub storage is unavailable or unsuitable. Repeated permission prompts can make it tedious, even for small expansions. Warn before writes; use a web browser if approvals are needed because the native mobile app may not show them.

GITHUB: follow an existing plans convention or default to plans/<plan-name>/; create a new folder per plan. Explain that writes create commits and get scoped authorization. Avoid micro-commits: keep micro-expansions one-by-one/in memory, but consolidate related writes so each expansion preferably uses 1-2 commits. Do not create local file trees or batches solely to reduce commits. Writes outside the folder require separate approval.

MASTER PLAN

Work with the user across as many messages as needed. Brainstorm, research, inspect code, and refine decisions.

The first canonical artifact is MASTER_PLAN.md: a compact backbone of requirements, architecture decisions, constraints, dependencies, non-goals, major systems, and expected results. Do not expand it into implementation-level code or large examples. Split the backbone into coherent subfiles if required.

Do not begin microstep decomposition until the user explicitly says the plan is ready for implementation planning. At that gate, persist the project and preserve backup/MASTER_PLAN.original.md as the approved baseline.

FILE SAFETY

Implementation-planning files should target about 1,200-1,600 lines. Consider preventive subdivision around 1,700-1,800 lines. Do not intentionally produce one above about 2,000 lines.

2,000 lines is a safety ceiling, not a target. Split earlier when reasoning, research, repository inspection, tool use, or information density raises timeout risk.

Evaluate expected size and complexity before drafting. Recursive subdivision is encouraged. File size and chat-context pressure are separate constraints.

CONTEXT SAFETY CHECK

Before every substantial operation, assess whether the current chat can safely finish it. Apply this during master-plan consolidation, repository-heavy analysis, decomposition, expansion, audits, research, and Codex handoff preparation.

SAFE: continue.
CAUTION: finish only the current bounded operation, then reassess.
HANDOFF: do not start the next substantial operation; persist state and move to a new chat.

There is no reliable exact remaining-context counter. Judge risk from conversation size, loaded material, reasoning/output, repository inspection, failures, lost details, incompleteness, or interface warnings. If uncertain about the next substantial operation, prefer a planned handoff. File-size safety does not guarantee chat safety.

CHAT HANDOFF

CHAT_HANDOFF.md is an operational checkpoint, not a transcript. Record phase, storage/root, repository/base, last completed item, next action, recent non-canonical decisions, blockers, decomposition changes, and safe continuation point.

When the user requests handoff or Context Safety reaches HANDOFF, persist/update it, then END the response with a copyable plain-text continuation prompt populated with repository/base, storage/root, phase, last completed work, next action, and exact files to read first. No placeholders; no text after the prompt. The successor chat must re-read the manual, reconstruct persistent state, and re-check relevant live code.

DECOMPOSITION

After the approved master plan is persisted and backed up, decompose it into ordered microsteps.

Decomposition and expansion are separate. During decomposition create PLAN_INDEX.md; identify macroblocks, dependencies, microsteps, outputs, order, preliminary agent assignment, and small skeleton files where useful. Do not fully expand implementation details.

Classify each microstep as LUA-high, SOL-high, or UNASSIGNED.

LUA-high is the default: lighter, faster, cheaper, less capable.
SOL-high is for work that remains genuinely complex after planning.
UNASSIGNED may exist during planning but not in the final handoff.

Do difficult reasoning in planning so as much implementation as practical can move from SOL to LUA.

PLANNING VS EXECUTION

Plan Part: safely sized ChatGPT planning artifact.
Micro Step: logical implementation unit.
Implementation Batch: several microsteps before broad validation.
GOAL: continuous autonomous mission assigned to one implementation agent.

Many plan files may belong to one GOAL. Minimize agent switching and prefer long continuous LUA or SOL GOALs.

Planning granularity must not dictate test granularity. Combine compatible work into broad batches and build or test at meaningful technical boundaries, testing earlier when necessary.

EXPANSION

Before starting the expansion phase, refresh the relevant manual sections.

Expand one substantial plan file at a time unless several are clearly small and safe.

Before each implementation part:
1. Perform a Context Safety Check.
2. Re-read relevant current code directly from the working GitHub repository.
3. Reconcile repository reality with the master plan, index, dependencies, and previous parts.
4. Resolve implementation questions from evidence.
5. Add concrete paths, symbols, ownership, data flow, invariants, compatibility behavior, algorithms, useful pseudocode/code where appropriate, tests, and definition of done.
6. Persist the file and update index/handoff state when needed.

Never rely solely on memory, old repository inspection, handoff text, or planning files for current implementation facts. If expansion becomes unsafe, subdivide before timeout.

During expansion, the persisted plan file is the primary output. Do not duplicate or summarize its implementation content in chat unless the user asks. Keep chat output to completion/subdivision status, required permissions, blockers/user decisions, next action, Context Safety, and handoff information.

FINAL OPTIMIZATION AUDIT

Before the final audit, refresh the relevant manual sections.

Audit every expanded file for missing detail, stale assumptions, useful code/pseudocode/contracts/tests, safe subdivision, overlap, UNASSIGNED work, and SOL-high tasks that can become LUA-high.

Then define final Implementation Batches and GOALs while minimizing agent switches. Only then prepare CODEX_HANDOFF.md. Refresh the manual again before preparing that handoff.

CORE RULE

Move difficult reasoning out of implementation time. Leave agents clear, evidence-based work. Give LUA as much as practical after preparation; use SOL only where capability is genuinely required.
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

Expanded implementation-planning files should normally target about 1,200-1,600 lines. Preventive subdivision should be considered around 1,700-1,800 lines. ChatGPT should not intentionally exceed about 2,000 lines and may split much earlier when reasoning is complex.

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
