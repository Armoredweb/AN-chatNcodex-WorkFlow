# AN-chatNcodex-WorkFlow

A practical planning workflow for using normal ChatGPT + GitHub + Codex on large software projects.

The workflow separates three responsibilities:

- ChatGPT: architecture, research, decomposition, implementation planning, context recovery, and review.
- GitHub: current code source of truth and, optionally, persistent planning storage.
- Codex agents: autonomous implementation, testing, debugging, and validation from prepared plans.

The central goal is to move difficult reasoning into planning so implementation agents receive explicit, evidence-based work without forcing each planning file to become a separate execution.

## Start here

User documentation:

- English: docs/USER_GUIDE.md
- Português (Brasil): docs/USER_GUIDE_PT-BR.md

Both user guides are self-contained. They include copyable Project Instructions and startup/continuation prompts directly in the guide.

Operational documentation:

- docs/WORKFLOW.md - canonical end-to-end workflow.
- docs/CHATGPT_PROTOCOL.md - rules for ChatGPT while planning.
- docs/LIBRARY_AND_BACKUP.md - storage, persistence, backup, and recovery.
- docs/AGENT_STRATEGY.md - LUA-high / SOL-high assignment and execution strategy.

Raw text templates:

- templates/PROJECT_INSTRUCTIONS.txt
- templates/START_PROMPT.txt
- templates/CHAT_CONTINUATION_PROMPT.txt

Planning templates:

- templates/PROJECT.md
- templates/MASTER_PLAN.md
- templates/PLAN_INDEX.md
- templates/PLAN_PART.md
- templates/CHAT_HANDOFF.md
- templates/CODEX_HANDOFF.md

## Manual Context Rule

The canonical workflow manual must remain an active reference during the entire lifecycle.

ChatGPT reads it at every new or continuation chat and refreshes the relevant sections before major phase transitions, after handoffs, and whenever workflow behavior is uncertain.

The workflow must not depend only on remembered process rules.

For current software implementation facts, the working GitHub repository remains the primary source of truth.

## Core flow

    Project instructions
        -> new ChatGPT chat
        -> read/refresh this manual
        -> identify and verify working GitHub repository
        -> choose planning storage: Library or GitHub
        -> brainstorm / research / inspect code
        -> compact MASTER_PLAN
        -> user implementation-planning gate
        -> persist + backup approved master plan
        -> decompose into microsteps without expansion
        -> assign LUA-high / SOL-high / UNASSIGNED
        -> expand one safe plan part at a time
        -> final optimization audit
        -> define Implementation Batches and GOALs
        -> Codex handoff
        -> implementation / validation

## Two independent safety controls

File safety:

- normal target: about 1,200-1,600 lines;
- preventive subdivision: around 1,700-1,800 lines;
- do not intentionally exceed about 2,000 lines;
- split earlier when reasoning, research, repository inspection, or information density makes the operation risky.

Chat safety:

- there is no exact reliable remaining-context counter;
- ChatGPT performs a Context Safety Check before substantial operations;
- states are SAFE, CAUTION, and HANDOFF;
- when uncertain whether the next substantial operation can finish cleanly, prefer a planned handoff.

## Planning is not execution

A Plan Part is sized for safe ChatGPT planning. A Micro Step is a logical work unit. An Implementation Batch groups work before broad validation. A GOAL is a continuous autonomous mission assigned to one implementation agent.

Do not infer one Codex run per plan file. Many plan files may belong to a small number of continuous GOALs.

## Source precedence

For software facts, when sources conflict:

1. current repository code and active architecture;
2. newest canonical/consolidated plan;
3. newer implementation plans and macroblocks;
4. historical plans and notes.

For workflow procedure, the canonical manual is authoritative and should be re-read instead of reconstructed from memory.

## Canonical manual

Repository:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git
