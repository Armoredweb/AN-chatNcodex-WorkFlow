# Storage, Backup, and Recovery

The workflow supports two persistent planning backends: LIBRARY and GITHUB.

The storage choice changes where planning artifacts live, not where code facts come from. Current implementation facts always come from the working GitHub repository.

## Common project layout

A persistent planning root should converge on:

    PROJECT.md
    MASTER_PLAN.md
    PLAN_INDEX.md
    backup/
      MASTER_PLAN.original.md
    plan/
      001-....md
      002-....md
      ...
    handoff/
      CHAT_HANDOFF.md
    CODEX_HANDOFF.md

MASTER_PLAN.md may reference additional compact master-plan subfiles when required.

## PROJECT.md

PROJECT.md is the durable entry point.

A successor chat should be able to find from it:

- canonical workflow repository;
- working repository and base;
- storage mode;
- planning root;
- workflow phase;
- master plan;
- plan index;
- handoff file;
- final handoff when it exists.

Do not turn PROJECT.md into a transcript.

## LIBRARY mode

Use a dedicated persistent Library folder after the user approves the master plan for implementation planning.

Before writing to Library, warn the user that a permission request may appear.

If the native mobile app cannot show that request, the workflow should be performed in a web browser.

Use normal temporary chat workspace before the implementation-planning gate when persistence is not yet needed.

At the gate:

1. create the persistent project folder;
2. save the approved MASTER_PLAN.md;
3. save backup/MASTER_PLAN.original.md;
4. create PROJECT.md and PLAN_INDEX.md as decomposition begins.

Library mode is useful when unfinished plans should not appear as commits in the working repository.

At completion, obtain user authorization and publish the completed planning package to a dedicated plan folder in the working repository before Codex execution.

## GITHUB mode

Use a dedicated folder inside the working repository.

Inspect existing conventions first.

If a repository already has docs/plans/, planning/, plans/, or another clear canonical location, create a new subfolder there.

Otherwise default to:

    plans/<plan-name>/

Never place independent plan artifacts directly into a shared parent directory without a plan-specific folder.

Explain that planning writes may create incremental commits.

Obtain scoped authorization for ChatGPT to maintain files inside the dedicated plan folder for the workflow.

Once authorized, do not interrupt expansion for permission on every routine write inside that folder.

Do not treat that as authorization to modify application source code or unrelated documentation.

## Backup semantics

backup/MASTER_PLAN.original.md is a semantic checkpoint, not merely a Git backup.

It records the master plan as approved when the workflow crossed into implementation planning.

Do not overwrite it during normal refinement.

If material discoveries force a structural master-plan change later:

- update the working MASTER_PLAN.md;
- preserve the original baseline;
- record the material change in PLAN_INDEX.md and/or CHAT_HANDOFF.md.

Git history remains useful, but it does not replace the explicit baseline.

## Handoff checkpoint

handoff/CHAT_HANDOFF.md should be updated at meaningful recovery points and whenever Context Safety reaches HANDOFF.

In GITHUB mode it can be updated frequently because persistence is cheap.

In LIBRARY mode balance checkpoint frequency with permission prompts. Always update before a planned handoff.

A handoff file is a concise operational state, not a copy of the conversation.

## Recovery order

A successor chat should:

1. read Project instructions;
2. read the canonical workflow;
3. read PROJECT.md;
4. read CHAT_HANDOFF.md;
5. read MASTER_PLAN.md;
6. read PLAN_INDEX.md;
7. inventory the plan directory;
8. read only the plan files needed for the next action;
9. re-inspect relevant current source code.

Do not eagerly load every expanded plan file into context.

## Storage failure

If persistent storage cannot be written:

- do not pretend persistence succeeded;
- preserve the current bounded result in the available workspace if possible;
- tell the user what was not persisted;
- do not continue into a phase that depends on the missing durable state.
