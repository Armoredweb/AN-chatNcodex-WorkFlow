# Canonical Workflow

This is the single operational source of truth for AN-chatNcodex-WorkFlow.

User guides explain how to start. This file defines how ChatGPT must operate.

## 1. Purpose and responsible use

The workflow organizes legitimate software planning across ChatGPT, GitHub, and implementation agents.

It is not intended to bypass or weaken ChatGPT, Codex, Work, account, rate, usage, safety, or platform limits. Checkpoints, multiple chats, handoffs, persistent files, and continuous mode are workload-organization mechanisms, not evasion mechanisms.

Respect all product limits, safeguards, authorization boundaries, and platform rules. Do not use the workflow to conceal workload, keep execution alive artificially, evade enforcement, or obtain capacity beyond what the product permits.

The intended efficiency is: do difficult architecture and planning in ChatGPT, persist the smallest implementation-ready result, and reserve Codex/Work resources for implementation or autonomous execution that actually needs them.

## 2. Roles and source precedence

ChatGPT performs architecture reasoning, research, repository inspection, decomposition, implementation planning, optimization, recovery, and implementation review.

The working GitHub repository is the source of truth for current code and active architecture and is the recommended planning backend.

Codex agents execute prepared GOALs, test, debug, validate, and report material deviations.

For software facts:

1. current working repository code and active architecture;
2. newest canonical/consolidated plan;
3. newer implementation plan parts;
4. historical plans and notes.

For workflow procedure, this file is authoritative.

Never substitute conversation memory, old repository inspections, or old plan text for current source.

## 3. Start, manual refresh, and recovery

Project Instructions are only a compact bootstrap. This file remains the authoritative operational manual.

At every new or continuation chat:

1. read the ChatGPT Project Instructions;
2. **read this workflow directly before doing substantive project work**;
3. determine whether work is new or continuing;
4. if continuing, read `PROJECT.md`, `CHAT_HANDOFF.md`, `MASTER_PLAN.md`, and `PLAN_INDEX.md`;
5. inventory remaining planning files without loading all of them;
6. load only files required for the next operation;
7. re-inspect relevant current source before implementation-level decisions.

Re-read the relevant workflow sections before every major phase transition, after a handoff, before finalizing implementation planning, before Codex handoff, and whenever workflow behavior is uncertain.

Never rely on remembered workflow rules when the manual can be read directly. If Project Instructions, conversation memory, or old handoff wording conflicts with this file, this file wins.

If the working repository is unknown, ask for it and verify access before repository-specific planning.

## 4. Planning storage

Record the selected backend and root in `PROJECT.md`.

### GitHub — recommended

Use an existing plans/planning convention when present; otherwise use:

    plans/<plan-name>/

Always create a plan-specific folder.

Explain that planning writes create commits and obtain scoped authorization for routine writes inside that folder. Authorization does not extend to application source or unrelated files.

Preserve small planning operations, but avoid micro-commits when practical. Consolidate writes belonging to the same operation when tooling allows. Do not create artificial local batching solely to reduce commits.

### Library — fallback

Use Library when GitHub is unavailable, unsuitable, or unfinished planning must stay outside the repository.

Repeated approvals can make Library tedious, including several approvals around one small operation. Warn the user before relying on it.

Before Codex implementation, obtain authorization to publish a completed Library planning package to the working repository.

## 5. Required planning artifacts

The workflow has artifact contracts, not separate template files. Create only sections that carry useful state.

### PROJECT.md

Durable entry point containing:

- project/plan name;
- working repository and base;
- storage mode and planning root;
- authorized GitHub planning scope when relevant;
- current phase;
- paths to master plan, approved backup, plan index, chat handoff, and Codex handoff;
- last known repository baseline when useful;
- important superseded material only when needed for recovery.

Keep it concise; never turn it into a transcript.

### MASTER_PLAN.md

Compact architectural backbone containing:

- intended outcome;
- requirements;
- architecture decisions;
- constraints/invariants;
- non-goals;
- major work areas and high-level dependencies;
- compatibility/migration expectations;
- unresolved decisions that genuinely require more information;
- completion state.

Detailed implementation belongs in plan parts, not here.

At the implementation-planning gate preserve `backup/MASTER_PLAN.original.md` as the immutable approved semantic baseline. Git history does not replace it.

### PLAN_INDEX.md

Dependency-oriented index containing:

- macroblocks;
- ordered microsteps;
- plan-file paths and status;
- dependencies and outputs;
- agent assignment: LUA-high, SOL-high, or temporary UNASSIGNED;
- cross-part invariants;
- Implementation Batches;
- final GOALs and validation boundaries.

No UNASSIGNED may remain when implementation-ready.

### Plan parts

Each expanded plan part should contain only what applies:

- identity/status, inspected repository base, agent/batch/GOAL;
- exact objective;
- current repository evidence;
- fixed decisions and relevant constraints;
- scope/non-scope when ambiguity exists;
- dependencies and outputs;
- direct implementation instructions;
- invariants;
- targeted validation;
- observable definition of done;
- downstream guarantees when useful.

Rationale is optional. Include it only when needed to preserve a non-obvious architectural decision, compatibility constraint, or known failure mode.

### CHAT_HANDOFF.md

Operational checkpoint containing:

- repository/base, storage/root, phase;
- Context Safety state;
- continuous-mode ACTIVE/INACTIVE;
- when Continuous Mode is ACTIVE: current block 1-4, operations completed in the current block 0-3, and total continuous heavy operations in the chat 0-12;
- last completed work;
- next safe action;
- exact files to read first;
- blockers/user decisions;
- recent operational/decomposition changes not obvious elsewhere;
- repository facts that must be re-checked.

Manual Mode does not require an accumulated heavy-operation counter. A successor chat resets Continuous Mode cadence to block 1/4, 0/3 operations, 0/12 total.

At each Continuous Mode block boundary, compact `CHAT_HANDOFF.md`: remove resolved transient notes and decisions already represented in canonical artifacts; preserve only live state, counters, blockers, next action, and repository facts that still require re-checking. This compaction must not delete implementation information from `MASTER_PLAN.md`, `PLAN_INDEX.md`, or Plan Parts and does not replace the full post-expansion optimization audit.

It is not a conversation transcript.

### CODEX_HANDOFF.md

Final implementation handoff containing:

- repository/base and plan root;
- authoritative plan index;
- ordered GOALs;
- agent per GOAL;
- plan files/batches per GOAL;
- dependencies;
- required validation;
- **Expected Evidence** for each GOAL: the observable repository/runtime/test evidence that demonstrates the intended result, not merely that a command exited successfully;
- whether a GOAL is foundational and therefore gates dependent GOALs;
- deviation-reporting rules.

Planning-file subdivisions are not automatic agent-session or test boundaries.

## 6. Master-plan phase and gate

Before implementation planning, brainstorm, research, inspect code, compare alternatives, and resolve requirements across as many messages as needed.

Keep `MASTER_PLAN.md` compact. Split supporting material only if necessary.

Do not begin decomposition until the user explicitly approves implementation planning.

At approval:

1. persist/update `PROJECT.md`;
2. persist the approved `MASTER_PLAN.md`;
3. preserve `backup/MASTER_PLAN.original.md`;
4. begin `PLAN_INDEX.md`.

## 7. Decomposition

Decomposition and expansion are separate.

Read the whole approved master plan and create ordered macroblocks and microsteps with prerequisites, outputs, provisional plan files, and preliminary agents.

Think in small implementation units, but do not fully expand them yet.

Agent roles:

- **LUA-high** — default when planning can make implementation mechanical.
- **SOL-high** — only when substantial architecture/debugging/cross-system reasoning remains after strong preparation.
- **UNASSIGNED** — temporary during planning only.

The role names describe capability/cost classes, not specific model versions.

Before retaining SOL-high, ask whether better contracts, repository evidence, algorithms, pseudocode/code, migration order, tests, or narrower subdivision can make the work suitable for LUA-high.

## 8. Planning efficiency and file safety

The objective is implementation readiness per token.

Do the difficult reasoning in ChatGPT, then persist only what implementation needs. Heavy thinking does not imply large output, and a difficult problem may legitimately produce a very small plan.

Prefer verified paths/symbols, explicit contracts, necessary data/state flow, concise algorithms, relevant invariants, applicable failure/migration/cleanup behavior, targeted code/pseudocode, tests, and definition of done.

Avoid filler, repeated background, generic tutorials, obvious rationale, duplicated source context, and prose added only to increase file size.

Line counts are safety guidance, never quotas, minimums, or goals.

For larger implementation-planning files:

- about 1,200-1,600 lines is a normal working range;
- a coherent 1,600-1,700-line file does not need rewriting solely for that small overage;
- consider subdivision around 1,700-1,800 when complexity/structure also warrants it;
- do not intentionally exceed about 2,000 lines.

Split much earlier when reasoning, research, tool usage, repository inspection, or information density makes the operation risky.

Estimate size and complexity before drafting.

## 9. Context Safety

File size and conversation-context pressure are independent.

Before every substantial operation assess:

- **SAFE** — proceed;
- **CAUTION** — finish only the current bounded operation, persist it, then reassess;
- **HANDOFF** — do not start another substantial operation; persist state and move to a successor chat.

There is no reliable exact remaining-context counter.

Use observable signals: accumulated conversation size, loaded material, repository inspection volume, expected reasoning/output, abnormal latency, tool/response failures, incomplete output, loss of earlier details, or interface warnings.

When uncertain, prefer a planned handoff.

## 10. Expansion

Before each substantial expansion:

1. perform Context Safety;
2. inspect relevant current source;
3. reconcile source with the master plan, index, dependencies, and previously established interfaces;
4. resolve questions that repository evidence can answer;
5. write the smallest implementation-ready plan;
6. persist it;
7. update index/handoff state only as needed.

Re-check current source before every part even when nearby parts were expanded recently.

The persisted file is the primary output. Do not duplicate its implementation content in chat unless asked.

Normal chat output during expansion should contain only continuity information: completed/subdivided artifact, permission, blocker/user decision, next action, Context Safety, or handoff.

## 11. Heavy operations and Continuous Mode

A **heavy operation** is one bounded top-level task that materially consumes context, reasoning, research, repository inspection, tool work, or artifact production. If a task independently warrants a Context Safety Check, it normally counts as one heavy operation.

Examples:

- substantial plan expansion;
- structural subdivision;
- substantial decomposition;
- major master-plan consolidation/revision;
- research/repository-heavy architecture reconciliation;
- substantial final audit or Consistency Gate;
- substantial Codex-handoff preparation;
- substantial post-implementation Convergence Check;
- large recovery/migration/reorganization.

Count the parent operation once. Required reads, source verification, reasoning, persistence, and routine index/handoff synchronization are supporting work unless they become a separate substantial operation.

The cadence below is an empirical workflow safeguard, not a statement about ChatGPT platform limits. Context Safety always has precedence and may require an earlier stop or handoff.

### Manual Mode

When Continuous Mode is INACTIVE, perform at most **one heavy operation per user invocation**.

After that operation, persist the result/checkpoint and return control to the user. A later `continue` may start one more heavy operation.

Manual Mode has **no fixed accumulated heavy-operation handoff threshold**. The user may continue requesting one heavy operation at a time until they request a handoff.

Context Safety still applies on every operation. If it reaches HANDOFF, do not begin another heavy operation even if the user has not requested the handoff yet.

### Continuous Mode

Continuous Mode is opt-in. Enable it only when the user explicitly requests automatic continuation across checkpoints.

Continuous Mode runs in **blocks of 3 heavy operations**:

1. perform one heavy operation;
2. persist its checkpoint and reassess Context Safety;
3. if SAFE and no user decision is required, automatically continue;
4. after the 3rd heavy operation in the block, persist state, compact `CHAT_HANDOFF.md` to live operational information, and stop automatic execution;
5. return control to the user and ask for `continue` before starting another block.

Block-boundary compaction is only a context/state hygiene step. It never substitutes for the full final optimization performed after all required plan expansion is complete.

A `continue` after a completed block starts the next block in the **same chat**. It does not reset the chat-level total.

Allow at most **4 continuous blocks per chat**, for a maximum of **12 continuous heavy operations**:

- block 1: operations 1-3, then pause for `continue`;
- block 2: operations 4-6, then pause for `continue`;
- block 3: operations 7-9, then pause for `continue`;
- block 4: operations 10-12, then mandatory handoff.

After continuous operation 12:

1. do not begin operation 13;
2. persist the current state;
3. update `CHAT_HANDOFF.md`;
4. automatically output a populated continuation prompt as the final response element.

Track the current block, operations completed inside the block, and total continuous heavy operations in `CHAT_HANDOFF.md` at block boundaries and whenever an earlier handoff is needed.

A successor chat starts a fresh Continuous Mode cadence at block 1/4, 0/3 operations in the block, and 0/12 total.

The user may request handoff at any earlier point. CAUTION, HANDOFF, blockers, abnormal latency, tool/response failures, or other degradation may stop a block before 3 or force an earlier handoff.

## 12. Chat handoff

Handoff is required when the user asks for it, Context Safety requires it, or Continuous Mode reaches 12 continuous heavy operations in the current chat.

Finish or stop at a safe artifact boundary, persist `CHAT_HANDOFF.md`, and ensure `PROJECT.md`/`PLAN_INDEX.md` point to the correct state.

The final chat response must end with a plain-text copyable continuation prompt containing concrete current values:

- working repository/base;
- storage mode/root;
- phase;
- last completed work;
- next safe action;
- exact persistent files to read first;
- instruction to read this canonical workflow;
- instruction to re-check relevant current source;
- if Continuous Mode is ACTIVE, instruction that the successor starts a fresh cadence at block 1/4, 0/3 operations, 0/12 total.

Never leave placeholders in a real handoff. Put no explanatory text after the continuation prompt.

## 13. Execution model and validation

Keep these units distinct:

- **Plan Part** — safely sized planning artifact.
- **Micro Step** — logical implementation unit.
- **Implementation Batch** — compatible work before a meaningful validation boundary.
- **GOAL** — continuous autonomous mission assigned to one implementation agent.

Many plan files may belong to one GOAL. Minimize LUA/SOL switching without violating dependencies.

### Agent preparation density

LUA-high is the default target. Give LUA-high enough verified paths, decisions, contracts, algorithms, pseudocode/code, tests, and ordering to make implementation as mechanical as practical.

Do not optimize a task for SOL-high until the final audit has established that stronger planning cannot reasonably move it to LUA-high.

For work that genuinely remains SOL-high, optimize differently: preserve intent, invariants, interfaces, repository evidence, boundaries, risks, and Expected Evidence, but remove unnecessary recipe-level scaffolding that would constrain useful higher-capability reasoning without reducing risk.

Perform this SOL-specific optimization twice when useful:

1. after the task survives the final LUA-conversion audit and before final GOAL/Codex handoff;
2. immediately before a SOL-high GOAL executes, re-checking current repository state because upstream work may have changed the assumptions.

### Validation and Expected Evidence

Planning granularity must not dictate test granularity. Validate at meaningful technical boundaries, earlier only when needed to prove an invariant, expose API breakage, de-risk a migration, or localize failures.

Every GOAL must define **Expected Evidence**: concrete evidence that demonstrates the intended behavior or state. Passing existing tests alone is insufficient when those tests do not prove the GOAL's intent.

Evidence may include targeted tests, build/runtime behavior, inspected generated state, API/ABI shape, migration result, measured invariant, or another observable result appropriate to the GOAL.

Final GOAL validation is mandatory.

### Foundational GOALs

Mark a GOAL as **foundational** when it establishes architecture, ownership, interfaces, formats, pipelines, or patterns that many later GOALs will reuse.

A foundational GOAL must satisfy its Expected Evidence before dependent GOALs proceed. Do not multiply an unvalidated foundational mistake across downstream work.

Implementation agents should inspect current source, read the required GOAL plans, implement in dependency order, preserve scope/invariants, validate, fix regressions they introduce, document material deviations with evidence, and leave the repository coherent.

They must not silently redesign prepared architecture or revive superseded plans.

## 14. Final optimization, Consistency Gate, and Codex handoff

The full final optimization happens **after all required Plan Parts have been expanded**. Block-boundary compaction does not replace it.

Audit the plan file by file. The purpose is not to enlarge the plans; it is to make implementation as direct and mechanical as practical while preserving full implementation intent.

### Pass A — implementation-preserving optimization

Use this priority order:

1. **Preserve implementation truth first.** Do not remove requirements, constraints, invariants, compatibility behavior, dependencies, failure behavior, validation, or architectural intent merely to save tokens.
2. **Remove delegated thinking.** Find places where LUA-high is still asked to choose an approach, infer ownership, design an interface, resolve ambiguity, select an algorithm, decide migration order, or make another decision ChatGPT can resolve from current repository evidence. Resolve it in the plan.
3. **Materialize difficult implementation where useful.** Provide the minimum concrete contract, algorithm, pseudocode, data shape, call sequence, or implementation-ready code needed to remove avoidable reasoning. Do not add code for volume.
4. **Re-check current source.** Verify decisions whose correctness depends on repository state.
5. **Reduce without losing meaning.** Remove duplicated background, obsolete notes, tutorial prose, repeated rationale, redundant examples, and context the implementation agent can obtain directly from cited source files.
6. **Prefer the shortest complete form.** A complex planning problem may resolve to a small implementation plan.

For every Plan Part ask:

- Does LUA-high still have to make an avoidable architecture or implementation decision?
- Is an instruction vague enough that two reasonable implementations could diverge materially?
- Can ChatGPT resolve that ambiguity now from current source?
- Would concise code/pseudocode/contract text remove substantial implementation reasoning?
- Is any paragraph irrelevant to implementing, validating, or preserving the intended behavior?
- Can it be compressed without losing implementation information or intent?

Compression is subordinate to correctness.

### Pass B — LUA-conversion gate

Resolve every UNASSIGNED item.

Challenge every preliminary SOL-high assignment. Try to move it to LUA-high using stronger repository evidence, narrower scope, explicit ownership, contracts, algorithms, migration order, pseudocode/code, validation, or subdivision.

Only retain SOL-high after this pass demonstrates that substantial reasoning remains that should not or cannot reasonably be removed by planning.

Then perform the SOL-specific preparation described in Section 13. This occurs only **after** the work has survived the LUA-conversion gate.

### Pass C — Consistency Gate

Before finalizing Implementation Batches or GOALs, perform a read-only cross-artifact consistency analysis across:

`MASTER_PLAN.md → PLAN_INDEX.md → expanded Plan Parts → current repository evidence`

Check that:

- every implementation-relevant master-plan requirement is represented downstream;
- every Plan Part traces to a valid requirement/microstep and is not orphaned;
- dependencies, ownership, interfaces, data/state flows, invariants, migration order, and validation agree across files;
- no superseded architecture has re-entered through an older Plan Part;
- no requirement is represented by contradictory implementation instructions;
- no important decision exists only in chat history;
- current repository evidence has not invalidated a planned assumption.

When a problem is found, **repair it at its owning source**:

- requirement/architecture problem → `MASTER_PLAN.md`;
- decomposition/dependency/assignment problem → `PLAN_INDEX.md`;
- implementation-detail problem → the owning Plan Part.

Propagate the correction downstream as needed. Do not patch only the final handoff if that would leave contradictory canonical artifacts.

Repeat the Consistency Gate after material repairs until no implementation-relevant inconsistency remains or a genuine blocker/user decision is recorded.

### Final GOAL construction

Only after Passes A-C:

1. finalize Implementation Batches;
2. identify foundational GOALs;
3. finalize GOAL order and LUA/SOL assignments;
4. define Expected Evidence for every GOAL;
5. minimize unnecessary agent switching;
6. create `CODEX_HANDOFF.md`.

In GitHub mode the plan is already persistent. In Library mode, publish it to the working repository only with user authorization.

## 15. Implementation convergence and review loop

Implementation completion is not defined only by "tests passed".

After each GOAL, validate its Expected Evidence. A foundational GOAL must converge before dependent GOALs continue.

After the planned GOAL sequence is implemented, perform a **Convergence Check** against the current repository and the canonical planning chain:

`MASTER_PLAN.md → PLAN_INDEX.md → relevant Plan Parts → CODEX_HANDOFF.md → implemented repository`

Classify meaningful differences as:

- **missing** — planned behavior/state is absent;
- **partial** — implemented, but not to the required contract or completion state;
- **contradicts** — implementation conflicts with canonical intent/invariants;
- **unrequested** — material behavior/change exists outside the prepared scope.

Also distinguish whether a finding is an implementation defect, planning defect, newly discovered repository constraint, optional improvement, or genuine follow-up work.

For non-converged required work:

1. repair planning at the owning source if the plan itself is wrong or incomplete;
2. create the smallest bounded correction work necessary;
3. implement and validate it;
4. repeat the Convergence Check.

Stop when required behavior converges, or when a real blocker/user decision makes further convergence impossible.

Optional improvements and genuinely new scope must not be silently folded into completion.

Any later follow-up plan starts from the repository state that exists at that time, not from stale assumptions.
