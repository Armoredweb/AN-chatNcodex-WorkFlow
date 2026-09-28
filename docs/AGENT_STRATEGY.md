# Implementation Agent Strategy

The workflow uses two implementation-agent classes:

- LUA-high: lighter, faster, cheaper, less capable.
- SOL-high: larger, more capable, more expensive.

The planning layer should minimize implementation reasoning and therefore maximize safe LUA-high usage.

No model version is part of the protocol. LUA-high and SOL-high describe capability/cost roles.

## Assignment principle

Default to LUA-high when the implementation can be made mechanical enough through planning.

Use SOL-high when the task still requires substantial architecture reasoning, difficult debugging, cross-system inference, ambiguous migration decisions, or other capability that cannot reasonably be removed by better preparation.

Do not use SOL-high as insurance for an underprepared plan.

## UNASSIGNED

UNASSIGNED is allowed during decomposition when there is not yet enough implementation evidence.

During expansion and final optimization, resolve it.

No UNASSIGNED work may enter CODEX_HANDOFF.md.

## Convert SOL work to LUA when possible

Before retaining a SOL-high assignment, ask whether the planning layer can provide:

- verified code paths and symbols;
- explicit interfaces/contracts;
- exact ownership;
- algorithms;
- data/state flow;
- compatibility requirements;
- migration order;
- pseudocode;
- targeted implementation code;
- tests and expected results;
- narrower subdivision.

If this removes the difficult reasoning, reassign to LUA-high.

## Four units

Plan Part:
A safely sized planning artifact. Its size is constrained by ChatGPT planning reliability.

Micro Step:
A logical implementation unit in the dependency graph.

Implementation Batch:
A set of compatible microsteps intended to be implemented before a broader validation checkpoint.

GOAL:
A continuous autonomous mission given to one implementation agent.

These units are intentionally different.

Do not map one Plan Part to one Codex execution.

## GOAL design

Prefer long coherent GOALs.

For example, dozens of sequential LUA plan parts may be one LUA GOAL.

Manual model changes are expensive operational boundaries. Organize dependency order to reduce unnecessary LUA -> SOL -> LUA -> SOL switching.

When possible, group prepared LUA work together without violating technical dependencies.

## Testing strategy

Planning granularity must not dictate validation granularity.

Do not require a full build/test cycle merely because another Plan Part ended.

Create Implementation Batches around meaningful technical boundaries.

Agents may test earlier when:

- an intermediate invariant must be proven before later work;
- compilation is necessary to expose API breakage;
- a risky migration needs early validation;
- debugging without an intermediate test would make later failures difficult to localize.

Final GOAL validation remains mandatory.

## Agent behavior

Each implementation agent should:

1. read its GOAL and required plan files;
2. inspect current repository state before editing;
3. verify critical plan assumptions against current source;
4. implement in dependency order;
5. preserve scope and invariants;
6. validate at planned or technically necessary boundaries;
7. fix regressions introduced by its work;
8. record material deviations and the evidence that required them;
9. leave the repository coherent for the next GOAL.

Agents should not silently redesign prepared architecture or revive superseded plans.

## Final optimization responsibility

Before CODEX_HANDOFF is produced, ChatGPT performs one last file-by-file assignment audit.

The purpose is not only to detect plan defects. It is specifically to reduce SOL usage where additional preparation can make the work suitable for LUA.

The resulting GOAL sequence should make model switches explicit to the user.
