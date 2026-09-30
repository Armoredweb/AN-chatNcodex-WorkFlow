# AN-chatNcodex-WorkFlow

A compact workflow for using ChatGPT as the architecture/planning layer, GitHub as the source of truth and planning store, and Codex agents for prepared implementation work.

The objective is implementation readiness per token: spend reasoning where it matters, persist only what implementation needs, and avoid turning difficult thinking into oversized documents.

## Start here

User guides are self-contained and include the exact Project Instructions and startup prompts:

- English: `docs/USER_GUIDE.md`
- Português (Brasil): `docs/USER_GUIDE_PT-BR.md`

The single operational source of truth for ChatGPT is:

- `docs/WORKFLOW.md`

Older handoffs may still mention `docs/CHATGPT_PROTOCOL.md`; it is retained only as a small compatibility redirect.

Do not load the whole workflow repository into chat context. Read `docs/WORKFLOW.md` and only the project files needed for the current operation.

## Responsible use

This workflow is for legitimate software planning and resource-efficient orchestration. It is not intended to bypass ChatGPT, Codex, Work, account, rate, usage, safety, or platform limits.

Checkpoints, multiple chats, handoffs, and continuous mode divide work into bounded operations and preserve state. Product limits, safeguards, authorization boundaries, and platform rules always take precedence.

## Core ideas

- Current working-repository code and active architecture are authoritative for software facts.
- GitHub is the recommended planning backend; Library is a fallback.
- `MASTER_PLAN.md` stays compact; decomposition and detailed expansion happen later.
- Plan files contain the minimum complete implementation information. No filler, tutorials, repeated context, or prose added to reach a size.
- Line counts are safety guidance only. Small complete subplans are desirable.
- Context Safety and file size are independent.
- Continuous mode is opt-in and limited to four heavy ChatGPT operations per chat; operation 4 ends in a persisted handoff.
- Planning-file boundaries do not imply one Codex session or one test cycle per file.
- LUA-high is the default implementation role; SOL-high is retained only where strong preparation cannot remove substantial implementation reasoning.

## Repository contents

- `docs/WORKFLOW.md` — complete operational protocol.
- `docs/USER_GUIDE.md` — self-contained English guide.
- `docs/USER_GUIDE_PT-BR.md` — self-contained Portuguese guide.
- `docs/CHATGPT_PROTOCOL.md` — compatibility redirect for older handoffs.
- `LICENSE` — CC BY 4.0.

## License

Creative Commons Attribution 4.0 International (CC BY 4.0).

Suggested attribution: **AN-chatNcodex-WorkFlow by Armoredweb**.
