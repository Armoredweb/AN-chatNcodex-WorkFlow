# Codex Implementation Handoff

Working repository: <owner/repository>
Base branch/ref: <branch/ref>
Planning root: <path>
Plan index: <path>
Workflow manual: https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

## Mission

Implement the prepared GOALs in dependency order.

Planning-file subdivisions are planning-safety boundaries, not automatic agent sessions or test boundaries.

## Source precedence

1. current repository code and active architecture;
2. canonical master plan and implementation-ready PLAN_INDEX;
3. expanded plan parts;
4. historical material.

If a material plan assumption conflicts with the current repository, do not silently redesign. Record the evidence and deviation.

## GOAL sequence

### <GOAL ID>

Agent: <LUA-high | SOL-high>
Depends on: <GOAL/none>

Read:
- <plan parts / batches>

Mission:
- <goal>

Validation:
- <checks>

### <GOAL ID>

Agent: <LUA-high | SOL-high>
Depends on: <GOAL>

Read:
- <plan parts / batches>

Mission:
- <goal>

Validation:
- <checks>

## Required implementation behavior

1. Inspect current repository state before editing.
2. Read all plan parts required by the current GOAL.
3. Implement in dependency order.
4. Keep work scoped to the prepared plan.
5. Treat one GOAL as a continuous autonomous mission even if it includes many plan files.
6. Validate at planned Implementation Batch boundaries or earlier when technically necessary.
7. Fix regressions introduced by the implementation.
8. Do not revive superseded architecture.
9. Document material deviations and their repository evidence.
10. Leave the repository coherent for the next GOAL.

## Final completion report

Report:

- GOALs completed;
- files changed;
- important architectural results;
- builds/tests/checks run and results;
- plan deviations;
- unresolved blockers;
- follow-up work only when genuinely required.
