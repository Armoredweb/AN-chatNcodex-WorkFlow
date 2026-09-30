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

For planning persistence, GitHub is recommended when available. Library remains a fallback because repeated write approvals can make long micro-expansion workflows tedious. In GitHub mode, preserve micro-expansion granularity but consolidate related writes to avoid unnecessary micro-commits, preferably one or two commits per expansion.

## Core flow

    Project instructions
        -> new ChatGPT chat
        -> read/refresh this manual
        -> identify and verify working GitHub repository
        -> choose planning storage: GitHub recommended / Library fallback
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
- a small overage around 1,600-1,700 lines is acceptable and does not require compacting, recreating, or subdividing an otherwise coherent file;
- consider preventive subdivision prospectively around 1,700-1,800 lines, especially when complexity or structure also warrants it;
- do not intentionally exceed about 2,000 lines;
- split earlier when reasoning, research, repository inspection, or information density makes the operation risky.

Chat safety:

- there is no exact reliable remaining-context counter;
- ChatGPT performs a Context Safety Check before substantial operations;
- states are SAFE, CAUTION, and HANDOFF;
- when uncertain whether the next substantial operation can finish cleanly, prefer a planned handoff;
- every requested/triggered handoff ends with a concrete plain-text continuation prompt ready to copy into the next chat.

## Bounded continuous expansion

When explicitly enabled by the user, ChatGPT may expand plans continuously across automatic checkpoints instead of stopping for a "continue" message after every part.

The mode is deliberately bounded:

- work remains one bounded expansion or subdivision at a time;
- each completed plan expansion counts as 1 operation;
- one structural subdivision into subplans also counts as 1 operation;
- routine checkpoint/index/handoff synchronization does not count separately;
- maximum: 4 continuous planning operations per chat;
- after the 4th operation, ChatGPT persists state and produces a handoff to a successor chat instead of starting a 5th;
- the counter resets only in the successor chat;
- Context Safety or degradation can force an earlier handoff.

This limit is based on planning operations rather than Git commit count because one semantic operation may require a different number of persistence writes depending on the available tooling.

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

## License

This project is licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0).

You may share and adapt the material for any purpose, including commercially, provided appropriate attribution is given.

Suggested attribution: **AN-chatNcodex-WorkFlow by Armoredweb** — https://github.com/Armoredweb/AN-chatNcodex-WorkFlow

See `LICENSE` for the full legal terms.
