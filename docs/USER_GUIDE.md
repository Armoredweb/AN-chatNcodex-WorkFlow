# User Guide

This is the human-facing guide for starting and operating the AN-chatNcodex workflow.

All operational templates and agent-facing documents remain in English. A Portuguese version of this guide is available at USER_GUIDE_PT-BR.md.

## 1. Create a ChatGPT Project

Create a new ChatGPT Project for the work you want to plan.

Copy the contents of templates/PROJECT_INSTRUCTIONS.md into the Project instructions area.

Those instructions are generic. They point ChatGPT to the public manual and define the minimum behavior required even if a future chat starts with little or no conversational context.

## 2. Start the first chat

Open a new chat inside the Project and paste the contents of templates/START_PROMPT.md.

ChatGPT should:

1. read the local Project instructions;
2. read the canonical workflow manual;
3. determine whether this is a new workflow or a continuation;
4. ask for the working GitHub repository if it is not already known;
5. verify that repository before planning.

The workflow repository and the working repository are different:

- workflow repository: this reusable public manual;
- working repository: the software project being planned and implemented.

## 3. Choose planning storage

After the working repository is verified, ChatGPT asks you to choose one storage mode.

### Library

Choose Library when you want planning isolated from the working GitHub repository until final publication.

Planning becomes persistent in a dedicated ChatGPT Library folder after the master plan is approved for implementation planning.

Library writes may require approval. Keep the interface available to approve requests. When the approval UI is unavailable in the native mobile app, use ChatGPT in a desktop or mobile web browser.

### GitHub

Choose GitHub when incremental planning commits are acceptable and you want persistent planning without repeated Library write approvals.

ChatGPT first inspects the repository for an existing plans/planning convention. It always creates a new folder for the independent plan. If no convention exists, the default is:

    plans/<plan-name>/

Before using GitHub storage, ChatGPT should tell you that planning writes may create commits and ask for authorization to maintain files inside that plan folder.

Once that scope is authorized, routine planning writes inside the approved folder do not require a new confirmation every time. Writes outside the approved folder require separate authorization.

## 4. Build the master plan

Now describe the full project or change.

You can do this across many messages. Use brainstorming, questions, research, comparisons, repository inspection, and design discussion as needed.

ChatGPT creates MASTER_PLAN.md only after enough decisions exist. The master plan is the compact backbone of the project:

- requirements;
- architecture decisions;
- constraints;
- dependencies;
- non-goals;
- important subsystems;
- expected results.

It should not be a giant implementation document. It should avoid large code listings and detailed implementation expansion.

If the backbone itself is too large, ChatGPT may split it into coherent master-plan subfiles while preserving a compact top-level MASTER_PLAN.md.

## 5. Approve the implementation-planning gate

Stay in brainstorming/refinement mode until you believe the master plan is ready.

When you explicitly say it is ready for implementation planning, ChatGPT crosses the gate.

At that point it:

1. persists the project in the selected storage;
2. creates/updates PROJECT.md;
3. preserves backup/MASTER_PLAN.original.md;
4. starts decomposition.

The original backup represents the approved baseline.

## 6. Decomposition comes before expansion

ChatGPT first breaks the complete master plan into macroblocks and microsteps.

This stage creates PLAN_INDEX.md and small plan skeletons where useful.

It does not fully expand implementation details yet.

Each microstep receives a preliminary assignment:

- LUA-high - preferred/default implementation agent;
- SOL-high - more capable and more expensive agent for genuinely difficult work;
- UNASSIGNED - temporary state while more planning evidence is needed.

No UNASSIGNED items may remain in the final implementation handoff.

## 7. Expansion

After every microstep has been identified, expansion begins.

Normally ChatGPT expands one substantial plan file per invocation. If several are obviously small and safe, they may be handled together.

Before expanding each implementation part, ChatGPT re-reads the relevant current code directly from the working GitHub repository. It must not rely only on memory, previous repository inspection, or planning text.

Expanded plans should normally target about 1,200-1,600 lines. ChatGPT should consider preventive subdivision around 1,700-1,800 lines and should not intentionally exceed about 2,000 lines. Complex reasoning may require subdivision much earlier.

If a part is too large, ChatGPT may recursively split it into A/B/C or deeper subparts.

### Chat output during expansion

The persistent plan file is the main output.

ChatGPT should not duplicate or summarize the expanded implementation content in the conversation unless you ask.

The chat response should normally contain only what you need to continue:

- completed/updated/subdivided file;
- storage permission required;
- blocker or decision requiring you;
- next file/action;
- Context Safety status when relevant;
- handoff recommendation.

This preserves context for actual planning.

## 8. Context Safety and chat changes

Long chats can eventually become unreliable. ChatGPT has no exact trustworthy counter showing how much context remains.

Before substantial work it performs a Context Safety Check:

- SAFE - continue;
- CAUTION - finish the current bounded operation, then reassess;
- HANDOFF - do not begin the next substantial operation in this chat.

If ChatGPT is uncertain whether the next large operation can finish safely, it should prefer a planned handoff.

This applies everywhere: master-plan creation, decomposition, expansion, audits, research, and final handoff preparation.

When a handoff is needed, ChatGPT writes/updates CHAT_HANDOFF.md and gives you the continuation prompt.

## 9. Start a successor chat

Open another chat in the same ChatGPT Project and paste templates/CHAT_CONTINUATION_PROMPT.md.

The new chat reconstructs state from persistent sources.

It starts with:

1. Project instructions;
2. this workflow manual;
3. PROJECT.md;
4. CHAT_HANDOFF.md;
5. MASTER_PLAN.md;
6. PLAN_INDEX.md.

It inventories remaining plan files and reads only those required for the next operation rather than loading every expanded file into context.

Relevant implementation facts are verified again against the current working GitHub repository.

## 10. Final optimization audit

After all parts are expanded, ChatGPT audits them file by file.

It looks for:

- missing implementation detail;
- stale repository assumptions;
- useful contracts, pseudocode, code, algorithms, or tests that can be prepared;
- files that still need subdivision;
- overlaps or gaps;
- UNASSIGNED work;
- SOL-high tasks that can now become LUA-high because the planning has made them simple enough.

The goal is to leave implementation agents with execution rather than architecture work.

## 11. Batches and GOALs

Planning-file count does not determine execution count.

ChatGPT groups compatible microsteps into Implementation Batches and long-running GOALs.

A GOAL is intended to be executed continuously by one agent even if it references many plan files.

Minimize manual agent switching. Prefer large coherent stretches of LUA-high work. Escalate to SOL-high only where the task still needs the stronger model after preparation.

Testing should happen at meaningful technical boundaries. Do not force a full build/test cycle after every tiny planning file.

## 12. Codex handoff

When the final audit is complete, ChatGPT prepares CODEX_HANDOFF.md.

In GitHub storage mode the complete plan already lives in the working repository.

In Library mode, ChatGPT asks for authorization before publishing the completed planning package to the appropriate plan folder in the working repository.

The implementation agents then execute the GOALs in the planned order.

## Prompts

First chat: templates/START_PROMPT.md

Successor chat: templates/CHAT_CONTINUATION_PROMPT.md

Canonical manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git
