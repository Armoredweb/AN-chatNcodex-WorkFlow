# Como usar o AN-chatNcodex-WorkFlow

Este guia é autossuficiente para o uso normal. Você não precisa abrir os arquivos da pasta `templates/` para começar. As instruções e os prompts exatos já estão reproduzidos abaixo em caixas copiáveis.

Os documentos operacionais e as instruções para ChatGPT/Codex permanecem em inglês para existir um único protocolo canônico. Os prompts humanos de brainstorm deste guia estão em português.

## 1. Crie um Projeto no ChatGPT

Crie um novo Projeto do ChatGPT para o trabalho que deseja planejar.

Copie TODO o texto abaixo para o campo de instruções do Projeto:

```text
AN-chatNcodex WORKFLOW - PROJECT INSTRUCTIONS

Canonical manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

Keep the canonical workflow manual as an active reference throughout the entire planning lifecycle. Read it at the start of every new or continuation chat. Refresh relevant sections before major phase transitions, after handoffs, and whenever workflow behavior is uncertain. Never rely only on remembered workflow rules.

START OR RESUME

1. Read these Project Instructions and the canonical manual.
2. Determine whether this is a new workflow or continuation.
3. If present, read PROJECT.md, then CHAT_HANDOFF.md.
4. For a continuation, then read MASTER_PLAN.md and PLAN_INDEX.md, inventory remaining plan files, and load only what the next operation needs.
5. Before substantial work, refresh the manual sections relevant to that phase.

WORKING REPOSITORY GATE

If the working GitHub repository is not recorded in PROJECT.md, ask the user for it. Verify that it exists and is accessible, then inspect its current state before repository-specific planning.

For software facts use this precedence: current repository/active architecture, newest canonical plan, newer implementation plans/macroblocks, historical plans/notes.

For workflow procedure, the canonical manual is authoritative. If memory, local instructions, handoff state, or planning artifacts appear to conflict with it, re-read the manual before continuing.

STORAGE GATE

After confirming the working repository, ask the user to choose LIBRARY or GITHUB. Record mode and planning root in PROJECT.md.

LIBRARY: use a dedicated persistent ChatGPT Library folder after the implementation-planning gate. Before each Library write, warn that a permission request may appear. When approval is required, use a web browser; do not rely on the native mobile app if it cannot present the request.

GITHUB: inspect for an existing plans/planning convention. Always create a new folder for an independent plan; otherwise default to plans/<plan-name>/. Explain that planning writes may create commits and obtain authorization to maintain files inside that folder. After scoped authorization, routine writes there need no repeated confirmation. Writes elsewhere require separate approval.

MASTER PLAN

Work with the user across as many messages as needed. Brainstorm, research, inspect code, and refine decisions.

The first canonical artifact is MASTER_PLAN.md: a compact backbone of requirements, architecture decisions, constraints, dependencies, non-goals, major systems, and expected results. Do not expand it into implementation-level code or large examples. Split the backbone into coherent subfiles if required.

Do not begin microstep decomposition until the user explicitly says the plan is ready for implementation planning. At that gate, persist the project and preserve backup/MASTER_PLAN.original.md as the approved baseline.

FILE SAFETY

Implementation-planning files should target about 1,200-1,600 lines. Consider preventive subdivision around 1,700-1,800 lines. Do not intentionally produce one above about 2,000 lines.

2,000 lines is a safety ceiling, not a target. Split earlier when reasoning, research, repository inspection, tool use, or information density raises timeout risk.

Evaluate expected size and complexity before drafting. Recursive subdivision is encouraged. File size and chat-context pressure are separate constraints.

CONTEXT SAFETY CHECK

Before every substantial operation, assess whether the current chat can safely finish it. Apply this during master-plan consolidation, repository-heavy analysis, decomposition, expansion, audits, research, and Codex handoff preparation.

SAFE: continue.
CAUTION: finish only the current bounded operation, then reassess.
HANDOFF: do not start the next substantial operation; persist state and move to a new chat.

There is no reliable exact remaining-context counter. Judge risk from accumulated conversation size, loaded material, required reasoning, expected output, repository inspection, repeated failures, loss of earlier details, abnormal incompleteness, or interface warnings.

If uncertain whether enough context remains for the next substantial operation, prefer a planned handoff. Output below the file-size ceiling does not guarantee chat safety.

CHAT HANDOFF

CHAT_HANDOFF.md is an operational checkpoint, not a transcript. Record current phase, storage mode/root, working repository/base, last completed item, next item, recent non-canonical decisions, blockers, decomposition changes, and safe continuation point.

When handoff is needed, persist or update it and give the user the canonical continuation prompt. A successor chat must reconstruct state from persistent files, re-read the manual, and re-check relevant live code instead of relying on assumed memory.

DECOMPOSITION

After the approved master plan is persisted and backed up, decompose it into ordered microsteps.

Decomposition and expansion are separate. During decomposition create PLAN_INDEX.md; identify macroblocks, dependencies, microsteps, outputs, order, preliminary agent assignment, and small skeleton files where useful. Do not fully expand implementation details.

Classify each microstep as LUA-high, SOL-high, or UNASSIGNED.

LUA-high is the default: lighter, faster, cheaper, less capable.
SOL-high is for work that remains genuinely complex after planning.
UNASSIGNED may exist during planning but not in the final handoff.

Do difficult reasoning in planning so as much implementation as practical can move from SOL to LUA.

PLANNING VS EXECUTION

Plan Part: safely sized ChatGPT planning artifact.
Micro Step: logical implementation unit.
Implementation Batch: several microsteps before broad validation.
GOAL: continuous autonomous mission assigned to one implementation agent.

Many plan files may belong to one GOAL. Minimize agent switching and prefer long continuous LUA or SOL GOALs.

Planning granularity must not dictate test granularity. Combine compatible work into broad batches and build or test at meaningful technical boundaries, testing earlier when necessary.

EXPANSION

Before starting the expansion phase, refresh the relevant manual sections.

Expand one substantial plan file at a time unless several are clearly small and safe.

Before each implementation part:
1. Perform a Context Safety Check.
2. Re-read relevant current code directly from the working GitHub repository.
3. Reconcile repository reality with the master plan, index, dependencies, and previous parts.
4. Resolve implementation questions from evidence.
5. Add concrete paths, symbols, ownership, data flow, invariants, compatibility behavior, algorithms, useful pseudocode/code where appropriate, tests, and definition of done.
6. Persist the file and update index/handoff state when needed.

Never rely solely on memory, old repository inspection, handoff text, or planning files for current implementation facts. If expansion becomes unsafe, subdivide before timeout.

During expansion, the persisted plan file is the primary output. Do not duplicate or summarize its implementation content in chat unless the user asks. Keep chat output to completion/subdivision status, required permissions, blockers/user decisions, next action, Context Safety, and handoff information.

FINAL OPTIMIZATION AUDIT

Before the final audit, refresh the relevant manual sections.

Audit every expanded file for missing detail, stale assumptions, useful code/pseudocode/contracts/tests, safe subdivision, overlap, UNASSIGNED work, and SOL-high tasks that can become LUA-high.

Then define final Implementation Batches and GOALs while minimizing agent switches. Only then prepare CODEX_HANDOFF.md. Refresh the manual again before preparing that handoff.

CORE RULE

Move difficult reasoning out of implementation time. Leave agents clear, evidence-based work. Give LUA as much as practical after preparation; use SOL only where capability is genuinely required.
```

As Project Instructions são texto simples e precisam permanecer dentro do limite de 8.000 caracteres das instruções de Projeto do ChatGPT.

## 2. Inicie o primeiro chat

Abra um novo chat dentro desse Projeto e envie:

```text
Read the instructions configured for this ChatGPT Project first.

Then read the canonical workflow manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

Keep that manual as an active reference throughout the workflow and refresh the relevant sections before major phase transitions or whenever workflow behavior is uncertain.

Follow the manual for this project.

Determine whether this is a new workflow or an existing one with persistent planning state.

If the working GitHub repository is not already known from persistent project state, ask me for it. Verify the repository before making repository-specific planning decisions.

Do not assume current code or architecture from conversation memory. Use the working GitHub repository as the source of truth for implementation facts.

If this is a new workflow, run the required Storage Gate after the working repository has been verified.
```

O ChatGPT deverá ler as instruções do Projeto e este manual, descobrir se o fluxo é novo ou uma continuação e, se necessário, perguntar qual é o repositório GitHub de trabalho.

Depois de receber o repositório, deve verificá-lo antes de tomar decisões dependentes do código.

Existem dois repositórios diferentes:

- repositório do workflow: este manual público e reutilizável;
- repositório de trabalho: o projeto de software que será planejado e implementado.

## 3. O manual deve continuar ativo durante todo o trabalho

O manual não serve apenas para inicializar o primeiro chat.

O ChatGPT deve relê-lo no início de todo chat novo ou de continuação e atualizar em contexto as seções relevantes antes de mudanças importantes de fase, depois de handoffs e sempre que houver dúvida sobre o procedimento.

Conversas longas não devem depender apenas da memória das regras do workflow.

Para fatos sobre implementação, o código atual do repositório GitHub de trabalho continua sendo a fonte principal.

## 4. Escolha onde o planejamento será salvo

Depois de verificar o repositório de trabalho, o ChatGPT oferece LIBRARY ou GITHUB.

### Library

Escolha Library quando quiser manter o planejamento incompleto separado do repositório até a publicação final.

Depois que o plano principal for aprovado para planejamento de implementação, o ChatGPT usa uma pasta persistente dedicada na Library.

Gravações na Library podem exibir pedidos de permissão. Fique disponível para aprovar. Se o app nativo de smartphone não conseguir mostrar essa autorização, use o ChatGPT no navegador do computador ou do smartphone.

### GitHub

Escolha GitHub quando aceitar commits incrementais dos planos e quiser evitar os pedidos frequentes de autorização da Library.

O ChatGPT procura uma convenção existente para planos e sempre cria uma nova pasta para o novo plano. Se não houver uma convenção melhor:

```text
plans/<nome-do-plano>/
```

Antes de começar, ele explica que as gravações podem gerar commits e pede autorização para manter os arquivos dentro dessa pasta.

Depois dessa autorização, não precisa perguntar novamente para cada gravação normal dentro da pasta aprovada. Alterações fora dela exigem autorização separada.

## 5. Faça o brainstorm e construa o plano principal

Você pode enviar requisitos durante várias mensagens, pesquisar, refletir, revisar escolhas e confrontar ideias com o código existente.

Um bom prompt para iniciar o brainstorm:

```text
Quero começar a construir o plano deste projeto.

Antes de criar o MASTER_PLAN, quero fazer brainstorm comigo. Analise o estado atual do repositório, faça perguntas quando necessário, identifique decisões ainda abertas e me ajude a consolidar requisitos, arquitetura, restrições e não-objetivos.

Consulte o manual canônico do workflow sempre que necessário e não comece a decomposição para implementação até eu dizer explicitamente que o plano está pronto.
```

Para continuar sem consolidar ainda:

```text
Continue o brainstorm. Ainda não quero consolidar o MASTER_PLAN. Continue verificando o repositório quando as decisões dependerem do estado atual do código.
```

Para fazer uma revisão antes da consolidação:

```text
Agora revise tudo o que decidimos e verifique novamente o repositório. Se houver contradições, decisões faltando ou premissas que não combinam com o código atual, aponte antes de consolidar o MASTER_PLAN.
```

O primeiro artefato canônico é `MASTER_PLAN.md`: uma espinha dorsal compacta com requisitos, decisões arquiteturais, restrições, dependências, não-objetivos, principais sistemas e resultado esperado.

Ele não deve virar um documento gigante de implementação ou ficar cheio de grandes blocos de código.

Se necessário, a espinha dorsal pode ser dividida em subarquivos mantendo um `MASTER_PLAN.md` principal compacto.

## 6. Revise e aprove o gate para planejamento de implementação

Quando acreditar que o plano principal está quase pronto, você pode usar:

```text
Acredito que o plano principal está pronto. Faça uma revisão final do MASTER_PLAN, releia as seções relevantes do manual e verifique novamente o repositório. Se encontrar algo que precise ser resolvido, aponte antes de iniciar a decomposição. Ainda não comece a decomposição até eu aprovar esta versão.
```

Depois de revisar e aceitar:

```text
MASTER_PLAN aprovado. Pode iniciar o planejamento para implementação seguindo o workflow canônico.
```

Nesse gate, o ChatGPT persiste o projeto, cria ou atualiza `PROJECT.md`, guarda `backup/MASTER_PLAN.original.md` e inicia a decomposição.

O backup representa a versão aprovada antes da expansão.

## 7. Primeiro decompor, depois expandir

O ChatGPT identifica macroblocos, dependências e micro passos e cria `PLAN_INDEX.md`.

Nesta etapa os arquivos podem ser apenas esqueletos. A expansão detalhada vem depois.

Cada micro passo recebe:

- LUA-high: preferencial/padrão;
- SOL-high: para trabalho que continua realmente complexo depois da preparação;
- UNASSIGNED: temporário enquanto faltam evidências.

Nenhum UNASSIGNED pode permanecer no handoff final.

## 8. Expansão

Depois que todos os micro passos estiverem definidos, começa a expansão.

Normalmente um arquivo substancial é expandido por invocação. Arquivos claramente pequenos podem ser agrupados quando for seguro.

Antes de cada expansão, o ChatGPT faz um Context Safety Check e lê novamente o código atual relevante diretamente no repositório GitHub de trabalho.

Arquivos expandidos devem mirar aproximadamente 1.200-1.600 linhas. Por volta de 1.700-1.800 deve considerar divisão preventiva e não deve tentar produzir intencionalmente um arquivo acima de aproximadamente 2.000 linhas.

Trabalho complexo pode exigir divisão muito antes disso.

### Resposta no chat durante a expansão

O arquivo persistido é o resultado principal.

O ChatGPT não deve copiar, explicar ou resumir no chat o conteúdo detalhado que acabou de gravar, a menos que você solicite.

A resposta deve ficar limitada ao necessário para continuar:

- arquivo concluído, atualizado ou subdividido;
- permissão que precisa ser aprovada;
- bloqueio ou decisão que depende de você;
- próximo arquivo/ação;
- aviso de Context Safety;
- necessidade de handoff.

## 9. Context Safety e troca de chat

O ChatGPT não possui um contador exato e confiável do contexto restante.

Antes de tarefas substanciais usa:

- SAFE: continua;
- CAUTION: termina somente a operação limitada atual e reavalia;
- HANDOFF: não inicia a próxima operação substancial neste chat.

Se houver dúvida sobre conseguir terminar a próxima tarefa grande com segurança, deve preferir um handoff planejado.

Isso vale na criação do MASTER_PLAN, decomposição, expansão, pesquisa, auditoria final e preparação do handoff para Codex.

## 10. Continue em um chat novo

Quando o ChatGPT recomendar a troca, ele deve primeiro atualizar `CHAT_HANDOFF.md`.

Abra outro chat no mesmo Projeto e envie:

```text
Read the instructions configured for this ChatGPT Project first.

Then read the canonical workflow manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

Keep that manual as an active reference and refresh the relevant sections before continuing the current phase or crossing any major phase boundary.

This chat continues an existing planning workflow.

Recover the project from its persistent planning storage. Start with PROJECT.md and CHAT_HANDOFF.md, then read MASTER_PLAN.md and PLAN_INDEX.md. Inventory the remaining planning files and load only those required for the next operation.

Do not rely on assumed context from the previous conversation. Reconstruct project state from persistent artifacts.

Before making implementation-level decisions or expanding another plan part, verify the relevant current code directly in the working GitHub repository.

Continue from the next safe action recorded in CHAT_HANDOFF.md and follow the workflow's File Safety and Context Safety rules.
```

O novo chat reconstrói o projeto pelos arquivos persistentes, relê o manual e não pede que você reconte toda a conversa anterior.

Ele começa por `PROJECT.md`, `CHAT_HANDOFF.md`, `MASTER_PLAN.md` e `PLAN_INDEX.md`, inventaria os outros arquivos e carrega apenas os necessários para a próxima operação.

Fatos de implementação relevantes são verificados novamente no repositório atual.

## 11. Auditoria final de otimização

Depois de expandir tudo, o ChatGPT percorre os arquivos procurando detalhes faltando, premissas antigas, oportunidades de adicionar contratos/código/pseudocódigo/testes, divisão adicional, sobreposições ou lacunas, UNASSIGNED e tarefas SOL-high que agora possam virar LUA-high.

## 12. Batches e GOALs

Quantidade de arquivos de plano não é quantidade de execuções do Codex.

Plan Part é uma unidade segura de planejamento. Micro Step é uma unidade lógica. Implementation Batch agrupa trabalho antes de validação ampla. GOAL é uma missão autônoma contínua para um agente.

Um GOAL pode usar dezenas ou centenas de arquivos.

O ChatGPT deve minimizar trocas manuais de agente e preparar o máximo possível para LUA-high.

Build/test completo deve acontecer em limites técnicos relevantes, não obrigatoriamente depois de cada pequeno arquivo.

## 13. Handoff para Codex

Depois da auditoria final, o ChatGPT prepara `CODEX_HANDOFF.md`.

No modo GitHub, o planejamento já está no repositório.

No modo Library, o ChatGPT pede autorização antes de publicar o pacote completo em uma pasta dedicada de planos no repositório de trabalho.

Os agentes então executam os GOALs na ordem planejada.

## Templates canônicos

As caixas acima são o caminho normal para o usuário. Também existem cópias raw canônicas:

- `templates/PROJECT_INSTRUCTIONS.txt`
- `templates/START_PROMPT.txt`
- `templates/CHAT_CONTINUATION_PROMPT.txt`

Quando um desses templates mudar, as cópias incorporadas nos dois guias devem permanecer idênticas.

Manual canônico:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git
