# Chat Handoff

This is an operational checkpoint, not a conversation transcript.

## Project

Working repository: <owner/repository>
Working base: <branch/ref>
Storage mode: <LIBRARY | GITHUB>
Planning root: <location>
Workflow manual: https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

## Current phase

Phase: <phase>
Context Safety at handoff: <CAUTION | HANDOFF | planned boundary>

## Last completed work

- <artifact/action>

## Next safe action

- <next action>

Do not begin a different large operation before reconstructing state and verifying prerequisites.

## Files to read first

1. PROJECT.md
2. MASTER_PLAN.md
3. PLAN_INDEX.md
4. <specific plan files needed next>

Do not load every expanded plan file unless the next operation requires it.

## Recent operational decisions

Record only decisions not yet obvious from canonical files.

- <decision>

## Decomposition / index changes

- <change>

## Blockers or user decisions pending

- <item>

## Repository facts to re-check

Do not treat these notes as current evidence. Re-read the relevant live source.

- <area/path>

## Continuation prompt output

When the user requests this handoff or Context Safety triggers it, also produce a concrete continuation prompt from `templates/CHAT_CONTINUATION_PROMPT.txt`.

Fill every field with current values: repository/base, storage/root, phase, last completed work, next action, and exact files to read first.

The continuation prompt must be the final element of the chat response, inside a plain-text copyable code block, with no explanation after it.

The successor chat must read the Project Instructions and canonical workflow, reconstruct the state above, and verify relevant implementation facts against the current working GitHub repository before continuing.
