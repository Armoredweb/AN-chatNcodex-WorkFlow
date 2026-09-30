# Guia de uso

Este é o guia completo para o usuário. Não existem arquivos de template separados para abrir ou manter.

As regras operacionais usadas pelo ChatGPT ficam em `docs/WORKFLOW.md`. As duas caixas copiáveis abaixo são todo o texto de configuração necessário.

## 1. Crie um Projeto no ChatGPT

Crie um novo Projeto e cole todo o bloco abaixo nas Instruções do Projeto:

```text
AN-chatNcodex WORKFLOW - PROJECT INSTRUCTIONS

Canonical workflow:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow/blob/main/docs/WORKFLOW.md

Read the canonical workflow at every new or continuation chat and refresh relevant sections before major phase changes or whenever procedure is uncertain.

PURPOSE

Use ChatGPT as the heavy architecture/planning layer, GitHub as the current-code source of truth and preferred planning store, and Codex agents for prepared implementation work.

This workflow is not intended to bypass ChatGPT, Codex, Work, account, rate, usage, safety, or platform limits. Checkpoints, handoffs, multiple chats, and continuous mode only divide legitimate work into bounded operations. Respect all product limits, safeguards, authorization boundaries, and platform rules.

START / RECOVERY

For a continuation, reconstruct state from PROJECT.md, CHAT_HANDOFF.md, MASTER_PLAN.md, and PLAN_INDEX.md. Inventory other plan files but load only what the next operation needs. Re-check relevant current repository source before implementation-level decisions.

If the working repository is unknown, ask for it and verify access.

STORAGE

Prefer GitHub planning storage in a dedicated plan-specific folder using the repository's existing convention or plans/<plan-name>/. Obtain scoped authorization for routine planning writes there. Library is a fallback when GitHub is unavailable or unsuitable; warn that repeated approvals may make it tedious.

MASTER PLAN / DECOMPOSITION

Keep MASTER_PLAN.md compact. Do not begin decomposition until the user explicitly approves implementation planning. At that gate preserve backup/MASTER_PLAN.original.md.

Decomposition and expansion are separate. Create dependency-oriented microsteps and provisional plan files first. LUA-high is the default implementation role; keep SOL-high only when strong preparation cannot remove substantial reasoning. UNASSIGNED is temporary only.

PLANNING EFFICIENCY

Optimize for implementation readiness per token. Do the difficult reasoning in ChatGPT, then write the smallest complete plan the implementation agent needs.

Do not add filler, repeated context, tutorials, generic explanation, or prose to reach a line count. Small complete subplans are good.

Line counts are safety guidance only. For larger files, about 1,200-1,600 lines is a normal working range; a coherent 1,600-1,700-line file does not need rewriting only for size. Consider subdivision around 1,700-1,800 and do not intentionally exceed about 2,000.

Prefer verified paths/symbols, direct instructions, concrete contracts, concise algorithms/code/pseudocode, relevant tests, and definition of done. Explain rationale only when needed to preserve a non-obvious constraint, compatibility rule, failure mode, or architecture decision.

CONTEXT SAFETY

Before every substantial operation use SAFE / CAUTION / HANDOFF.

SAFE: proceed.
CAUTION: finish only the current bounded operation, persist it, then reassess.
HANDOFF: do not start another substantial operation; persist state and move to a successor chat.

HEAVY OPERATIONS

A heavy operation is a substantial top-level task that independently warrants Context Safety. Supporting reads, verification, reasoning, persistence, and routine index/handoff updates stay inside the parent operation unless they become substantial work of their own.

In Manual Mode, perform at most one heavy operation per user invocation, persist it, and return control. A later "continue" may request one more. There is no fixed accumulated operation-count handoff threshold in Manual Mode; continue until the user requests handoff unless Context Safety requires one earlier.

Continuous Mode is opt-in and runs in blocks of 3 heavy operations. After each operation persist/reassess; after operation 3 of a block stop automatic execution and wait for the user to send "continue". A continue starts the next block in the same chat.

Allow at most 4 continuous blocks per chat: 3 + 3 + 3 + 3 = 12 heavy operations. After continuous operation 12, do not start operation 13; persist state and automatically produce the populated handoff. A successor chat starts fresh at block 1/4, 0/3, 0/12.

This cadence is a workflow safeguard, not a platform-limit claim. Context Safety, failures, blockers, or degradation may pause or hand off earlier.

EXPANSION

Before each substantial expansion: Context Safety, re-read relevant current source, reconcile dependencies/interfaces, resolve questions from evidence, write the smallest implementation-ready plan, persist it, and update index/handoff only as needed.

The persisted plan is the primary output. Do not duplicate detailed implementation content in chat unless asked.

HANDOFF

When requested by the user, required by Context Safety, or Continuous Mode reaches 12/12 in the current chat, persist operational state and END the response with a concrete plain-text continuation prompt. Include repository/base, storage/root, phase, last completed work, next safe action, exact files to read first, and continuous-mode state. No placeholders and no text after the prompt.

FINAL AUDIT

Audit every expanded plan for implementation readiness. Preserve implementation truth first. Then remove avoidable decisions left to LUA-high by resolving ownership, interfaces, algorithms, migration order, ambiguity, or other choices ChatGPT can settle from current source.

Where LUA-high would otherwise need difficult reasoning, add the minimum concrete contract, pseudocode, data shape, call sequence, or implementation-ready code needed to make the task mechanical. Then remove duplicated background, obsolete notes, tutorials, repeated rationale, and other text that does not affect implementation or validation.

Never trade away requirements, constraints, invariants, compatibility behavior, dependencies, validation, or architectural intent just to reduce tokens. Compression is subordinate to correctness.

Resolve UNASSIGNED work and re-evaluate SOL-high work for LUA-high after this preparation. Finalize Implementation Batches and GOALs only after the audit.

CORE RULE

Spend reasoning to simplify implementation. Heavy thinking is not a reason for large output.

```

## 2. Inicie o primeiro chat

Abra um chat dentro desse Projeto e envie:

```text
Read the instructions configured for this ChatGPT Project first.

Then read the canonical workflow:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow/blob/main/docs/WORKFLOW.md

Follow it for this project.

Determine whether this is a new workflow or a continuation with persistent planning state.

If continuing, reconstruct state from persistent artifacts instead of asking me to repeat prior work.

If the working GitHub repository is not already known, ask me for it and verify it before repository-specific planning.

Do not assume current code or architecture from conversation memory. Use the working repository as the source of truth.

For a new workflow, run the Storage Gate after verifying the repository.

```

O ChatGPT perguntará qual é o repositório GitHub de trabalho caso ainda não esteja registrado, verificará o repositório e estabelecerá onde o planejamento será persistido.

## 3. Uso responsável

O workflow serve para planejamento legítimo de software. Ele não existe para burlar limites do ChatGPT/Codex/Work, rate limits, sistemas de segurança, regras de conta ou limites de autorização.

Vários chats, checkpoints, handoffs e modo contínuo servem para dividir trabalho em operações limitadas e preservar estado. Os limites da plataforma sempre têm precedência.

A eficiência buscada é fazer o raciocínio pesado de arquitetura/planejamento no ChatGPT, persistir somente o resultado relevante para implementação e reservar Codex/Work para tarefas que realmente precisam de implementação ou execução autônoma.

## 4. Construa o master plan

Descreva o projeto ou mudança em quantas mensagens forem necessárias. O ChatGPT pode pesquisar, inspecionar o repositório, comparar alternativas e refinar requisitos.

Prompt útil:

```text
Construa/refine o master plan comigo. Mantenha-o compacto, verifique no código atual as premissas que dependem do repositório e não inicie a decomposição para implementação até eu aprovar explicitamente.
```

Quando estiver pronto:

```text
MASTER_PLAN aprovado. Inicie o planejamento para implementação seguindo o workflow canônico.
```

Nesse gate o ChatGPT preserva o baseline aprovado do master plan e inicia a decomposição.

## 5. Decomposição e expansão

Primeiro a decomposição define macroblocos, micro passos, dependências, arquivos provisórios e atribuições preliminares LUA-high/SOL-high. A expansão detalhada vem depois.

A expansão é otimizada por prontidão para implementação por token. Um problema difícil não precisa gerar um plano grande. Subplanos pequenos e completos são desejáveis.

As contagens de linhas são apenas referências de segurança. O ChatGPT não deve aumentar arquivos com tutoriais, contexto repetido, justificativas genéricas ou enchimento.

## 6. Operações pesadas e Modo Contínuo

Operação pesada é uma tarefa principal substancial, como expansão grande, subdivisão, decomposição, reconciliação de arquitetura/repositório, auditoria final, recuperação/migração ou preparação do handoff para Codex.

No Modo Manual normal, o ChatGPT executa no máximo uma operação pesada por mensagem sua, persiste o checkpoint e devolve o controle. Você pode continuar enviando `continue` para pedir mais uma operação pesada. Não existe um limite acumulado fixo para handoff no Modo Manual; você decide quando pedir o handoff, salvo se Context Safety exigir antes.

Para ativar continuação automática, envie:

```text
Ative o Modo Contínuo e continue automaticamente entre checkpoints seguindo o workflow canônico.
```

O Modo Contínuo funciona em blocos de 3 operações pesadas. O ChatGPT pode executar automaticamente três operações, persistindo e reavaliando entre elas. Depois da terceira, para e espera você enviar `continue`.

O mesmo chat pode executar quatro blocos:

`3 → continue → 3 → continue → 3 → continue → 3 → handoff`

Isso totaliza no máximo 12 operações pesadas contínuas no mesmo chat. Depois da operação 12, o ChatGPT prepara automaticamente o handoff em vez de iniciar a operação 13. O chat sucessor começa uma nova cadência 3×4.

Essa é uma salvaguarda experimental do workflow, não uma afirmação sobre limite da plataforma ChatGPT. Context Safety ou sinais de degradação podem interromper um bloco ou exigir handoff antes.

## 7. Handoff para outro chat

Você pode pedir handoff a qualquer momento:

```text
Prepare um handoff para um novo chat seguindo o workflow canônico.
```

O ChatGPT atualiza o estado persistido e termina a resposta com um prompt de continuação preenchido em texto simples. Copie essa última caixa para um novo chat no mesmo Projeto.

Você não precisa montar nem manter um template de continuação.

## 8. Auditoria final e Codex

Depois de expandir as partes necessárias, o ChatGPT revisa os planos arquivo por arquivo com um objetivo: deixar a implementação o mais fácil e mecânica possível sem perder a intenção da implementação.

Primeiro preserva todo comportamento necessário, restrições, invariantes, dependências, regras de compatibilidade e validações. Depois procura decisões que ainda foram deixadas para o LUA-high mas que o próprio ChatGPT pode resolver a partir do código atual. Onde ainda existir raciocínio difícil, adiciona apenas o contrato, algoritmo, pseudocódigo, formato de dados, sequência de chamadas ou código pronto para implementação necessário para tornar o trabalho mecânico. Só depois remove contexto duplicado, notas obsoletas, tutoriais, justificativas repetidas e texto que não afeta implementação ou validação.

A auditoria também resolve UNASSIGNED, reavalia SOL-high para LUA-high, define Implementation Batches e GOALs e prepara o handoff final para Codex. Economizar tokens é importante, mas nunca às custas de informação ou intenção de implementação.

Arquivos de planejamento são limites de segurança para o planejamento, não sessões obrigatórias do Codex nem ciclos de teste individuais. Um GOAL pode usar muitos arquivos.

## 9. Armazenamento

GitHub é recomendado porque o planejamento pode ser persistido diretamente em uma pasta dedicada e retomado por outro chat.

Library é alternativa. Ela pode pedir aprovações repetidas de escrita e por isso é menos conveniente para fluxos longos de micro-expansão.

O repositório GitHub de trabalho atual continua sendo a fonte de verdade para fatos de implementação independentemente do backend de planejamento.
