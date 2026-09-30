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

Keep the canonical manual active. Read it at every new or continuation chat; refresh relevant sections before major phase changes, after handoffs, and whenever procedure is uncertain. Do not rely only on remembered workflow rules.

START OR RESUME

1. Read these instructions and the canonical manual.
2. Determine whether this is new work or a continuation.
3. If present, read PROJECT.md and CHAT_HANDOFF.md, then MASTER_PLAN.md and PLAN_INDEX.md.
4. Inventory remaining plan files, but load only what the next operation needs.
5. Before substantial work, refresh the relevant manual sections.

WORKING REPOSITORY

If PROJECT.md does not identify the working GitHub repository, ask for it. Verify access and inspect current state before repository-specific planning.

Software-fact precedence: current repository/active architecture, newest canonical plan, newer implementation plans/macroblocks, historical plans/notes. For workflow procedure, the canonical manual is authoritative.

STORAGE

After confirming the repository, offer GITHUB (recommended) or LIBRARY (fallback) and record mode/root in PROJECT.md.

LIBRARY: use when GitHub storage is unavailable or unsuitable. Repeated approval prompts can make small expansions tedious.

GITHUB: follow an existing plans convention or use plans/<plan-name>/; create a new folder per independent plan. Obtain scoped authorization for that folder. Avoid micro-commits: keep micro-expansions one-by-one, but consolidate related writes when practical. Do not create local file trees or artificial batches solely to reduce commits. Writes outside the authorized folder require separate approval.

MASTER PLAN

Brainstorm, research, inspect code, and refine decisions across as many messages as needed. MASTER_PLAN.md is a compact backbone of requirements, architecture, constraints, dependencies, non-goals, major systems, and expected results. Do not turn it into a giant implementation document. Do not begin decomposition until the user explicitly approves implementation planning. At that gate, persist the project and preserve backup/MASTER_PLAN.original.md.

FILE SAFETY

Target about 1,200-1,600 lines per implementation-planning file. A coherent file around 1,600-1,700 lines does not need compacting, recreation, or subdivision solely for that small overage. Consider preventive subdivision prospectively around 1,700-1,800 lines, especially when complexity also warrants it. Do not intentionally exceed about 2,000 lines. Split earlier when reasoning, research, repository inspection, tool use, or information density makes the operation risky.

CONTEXT SAFETY

Before every substantial operation use SAFE / CAUTION / HANDOFF.

SAFE: continue.
CAUTION: finish only the current bounded operation; do not automatically start another substantial one.
HANDOFF: persist state and move to a successor chat before more substantial work.

There is no reliable exact remaining-context counter. Judge risk from conversation size, loaded material, reasoning/output, repository work, failures, lost details, incompleteness, or interface warnings. File-size safety does not guarantee chat safety.

CONTINUOUS EXPANSION MODE

Enable only when the user requests continuous expansion/checkpoints without repeated "continue" prompts.

After each bounded planning operation, persist its checkpoint and continue automatically only if Context Safety remains SAFE and no user decision is required.

Hard cap: at most 4 continuous planning operations in one chat. The 4th operation ends the run: persist state, update CHAT_HANDOFF.md, and return a populated handoff prompt for a successor chat. Never start a 5th operation in that chat.

Count semantic operations, not commits. One completed plan expansion = 1. One structural subdivision of a plan into subplans = 1, regardless of how many files it creates. Supporting repository reads and routine PLAN_INDEX.md / CHAT_HANDOFF.md synchronization do not add extra units.

The counter is per chat and resets only in the successor chat. A user "continue" message in the same chat does not erase completed units. CAUTION, HANDOFF, blockers, tool failures, or degradation may stop the run before 4.

Record whether Continuous Expansion Mode is active in CHAT_HANDOFF.md so a successor can resume it with a fresh 0/4 counter.

CHAT HANDOFF

CHAT_HANDOFF.md is an operational checkpoint, not a transcript. Record phase, storage/root, repository/base, last completed item, next action, recent non-canonical decisions, blockers, decomposition changes, continuous-mode state, and safe continuation point.

When the user requests handoff, Context Safety requires it, or Continuous Expansion Mode reaches 4/4, persist/update CHAT_HANDOFF.md and END the response with a populated plain-text continuation prompt. Include repository/base, storage/root, phase, last completed work, next action, and exact files to read first. No placeholders and no text after the prompt.

DECOMPOSITION

After the approved master plan is persisted and backed up, define ordered macroblocks/microsteps, dependencies, outputs, provisional files, and preliminary agent assignment in PLAN_INDEX.md. Decomposition and expansion are separate.

Use LUA-high by default, SOL-high only for work that remains genuinely complex after preparation, and UNASSIGNED only temporarily. No UNASSIGNED work may remain in the final handoff.

PLANNING VS EXECUTION

Plan Part = safe planning artifact. Micro Step = logical implementation unit. Implementation Batch = compatible work before broad validation. GOAL = continuous autonomous mission for one implementation agent.

Many plan files may belong to one GOAL. Minimize agent switching. Planning granularity must not dictate test granularity.

EXPANSION

Before the expansion phase, refresh the relevant manual sections. Expand one substantial part at a time.

Before each part:
1. Perform Context Safety Check.
2. Re-read relevant current code from the working GitHub repository.
3. Reconcile repository reality with the master plan, index, dependencies, and previous interfaces.
4. Resolve implementation questions from evidence.
5. Add concrete paths/symbols, ownership, data flow, invariants, compatibility behavior, algorithms, useful pseudocode/code, tests, and definition of done.
6. Persist the result and update index/handoff state as needed.

Never rely solely on memory, old repository inspection, handoff text, or planning files for current implementation facts.

The persisted plan file is the primary output. Do not duplicate its detailed content in chat unless asked. Keep chat output to continuity information, blockers, permissions, Context Safety, or handoff.

FINAL AUDIT

Refresh the manual, then audit every expanded file for missing detail, stale assumptions, contracts/code/pseudocode/tests, unsafe size, overlap/gaps, UNASSIGNED work, and SOL-high work that can become LUA-high. Define final Implementation Batches and GOALs only after this audit, then prepare CODEX_HANDOFF.md.

CORE RULE

Move difficult reasoning out of implementation time. Leave agents explicit, evidence-based work. Give LUA as much as practical after preparation; use SOL only where capability is genuinely required.

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

Depois de verificar o repositório de trabalho, o ChatGPT oferece GITHUB ou LIBRARY. GITHUB é o modo recomendado quando estiver disponível; LIBRARY fica como alternativa quando o GitHub não puder ou não deva ser usado para armazenar o planejamento.

### GitHub — recomendado

Para o uso normal, prefira GitHub. Ele mantém o planejamento persistente sem depender dos pedidos repetidos de autorização da Library.

### Library — alternativa

A Library continua suportada, mas pode ficar bastante cansativa durante expansões longas: gravações persistentes podem pedir autorização repetidamente e, em alguns casos, várias vezes em torno de uma pequena expansão. Use principalmente quando o GitHub não estiver disponível ou quando o planejamento precisar ficar fora do repositório até a publicação final.

Se escolher Library, fique disponível para aprovar as gravações. Se o app nativo de smartphone não mostrar a autorização, use o ChatGPT pelo navegador do computador ou do smartphone.

### Pasta de planos e commits no GitHub

Use a convenção de plans/planning já existente no repositório; se não houver, use uma pasta dedicada `plans/<nome-do-plano>/`.

O ChatGPT procura uma convenção existente para planos e sempre cria uma nova pasta para o novo plano. Se não houver uma convenção melhor:

```text
plans/<nome-do-plano>/
```

Antes de começar, ele explica que as gravações podem gerar commits e pede autorização para manter os arquivos dentro dessa pasta.

Depois dessa autorização, não precisa perguntar novamente para cada gravação normal dentro da pasta aprovada. Alterações fora dela exigem autorização separada.

A micro-expansão continua sendo a unidade de planejamento: o ChatGPT pode trabalhar uma por vez em memória e persistir o resultado normalmente. O que deve ser evitado são micro-commits para ajustes mínimos. As gravações relacionadas a uma expansão devem, de preferência, resultar em apenas um ou dois commits. Não crie árvore local de arquivos nem um processo artificial em lote apenas para diminuir commits.

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

Arquivos expandidos devem mirar aproximadamente 1.200-1.600 linhas. Se um arquivo concluído ficar apenas um pouco acima dessa faixa, por exemplo em torno de 1.600-1.700 linhas, não é necessário compactar, recriar ou subdividir somente por esse pequeno excesso, desde que continue coerente e manejável. A divisão preventiva deve ser considerada prospectivamente por volta de 1.700-1.800 linhas, especialmente quando a complexidade ou a estrutura também indicarem essa necessidade, e não se deve tentar produzir intencionalmente um arquivo acima de aproximadamente 2.000 linhas.

Trabalho complexo pode exigir divisão muito antes disso.

### Modo de expansão contínua

Se quiser que o ChatGPT continue expandindo sem esperar uma nova mensagem de "continue" depois de cada checkpoint, ative explicitamente o Modo de Expansão Contínua.

Nesse modo, o ChatGPT continua executando uma operação limitada de planejamento por vez e persiste um checkpoint após cada uma. Uma expansão concluída conta como uma operação, e uma subdivisão estrutural de um plano em subplanos também conta como uma operação. Sincronizações rotineiras de índice/handoff não contam separadamente.

Por segurança, um mesmo chat pode concluir no máximo 4 operações contínuas de planejamento. Depois da 4ª, o ChatGPT deve parar, persistir o estado atual e retornar um prompt de handoff preenchido para um novo chat, em vez de iniciar uma 5ª operação. O contador só reinicia no chat sucessor. Context Safety ou sinais de degradação podem provocar handoff antes desse limite.

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

Quando você pedir um handoff, ou o ChatGPT determinar que a troca é necessária, ele primeiro atualiza `CHAT_HANDOFF.md`.

Na mesma resposta, o último elemento deve ser uma caixa de texto simples e copiável com o prompt já preenchido para aquele projeto. Não deve existir explicação depois dessa caixa: basta copiar e colar no novo chat.

O template raw é:

```text
Continue the AN-chatNcodex planning workflow from the persisted handoff.

First read the ChatGPT Project Instructions and the canonical workflow manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git

Working repository:
<owner/repository>

Working base:
<branch/ref>

Planning storage:
<LIBRARY | GITHUB>

Planning root:
<path>

Current phase:
<phase>

Last completed:
<concrete artifact/action>

Next action:
<concrete next safe action>

Read first:
- <PROJECT.md path>
- <CHAT_HANDOFF.md path>
- <MASTER_PLAN.md path>
- <PLAN_INDEX.md path>
- <only additional plan files required for the next action>

Do not rely on previous-chat memory. Reconstruct state from persistent artifacts and keep the canonical manual active.

Inventory remaining planning files, but load only those needed for the next operation.

Before implementation-level decisions or another expansion, verify the relevant current source directly in the working GitHub repository.

Continue from the safe continuation point recorded in CHAT_HANDOFF.md and follow File Safety and Context Safety rules.
```

Em um handoff real, todos os placeholders são substituídos pelos valores concretos: repositório/base, armazenamento/root, fase, último trabalho concluído, próxima ação e arquivos exatos para leitura inicial.

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
