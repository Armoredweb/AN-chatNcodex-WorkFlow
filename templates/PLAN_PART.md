# <PLAN-ID> — <Title>

Status: draft  
Macroblock: <macroblock ID/name>  
Sequence: <position in implementation order>  
Target repository: <owner/repository>  
Target branch/base: <branch or ref>

## Objective

Describe the exact repository state or behavior that must exist when this part is complete.

## Why this part exists

Explain the architectural purpose of this part and why it is a useful planning boundary.

## Current repository evidence

Verified relevant code at planning time:

- `path/to/file` — <relevant type/function/system and current behavior>
- `path/to/other` — <relevant evidence>

Repository observations:

- <observation>
- <observation>

Do not list guessed paths as verified evidence.

## Decisions already made

Codex should treat these as fixed planning decisions unless current implementation evidence makes one impossible:

- <decision>
- <decision>

## Scope

This part includes:

- <work item>
- <work item>

## Non-scope

This part must not:

- <unrelated redesign>
- <future macroblock work>

## Dependencies

Required before implementation:

- <previous plan part or repository state>

Produces prerequisites for:

- <later plan part>

## Implementation instructions

### 1. <Implementation area>

Relevant current files:

- `path/to/file`

Required changes:

- <specific change>
- <state ownership / API / data flow / invariant>
- <compatibility behavior>
- <error handling>

Expected result:

- <observable technical result>

### 2. <Implementation area>

Relevant current files:

- `path/to/file`

Required changes:

- <specific change>

Expected result:

- <observable technical result>

## Invariants

The implementation must preserve:

- <invariant>
- <invariant>

## Tests and validation

Run or add the relevant checks:

- <unit test>
- <integration test>
- <build command>
- <runtime validation>
- <regression case>
- <failure case>

Expected validation result:

- <result>

## Definition of done

This part is complete only when:

- [ ] <observable criterion>
- [ ] <observable criterion>
- [ ] relevant tests pass;
- [ ] the repository remains buildable;
- [ ] no unrelated subsystem was redesigned;
- [ ] material deviations from this plan are documented.

## Handoff to the next part

After this part, the repository should provide:

- <new interface/state/behavior>

The next part may assume:

- <assumption guaranteed by this part>

## Implementation notes

Use this section only for discoveries made during implementation that materially change the handoff.

- <note>
