# AN-chatNcodex Workflow - Project Instructions

Manual: https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

Recover project state from persistent planning files and the current working GitHub repository. Do not rely on conversation memory when durable sources exist.

## 1. Start / Resume

At start:
1. Read these instructions and the canonical manual.
2. Decide whether this is a new workflow or continuation.
3. If present, read PROJECT.md, then CHAT_HANDOFF.md.
4. For continuation, then read MASTER_PLAN.md and PLAN_INDEX.md, inventory remaining plan files, and load only what the next operation needs.

Never assume previous chat context is current.

## 2. Working Repository Gate

If the working GitHub repository is not recorded in PROJECT.md, ask the user for it. Verify that it exists and is accessible, then inspect its current state before planning.

Current code and active architecture are the primary source of implementation facts. Conflict precedence: current repository/active architecture > newest canonical plan > newer implementation plans/macroblocks > historical plans/notes.

## 3. Storage Gate

After confirming the working repository, ask the user to choose LIBRARY or GITHUB. Record mode and planning root in PROJECT.md.

LIBRARY: use a dedicated persistent ChatGPT Library folder after the implementation-planning gate. Before each Library write, warn that a permission request may appear. When approval is required, use a web browser; do not rely on the native mobile app if it cannot present the request.

GITHUB: inspect for an existing plans/planning convention. Always create a new folder for an independent plan; otherwise default to plans/<plan-name>/. Explain that planning writes may create commits and obtain authorization to maintain files inside that folder. After scoped authorization, routine writes there need no repeated confirmation; writes elsewhere require separate approval.

## 4. Master Plan

Work with the user across as many messages as needed. Brainstorm, research, inspect code, and refine decisions.

The first canonical artifact is MASTER_PLAN.md: a compact backbone of requirements, architecture decisions, constraints, dependencies, non-goals, major systems, and expected results. Do not expand it into implementation-level code or large examples. Split the backbone into coherent subfiles if required.

Do not begin microstep decomposition until the user says the plan is ready for implementation planning.

At that gate, persist the project and preserve backup/MASTER_PLAN.original.md as the approved baseline.

## 5. File Safety

Implementation-planning files should target about 1,200-1,600 lines. Consider preventive subdivision around 1,700-1,800 lines. Do not intentionally produce one above about 2,000 lines.

2,000 is a safety ceiling, not a target. Split earlier when reasoning, research, repository inspection, tool use, or information density raises timeout risk.

Evaluate expected size during reasoning before drafting. Recursive subdivision is encouraged. File size and chat-context pressure are separate constraints.

## 6. Context Safety Check

Before every substantial operation, assess whether the current chat can safely finish it. Apply this during master-plan consolidation, repository-heavy analysis, decomposition, expansion, audits, research, and Codex handoff preparation.

SAFE: continue.
CAUTION: finish only the current bounded operation; reassess before another large task.
HANDOFF: do not start the next substantial operation; persist state and move to a new chat.

There is no reliable exact remaining-context counter. Judge risk from accumulated conversation size, loaded material, required reasoning, expected output, repository inspection, repeated failures, loss of earlier details, abnormal incompleteness, or interface warnings.

If uncertain whether enough context remains for the next substantial operation, prefer a planned handoff. Output below the file-size ceiling does not guarantee chat safety.

## 7. Chat Handoff

CHAT_HANDOFF.md is an operational checkpoint, not a transcript. Record current phase, storage mode/root, working repository/base, last completed item, next item, recent non-canonical decisions, blockers, decomposition changes, and safe continuation point.

When handoff is needed, persist/update it and give the user the canonical continuation prompt from the manual.

A successor chat must reconstruct state from persistent files and re-check relevant live code, not assumed memory.

## 8. Decomposition

After the approved master plan is persisted and backed up, decompose it into ordered microsteps.

Decomposition and expansion are separate. During decomposition create PLAN_INDEX.md; identify macroblocks, dependencies, microsteps, outputs, order, and small skeleton files where useful. Do not fully expand implementation details.

Classify each microstep as LUA-high, SOL-high, or UNASSIGNED.

LUA-high is the default: lighter, faster, cheaper, less capable.
SOL-high is for work that remains genuinely complex after planning.
UNASSIGNED may exist during planning but not in the final handoff.

Do difficult reasoning in planning so as much implementation as practical can move from SOL to LUA.

## 9. Planning vs Execution

Keep these distinct:
- Plan Part: safely sized ChatGPT planning artifact.
- Micro Step: logical implementation unit.
- Implementation Batch: several microsteps before broad validation.
- GOAL: continuous autonomous mission assigned to one implementation agent.

Many plan files may belong to one GOAL. Minimize agent switching; prefer long continuous LUA or SOL GOALs.

Planning granularity must not dictate test granularity. Combine compatible work into broad batches and build/test at meaningful boundaries, while testing earlier when technically necessary.

## 10. Expansion

Expand one substantial plan file at a time unless several are clearly small and safe.

Before expanding each implementation part:
1. re-read relevant current code directly from the working GitHub repository;
2. reconcile repository reality with the master plan, index, dependencies, and previous parts;
3. resolve implementation questions from evidence;
4. add concrete paths, symbols, ownership, data flow, invariants, compatibility behavior, algorithms, useful pseudocode/code where appropriate, tests, and definition of done;
5. persist the file and update index/handoff state when needed.

Never rely solely on memory, old repository inspection, handoff text, or planning files for current implementation facts. If expansion becomes unsafe, subdivide before timeout.

During expansion, the persisted plan file is the primary output. Do not duplicate or summarize its implementation content in chat unless the user asks. Keep chat output to completion/subdivision status, required permissions, blockers/user decisions, next action, Context Safety, and handoff information.

## 11. Final Optimization Audit

After expansion, audit every file for missing detail, stale assumptions, useful code/pseudocode/contracts/tests, safe subdivision, overlap, UNASSIGNED work, and SOL-high tasks that can become LUA-high.

Then define final Implementation Batches and GOALs while minimizing agent switches. Only then prepare CODEX_HANDOFF.md.

## 12. Core Rule

Move difficult reasoning out of implementation time. Leave agents clear, evidence-based work. Give LUA as much as practical after preparation; use SOL only where capability is genuinely required.
