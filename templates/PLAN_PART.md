# <Plan ID> - <Title>

Status: <skeleton | expanding | complete | superseded>
Macroblock: <id/name>
Sequence: <order>
Working repository: <owner/repository>
Repository base inspected: <branch/ref/commit>
Agent: <LUA-high | SOL-high | UNASSIGNED>
Implementation Batch: <id/TBD>
GOAL: <id/TBD>

## Objective

Describe the exact implementation state this part must produce.

## Why this part exists

Explain the architectural purpose and why this is a useful planning boundary.

## Current repository evidence

Verified immediately before expansion:

- <path / symbol / observed behavior>

Do not present guessed paths or old planning assumptions as current evidence.

## Decisions already made

- <fixed decision>

## Scope

- <included work>

## Non-scope

- <excluded work>

## Dependencies

Requires:

- <prior state / plan part>

Produces:

- <state used later>

## Implementation instructions

Describe concrete work using verified paths/symbols when available.

Resolve as applicable:

- ownership;
- interfaces and contracts;
- state/data flow;
- lifecycle;
- algorithms;
- compatibility behavior;
- failure/error behavior;
- migration;
- cleanup/removal;
- concurrency/performance constraints.

Include useful pseudocode or implementation code when it materially reduces implementation-agent reasoning.

## Invariants

- <invariant>

## Validation

Plan validation at technically meaningful boundaries. This Plan Part does not automatically require its own full build/test cycle.

Relevant checks:

- <check>

Expected result:

- <result>

## Definition of done

- [ ] <observable criterion>
- [ ] no unrelated redesign;
- [ ] material deviations are documented;
- [ ] downstream prerequisites produced by this part are available.

## Handoff to dependent work

After implementation, later work may assume:

- <guarantee>

## Planning notes

Keep only information useful to implementation or later plan maintenance.

- <note>
