# Workflow

This document defines the canonical workflow for converting a development request or large plan into implementation-ready files for Codex.

## 1. Principles

### 1.1 Inspect before planning

Do not finalize implementation details from the plan alone.

Before producing implementation-ready instructions, ChatGPT should inspect the current target repository and verify:

- current architecture;
- relevant source files;
- existing abstractions and naming;
- tests and build system;
- recently introduced replacements for older systems;
- whether the plan contains assumptions that are no longer true.

A plan describes intent. The repository describes the current implementation reality.

### 1.2 Planning should remove implementation ambiguity

The purpose of the planning stage is not merely to summarize work.

The planning stage should resolve as much as possible before Codex starts:

- what must change;
- where it must change;
- what must remain unchanged;
- dependencies between changes;
- interfaces and data flow;
- edge cases;
- tests;
- validation criteria;
- migration or compatibility requirements.

Codex should primarily implement, test, and validate.

### 1.3 Split planning for reliability, not because implementation is separate

A large plan may be divided into multiple files because a single ChatGPT response would become too large, slow, or unreliable.

This does not imply separate Codex agents or separate implementation sessions.

Several planning files may describe one continuous implementation pass.

### 1.4 Preserve ordering and dependencies

Every plan part must make its place in the sequence explicit.

A part should declare:

- prerequisites;
- what it produces;
- which later parts depend on it;
- whether it may be implemented independently.

## 2. Source precedence

When sources disagree, apply this precedence:

1. current repository code and active architecture;
2. newest canonical or consolidated plan;
3. newer implementation plans and macroblocks;
4. historical plans and notes.

Older plans may be used to recover details only when those details are still compatible with the current system.

Never resurrect a superseded architecture merely because it is documented more thoroughly in an older file.

## 3. Planning phases

### Phase A — Understand the requested outcome

Extract:

- desired behavior;
- explicit constraints;
- non-goals;
- compatibility requirements;
- expected user-visible result;
- expected internal architecture result.

Do not decompose immediately if the scope is still semantically unclear.

### Phase B — Inspect the target repository

Inspect the code that actually participates in the requested change.

Prefer targeted inspection over reading the entire repository.

Look for:

- entry points;
- public interfaces;
- state ownership;
- data flow;
- persistence;
- rendering or UI paths;
- network boundaries;
- tests;
- configuration;
- build scripts;
- nearby TODOs or partially completed replacements.

Record discoveries that invalidate or refine the original plan.

### Phase C — Reconcile plan and repository

Before splitting work, decide:

- which plan assumptions remain valid;
- which are obsolete;
- which details must be adapted to the current code;
- which architectural decisions are already implemented;
- whether new prerequisites are required.

The implementation plan must describe the repository that exists now, not the repository that existed when an old plan was written.

### Phase D — Build macroblocks

Group the implementation into dependency-oriented macroblocks.

A macroblock should represent a meaningful implementation objective such as:

- introduce a core interface;
- migrate one subsystem;
- add persistence;
- add a renderer path;
- integrate the feature;
- validate and remove compatibility code.

Do not split merely by file count.

### Phase E — Split macroblocks into plan parts

Split a macroblock when one of these becomes true:

- it contains multiple independently reasoned implementation objectives;
- the instructions require too much repository context for one reliable ChatGPT response;
- the validation matrix becomes too large;
- the part spans unrelated subsystems;
- completing the planning response risks truncation or timeout;
- a clean dependency boundary exists.

Keep a macroblock together when splitting would force repeated context or produce artificial fragments.

## 4. Plan-part sizing

There is no fixed line-count limit.

A good plan part should be small enough that ChatGPT can fully reason about it and large enough that Codex receives a coherent implementation unit.

Prefer one primary objective per plan part.

Examples:

```text
03A-world-state-contract.md
03B-world-state-storage.md
03C-world-state-delta-application.md
03D-world-state-validation.md
```

These may all belong to macroblock 03 and still be implemented in a single Codex run.

## 5. Required content of every implementation plan part

Each plan file should contain the following sections when applicable.

### Identity

- plan ID;
- title;
- macroblock;
- sequence position;
- status.

### Objective

State exactly what must be true when the part is complete.

### Why this part exists

Explain the architectural purpose and why it is separated from adjacent work.

### Current repository evidence

List the relevant current files, types, functions, systems, or behavior observed during planning.

Do not include guessed paths as facts.

### Decisions already made

Record decisions Codex should treat as fixed unless implementation evidence proves they are impossible.

### Scope

Specify what is included.

### Non-scope

Specify what must not be redesigned or implemented in this part.

### Dependencies

List earlier plan parts or repository prerequisites.

### Implementation instructions

Describe concrete implementation work.

Use:

- exact file paths when verified;
- exact symbols when verified;
- expected new abstractions;
- state ownership;
- call/data flow;
- invariants;
- compatibility behavior;
- error handling;
- cleanup requirements.

Avoid vague instructions such as "refactor as needed."

### Tests and validation

Define:

- unit tests;
- integration tests;
- build commands;
- runtime checks;
- regression checks;
- expected failure cases.

### Definition of done

Use observable completion criteria.

### Handoff to the next part

Explain what state the repository should be in when the next part begins.

## 6. ChatGPT response boundary rule

When planning is being produced interactively and the next part is likely to become too large:

1. finish the current plan file completely;
2. save it to GitHub;
3. stop at that clean boundary;
4. report which file was completed;
5. report which file should be planned next.

Do not partially draft several files just to cover more scope.

A complete smaller plan is preferable to several incomplete ones.

## 7. Codex handoff

Before Codex implementation begins, ChatGPT should be able to provide:

- the ordered list of plan files;
- the target repository and branch;
- the implementation scope;
- whether all plan files belong to one continuous run;
- validation expectations;
- known risks or unresolved questions.

Codex should read all required prerequisite plan parts before implementing dependent work.

## 8. Codex implementation behavior

Codex should:

1. inspect the repository again before editing;
2. verify that plan assumptions still match HEAD;
3. implement in dependency order;
4. keep changes scoped to the plan;
5. run relevant tests after meaningful milestones;
6. fix regressions introduced by the implementation;
7. document material deviations from the plan;
8. leave the repository in a coherent state.

Codex should not:

- silently revive superseded architecture;
- rewrite unrelated subsystems;
- skip validation because the plan was detailed;
- treat every planning file as a separate agent assignment.

## 9. Review loop

After implementation, ChatGPT may review:

- diff;
- changed files;
- tests;
- logs;
- unresolved TODOs;
- deviations from the plan.

The review should classify findings as:

- implementation defect;
- plan defect;
- newly discovered repository constraint;
- optional improvement;
- follow-up work.

If a follow-up plan is required, it should be created from the updated repository state rather than by blindly extending the old plan.

## 10. Workflow summary

```text
request
  -> inspect repository
  -> reconcile sources
  -> define macroblocks
  -> split into reliable plan parts
  -> finish each plan part completely
  -> Codex reads ordered parts
  -> implement in one continuous run when appropriate
  -> build/test/validate
  -> ChatGPT reviews current result
  -> next plan starts from new repository state
```
