# AN-chatNcodex-WorkFlow

A practical workflow for turning a high-level development plan into implementation-ready work for Codex using:

- ChatGPT (normal chat) for analysis, planning, decomposition, and review
- GitHub as the persistent source of truth and handoff layer
- Codex for repository implementation, testing, and validation

## Goal

The purpose of this repository is to make a normal ChatGPT conversation capable of taking a large plan, checking it against the current repository, and converting it into a sequence of small, implementation-ready plan files that Codex can execute with minimal additional design work.

The workflow is designed for projects where:

- the original plan may be too large for a single ChatGPT response;
- implementation should remain in one continuous Codex execution even when planning is split into several files;
- current source code has precedence over stale assumptions;
- old plans may contain useful details but may also contain superseded decisions;
- planning should do as much of the reasoning as possible before implementation begins.

## Core flow

```text
Idea / requirement
      |
      v
ChatGPT planning
      |
      +--> inspect current GitHub repository
      +--> reconcile current architecture and plans
      +--> decompose work
      |
      v
Ordered implementation plan files
      |
      v
Codex implementation
      |
      +--> edit code
      +--> build
      +--> test
      +--> validate
      |
      v
GitHub result / PR / commit
      |
      v
ChatGPT review and next plan
```

## Roles

### ChatGPT

ChatGPT is the planner and orchestrator.

Its job is to:

1. understand the requested change;
2. inspect the current repository before finalizing implementation details;
3. identify the authoritative architecture and constraints;
4. split large work into ordered plan files;
5. make each file concrete enough that Codex mainly needs to implement, test, and validate;
6. stop at safe boundaries when a planning file becomes too large for one response;
7. review implementation results and prepare follow-up work when needed.

### GitHub

GitHub is the persistent coordination layer.

It stores:

- current source code;
- canonical workflow documentation;
- implementation plans;
- historical plans when useful;
- implementation results;
- commits and pull requests.

### Codex

Codex is the implementation agent.

It should receive implementation-ready instructions rather than broad design questions.

Codex is expected to:

- inspect the referenced code;
- implement the plan;
- keep the repository buildable;
- run relevant tests and validation;
- report deviations, blockers, and discoveries;
- avoid silently redesigning architecture that was already decided during planning.

## Planning rule

A planning file is not a separate implementation session.

Large work may be split into many planning files only to keep ChatGPT planning reliable and within response limits. Those files may later be implemented by the same Codex agent in one continuous implementation run.

## Source-of-truth precedence

When information conflicts, use this order:

1. current repository code and current architecture;
2. the newest consolidated/canonical plan;
3. newer implementation-plan files and macroblocks;
4. older plans and historical notes.

Historical plans are references, not automatic requirements. Reuse an old decision only when it is still compatible with the current architecture.

## Repository structure

```text
.
├── README.md
├── docs/
│   ├── CHATGPT_PROTOCOL.md
│   └── WORKFLOW.md
└── templates/
    ├── CODEX_HANDOFF.md
    ├── PLAN_INDEX.md
    └── PLAN_PART.md
```

More templates and examples can be added as the workflow is tested on real projects.

## Start here

For a new planning session:

1. give ChatGPT this repository and the target repository;
2. ask it to read [ChatGPT Planning Protocol](docs/CHATGPT_PROTOCOL.md);
3. provide the source plan, issue, or requirement;
4. let ChatGPT inspect the current target code before finalizing the decomposition;
5. create the master plan index using [PLAN_INDEX](templates/PLAN_INDEX.md);
6. optimize implementation files one at a time using [PLAN_PART](templates/PLAN_PART.md);
7. when planning is complete, prepare the Codex instruction using [CODEX_HANDOFF](templates/CODEX_HANDOFF.md).

## Canonical documents

- [Workflow rules](docs/WORKFLOW.md)
- [ChatGPT planning protocol](docs/CHATGPT_PROTOCOL.md)
- [Master plan index template](templates/PLAN_INDEX.md)
- [Implementation plan-part template](templates/PLAN_PART.md)
- [Codex handoff template](templates/CODEX_HANDOFF.md)

## Status

Initial workflow definition. The format is expected to evolve based on real ChatGPT + GitHub + Codex usage.
