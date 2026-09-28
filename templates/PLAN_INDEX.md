# <Plan Name> - Implementation Plan Index

Status: <decomposing | expanding | final-audit | implementation-ready>
Working repository: <owner/repository>
Working base: <branch/ref>
Storage mode: <LIBRARY | GITHUB>
Planning root: <location>
Master plan: <path>
Approved baseline: <backup/MASTER_PLAN.original.md>
Workflow manual: https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

## Source precedence

1. current repository code and active architecture;
2. newest canonical/consolidated plan;
3. newer implementation parts/macroblocks;
4. historical plans/notes.

Known superseded material:

- <item>

## Macroblocks

### <ID> - <name>

Purpose:
- <purpose>

Depends on:
- <dependency>

Produces:
- <output>

## Ordered microsteps

| Order | Plan file | Macroblock | Depends on | Agent | Batch | GOAL | Status |
|---|---|---|---|---|---|---|---|
| 001 | plan/001-<name>.md | <id> | - | UNASSIGNED | TBD | TBD | skeleton |

Agent is LUA-high, SOL-high, or UNASSIGNED during planning. No UNASSIGNED may remain when status becomes implementation-ready.

## Cross-part invariants

- <invariant>

## Implementation Batches

Define only when enough expansion exists.

### <Batch ID>

Plan parts:
- <paths>

Validation boundary:
- <validation>

## GOALs

Finalize after the optimization audit.

### <GOAL ID>

Agent: <LUA-high | SOL-high>
Plan parts / batches:
- <items>

Depends on:
- <GOAL>

Required final validation:
- <validation>

## Risks and unresolved planning questions

- <item>

## Final readiness checklist

- [ ] all required microsteps exist;
- [ ] all expanded parts are within safe planning size or intentionally subdivided;
- [ ] relevant repository assumptions were re-verified during expansion;
- [ ] dependencies are consistent;
- [ ] no UNASSIGNED remains;
- [ ] every SOL-high assignment survived the LUA-conversion audit;
- [ ] Implementation Batches are defined;
- [ ] GOALs minimize unnecessary agent switching;
- [ ] required validations are explicit;
- [ ] CODEX_HANDOFF.md can be generated without reconstructing design from chat history.
