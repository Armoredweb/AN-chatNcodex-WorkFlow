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

HEAVY-OPERATION LIMIT

Count heavy top-level ChatGPT operations in every chat, whether Continuous Mode is active or not. A task that independently warrants Context Safety normally counts as 1 unit. Required reads, verification, reasoning, persistence, and routine index/handoff updates are included in that parent unit.

Hard limit: 4 heavy operations per chat. A user "continue" does not reset the counter; only a successor chat starts at 0/4.

In manual mode, after operation 4 persist/update handoff state, recommend a new chat, and do not start operation 5. Do not emit the full handoff prompt unless requested; if the next message is merely "continue", perform the handoff instead of heavy operation 5.

Continuous Mode is opt-in. When active, use the same counter but automatically generate the populated handoff after operation 4. Safety/degradation may force earlier handoff in either mode.

EXPANSION

Before each substantial expansion: Context Safety, re-read relevant current source, reconcile dependencies/interfaces, resolve questions from evidence, write the smallest implementation-ready plan, persist it, and update index/handoff only as needed.

The persisted plan is the primary output. Do not duplicate detailed implementation content in chat unless asked.

HANDOFF

When requested/required or continuous mode reaches 4/4, persist operational state and END the response with a concrete plain-text continuation prompt. Include repository/base, storage/root, phase, last completed work, next safe action, exact files to read first, and continuous-mode state. No placeholders and no text after the prompt.

FINAL AUDIT

Before Codex handoff, remove stale assumptions, gaps, unnecessary prose, UNASSIGNED work, and avoidable SOL-high work. Finalize Implementation Batches and GOALs only after that audit.

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

## 6. Limite de operações pesadas e Modo Contínuo

O limite de 4 operações pesadas vale para todo chat, inclusive no uso manual normal em que você envia `continue` entre as etapas.

Operação pesada é uma tarefa principal substancial, como expansão grande, subdivisão, decomposição, reconciliação de arquitetura/repositório, auditoria final, recuperação/migração ou preparação do handoff para Codex.

No modo manual, depois da operação 4 o ChatGPT persiste o checkpoint e recomenda mudar para um novo chat. Ele não deve iniciar a operação 5. Se você então enviar apenas `continue`, o ChatGPT deve preparar o handoff em vez de executar outra operação pesada.

Para continuar automaticamente depois de cada checkpoint, envie:

```text
Ative o Modo Contínuo e continue automaticamente entre checkpoints seguindo o workflow canônico.
```

O Modo Contínuo usa o mesmo contador de 4 operações, mas após a operação 4 retorna automaticamente o prompt de handoff preenchido. O chat sucessor começa em 0/4. Context Safety pode forçar handoff antes disso em qualquer modo.

## 7. Handoff para outro chat

Você pode pedir handoff a qualquer momento:

```text
Prepare um handoff para um novo chat seguindo o workflow canônico.
```

O ChatGPT atualiza o estado persistido e termina a resposta com um prompt de continuação preenchido em texto simples. Copie essa última caixa para um novo chat no mesmo Projeto.

Você não precisa montar nem manter um template de continuação.

## 8. Auditoria final e Codex

Depois de expandir as partes necessárias, o ChatGPT faz uma auditoria final:

- remove ambiguidades e premissas antigas;
- remove texto desnecessário;
- resolve trabalhos UNASSIGNED;
- transforma SOL-high em LUA-high quando melhor preparação tornar isso seguro;
- define Implementation Batches e GOALs;
- prepara o handoff final para Codex.

Arquivos de planejamento são limites de segurança para o planejamento, não sessões obrigatórias do Codex nem ciclos de teste individuais. Um GOAL pode usar muitos arquivos.

## 9. Armazenamento

GitHub é recomendado porque o planejamento pode ser persistido diretamente em uma pasta dedicada e retomado por outro chat.

Library é alternativa. Ela pode pedir aprovações repetidas de escrita e por isso é menos conveniente para fluxos longos de micro-expansão.

O repositório GitHub de trabalho atual continua sendo a fonte de verdade para fatos de implementação independentemente do backend de planejamento.
