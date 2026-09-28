# ChatGPT Planning Protocol

This document is the operational entry point for using a normal ChatGPT conversation as the planning layer before Codex implementation.

## What to give ChatGPT

A planning session should identify:

1. this workflow repository;
2. the target source repository;
3. the plan, requirement, issue, or existing planning document to refine;
4. any known canonical documents;
5. whether ChatGPT may write the resulting plan files directly to GitHub.

A minimal instruction can be:

```text
Read the AN-chatNcodex-WorkFlow manual.
Use it to prepare implementation planning for <target repository>.
The source plan is <plan/file/issue>.
Inspect the current repository before finalizing details.
Create the plan files one at a time and stop after each complete file if the next one may be large.
These planning subdivisions do not represent separate Codex agents.
```

## ChatGPT operating sequence

### Step 1 — Load the workflow manual

Read:

- `README.md`
- `docs/WORKFLOW.md`
- this file
- the relevant templates

Do not assume the workflow from memory when the repository can be read directly.

### Step 2 — Locate the source plan

The source may be:

- one existing plan file;
- several historical plan files;
- a GitHub issue;
- a user request;
- a previous implementation audit;
- a mixture of these.

Identify which source is newest and canonical.

Do not treat every historical document as equally authoritative.

### Step 3 — Inspect current code before optimizing the plan

Before converting a plan into implementation instructions:

- find the affected systems;
- inspect current interfaces and ownership;
- identify existing replacements for legacy code;
- inspect tests/build files when relevant;
- verify exact paths and symbols used in the plan.

If current code contradicts an old plan, adapt the plan.

Do not force the repository back to an obsolete design merely to match historical documentation.

### Step 4 — Create the plan index

Before writing detailed implementation parts, define the intended decomposition in a plan index.

The index should contain:

- objective;
- authoritative inputs;
- precedence notes;
- macroblocks;
- ordered plan files;
- dependencies;
- implementation mode;
- validation strategy.

At this point, file boundaries are provisional and may be split further during detailed planning.

### Step 5 — Optimize one plan file at a time

For each planned file:

1. inspect all relevant code needed for that file;
2. resolve architectural questions that can be resolved from evidence;
3. write implementation-level instructions;
4. define tests and completion criteria;
5. save the complete file;
6. update the index if the decomposition changed.

The planning file should leave little design work for Codex.

### Step 6 — Split again when necessary

If a planned file becomes too large, split it into sequential subparts.

Example:

```text
04-renderer.md
```

may become:

```text
04A-renderer-contracts.md
04B-renderer-resource-lifetime.md
04C-renderer-frame-path.md
04D-renderer-validation.md
```

Splitting is valid even after the original index was created.

Update the index to reflect the new structure.

### Step 7 — Respect the response boundary

When working interactively, prefer this behavior:

- finish exactly one substantial plan file;
- write it to GitHub;
- report completion;
- identify the next file;
- stop.

The user can then ask ChatGPT to continue.

This prevents a long planning run from timing out while preserving a clean persisted result.

Small files may be completed together when doing so does not reduce reasoning quality.

### Step 8 — Final planning audit

Before handing work to Codex, verify:

- every part has a clear objective;
- dependencies are correct;
- no part relies on an obsolete plan;
- verified paths and symbols still exist;
- overlapping work is intentional;
- tests cover integration boundaries;
- the final repository state is described;
- unresolved questions are explicitly marked.

If an unresolved question can be answered by inspecting the repository, inspect it instead of passing the question to Codex.

### Step 9 — Prepare the Codex handoff

The Codex handoff should specify:

- target repository;
- base branch or commit;
- plan index;
- ordered files to read;
- whether implementation should be one continuous run;
- required validation;
- how to report deviations.

Codex should not need to reconstruct the high-level design from scattered conversation history.

## Planning quality rules

### Use evidence

Prefer:

```text
src/world/state.rs currently owns WorldState and exposes apply_delta().
Extend this existing ownership path...
```

over:

```text
Create a world-state manager somewhere appropriate.
```

### Separate facts from intended changes

Use explicit language:

- "Current repository:" for observed facts.
- "Required implementation:" for intended changes.
- "Historical plan:" when citing old design information.

### Avoid premature code generation

Planning may include:

- signatures;
- schemas;
- pseudocode;
- state machines;
- data contracts;
- algorithms.

Do not fill the plan with large speculative production-code dumps when the implementation agent can write the code more reliably against the live repository.

### Do the hard reasoning during planning

The planning stage should decide:

- ownership;
- boundaries;
- sequence;
- compatibility;
- invariants;
- validation.

Do not intentionally leave difficult architectural decisions to Codex when ChatGPT has enough repository evidence to resolve them first.

## Interactive continuation protocol

At the end of a planning turn, use a compact status such as:

```text
Completed: 03B-world-storage.md
Index updated: yes
Next: 03C-world-delta-application.md
```

Do not start the next large file in the same response merely to show progress.

## When the source plan is already detailed

A detailed plan still requires repository verification.

The optimization task is then to:

1. validate each assumption against current code;
2. remove stale design;
3. make paths/symbols concrete;
4. split overly large implementation units;
5. add missing validation and handoff details.

The result should be more executable than the source plan, not merely reformatted.
