# <PLAN-ID> — Implementation Plan Index

Status: planning  
Target repository: <owner/repository>  
Target base: <branch / commit>  
Source plan: <path / issue / request>  
Implementation mode: <single continuous Codex run / staged runs>

## Objective

Describe the final outcome of the complete implementation.

## Authoritative inputs

Use this precedence for this plan:

1. <current repository / active architecture>
2. <newest canonical plan>
3. <newer macroblocks or implementation notes>
4. <historical references>

Known superseded material:

- <document/decision that must not be revived>

## Repository baseline

Relevant repository state verified before decomposition:

- <system/path/current behavior>
- <system/path/current behavior>

Baseline ref:

- branch: <branch>
- commit: <optional SHA>

## Macroblocks

### 01 — <Macroblock>

Purpose:

- <purpose>

Produces:

- <output relied on later>

### 02 — <Macroblock>

Purpose:

- <purpose>

Depends on:

- 01

## Ordered plan files

| Order | File | Macroblock | Depends on | Status |
|---|---|---|---|---|
| 01 | `01-<name>.md` | 01 | — | draft |
| 02 | `02A-<name>.md` | 02 | 01 | draft |
| 03 | `02B-<name>.md` | 02 | 02A | draft |

The decomposition may be refined during detailed planning. If one file becomes too large, split it and update this table.

## Cross-part invariants

All parts must preserve:

- <invariant>
- <invariant>

## Validation strategy

The complete implementation must be validated with:

- <build>
- <unit tests>
- <integration tests>
- <runtime/manual checks>
- <regression checks>

## Known risks

- <risk>
- <risk>

## Open questions

Only questions that cannot currently be resolved from repository evidence should remain here.

- <question>

## Final Codex handoff requirements

Before implementation begins:

- [ ] all plan files are complete;
- [ ] the ordering table is current;
- [ ] dependencies are internally consistent;
- [ ] obsolete assumptions have been removed;
- [ ] verified repository paths still exist;
- [ ] validation commands are known;
- [ ] implementation mode is explicit.
