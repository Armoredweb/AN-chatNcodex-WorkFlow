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

## Rationale / constraints

Include only rationale required to preserve a non-obvious architectural decision, compatibility constraint, or known failure mode. Omit this section when implementation instructions are self-explanatory.

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

Use the smallest amount of text that makes implementation unambiguous. Be direct and implementation-oriented; do not add tutorial prose, repeated background, generic explanations, or filler.

Use verified paths/symbols when available. Resolve only what applies:

- ownership;
- interfaces/contracts;
- state/data flow;
- lifecycle;
- algorithms;
- compatibility/error behavior;
- migration/cleanup;
- concurrency/performance constraints.

Prefer concise contracts, pseudocode, or implementation-ready code when they reduce LUA-high reasoning. A small complete solution is preferable to a large document.

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

Optional. Keep only implementation-relevant information not already stated above. No filler or repeated context.

- <note>
