# Guia de uso

Este é o guia completo para o usuário. Não existem arquivos de template separados para abrir ou manter.

As regras operacionais usadas pelo ChatGPT ficam em `docs/WORKFLOW.md`. As duas caixas copiáveis abaixo são todo o texto de configuração necessário.

## 1. Crie um Projeto no ChatGPT

Crie um novo Projeto e cole todo o bloco abaixo nas Instruções do Projeto:

```text
AN-chatNcodex WORKFLOW — PROJECT INSTRUCTIONS

Canonical manual:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow/blob/main/docs/WORKFLOW.md

MANDATORY MANUAL RULE
Read the canonical manual directly at the start of every new or continuation chat before substantive work. Re-read the relevant sections before major phase transitions, after handoffs, before final planning/Codex handoff, and whenever procedure is uncertain. Never substitute remembered workflow rules for the manual. The manual is authoritative.

CORE OPERATION
Use the current working GitHub repository as source of truth for code/architecture. For continuation, reconstruct state from PROJECT.md, CHAT_HANDOFF.md, MASTER_PLAN.md, PLAN_INDEX.md, and only the Plan Parts needed next. Re-check current source before implementation-level decisions.

Whenever ChatGPT already needs to read implementation source for the current operation, use that same reading pass to look for material bugs, architecture inconsistencies, dead/obsolete paths, unnecessary complexity, avoidable hot-path work, and clear optimization opportunities. Do not start extra unrelated source browsing merely to hunt for issues; inspect only minimal adjacent context needed to classify a discovered issue.

Prefer GitHub as planning storage in a dedicated plan folder; Library is fallback. Respect scoped write authorization. For a bounded heavy operation that updates several related planning files, prefer one coherent commit when tooling allows; especially avoid Pass A/B micro-commits.

Optimize for implementation readiness per token: do difficult reasoning in ChatGPT, persist the shortest complete implementation-ready result, and never add filler or remove implementation truth merely to save tokens.

LUA-high is the default implementation target. Resolve avoidable decisions in planning and provide contracts/algorithms/code where that makes LUA mechanical. Retain SOL-high only after a final LUA-conversion audit; then optimize surviving SOL work for high-capability reasoning without unnecessary scaffolding. Never encode LUA/SOL assignment in Plan Part filenames or paths; assignments belong in indexes/metadata/references so they can change without renaming plans.

CONTEXT / EXECUTION
Before substantial work apply Context Safety: SAFE / CAUTION / HANDOFF.

Manual Mode: at most one heavy operation per user invocation, then persist and return control; no fixed accumulated handoff count.

Continuous Mode: 3 heavy operations per block, persist/reassess after each, then stop for user "continue". Up to 4 blocks (12 operations) per chat; after operation 12, mandatory persisted handoff. Context Safety may stop earlier. At each block boundary compact only transient CHAT_HANDOFF state; never substitute this for the full post-expansion audit.

FINALIZATION
After all Plan Parts are expanded, always run the full file-by-file optimization, LUA-conversion gate, cross-artifact Consistency Gate, GOAL/Batch construction, Expected Evidence definition, and Codex handoff described in the manual.

After implementation, validate Expected Evidence and run the Convergence Check until required planned behavior converges or a real blocker/user decision remains.

After convergence, ChatGPT—not Codex—performs Cleanup Preparation under the same Context Safety/heavy-operation rules, resolves cleanup decisions, and prepares a mechanical CODEX_CLEAN_HANDOFF.md for one LUA-high Cleanup GOAL. Cleanup never starts automatically: stop and wait for the user to explicitly start that GOAL. Luna executes the prepared cleanup; it does not design the cleanup. The closed cycle leaves a concise CLEANUP_FINDINGS.md for the next planning cycle.

HANDOFF
When handoff is requested/required, persist state and end the response with a concrete plain-text continuation prompt containing current repository/base, storage/root, phase, last completed work, next action, exact files to read first, and continuous-mode state. No placeholders and no text after it.

RESPONSIBLE USE
This workflow organizes legitimate software planning. It is not intended to bypass product, account, rate, usage, safety, authorization, or platform limits.
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

If CLEANUP_FINDINGS.md exists from a previous closed cycle, read it early and reconcile its still-live findings into the new planning cycle.

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

Os nomes dos planos permanecem neutros em relação ao agente: descrevem o trabalho, não se a atribuição atual é LUA-high ou SOL-high. Mudanças de agente atualizam índice/cabeçalho/metadados do GOAL sem exigir renomear o arquivo nem quebrar referências.

A expansão é otimizada por prontidão para implementação por token. Um problema difícil não precisa gerar um plano grande. Subplanos pequenos e completos são desejáveis.

As contagens de linhas são apenas referências de segurança. O ChatGPT não deve aumentar arquivos com tutoriais, contexto repetido, justificativas genéricas ou enchimento.

## 6. Operações pesadas e Modo Contínuo

Operação pesada é uma tarefa principal substancial, como expansão grande, subdivisão, decomposição, reconciliação de arquitetura/repositório, auditoria final, recuperação/migração ou preparação do handoff para Codex.

No Modo Manual normal, o ChatGPT executa no máximo uma operação pesada por mensagem sua, persiste o checkpoint e devolve o controle. Você pode continuar enviando `continue` para pedir mais uma operação pesada. Não existe um limite acumulado fixo para handoff no Modo Manual; você decide quando pedir o handoff, salvo se Context Safety exigir antes.

Para ativar continuação automática, envie:

```text
Ative o Modo Contínuo e continue automaticamente entre checkpoints seguindo o workflow canônico.
```

O Modo Contínuo funciona em blocos de 3 operações pesadas. O ChatGPT pode executar automaticamente três operações, persistindo e reavaliando entre elas. Depois da terceira, compacta somente o estado transitório de handoff, para e espera você enviar `continue`. Isso não substitui a otimização final completa depois da expansão.

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

## 8. Depois da expansão: auditoria, consistência, Codex e convergência

Depois de expandir todos os Plan Parts necessários, as compactações feitas a cada bloco de 3 operações **não** substituem a auditoria final completa. Durante os Passes A e B, o ChatGPT deve, quando prático, agrupar edições relacionadas em um commit coerente por unidade limitada de operação pesada, em vez de criar micro-commits para cada pequena edição de arquivo.

O ChatGPT então:

1. otimiza cada Plan Part sem perder a intenção da implementação;
2. remove decisões evitáveis do LUA-high e adiciona contratos/código concretos quando útil;
3. desafia toda atribuição SOL-high e só mantém SOL quando um planejamento melhor ainda não consegue tornar o trabalho seguramente mecânico para LUA;
4. otimiza o trabalho que realmente permanecer SOL para raciocínio de maior capacidade, sem scaffolding desnecessário;
5. executa um Consistency Gate entre `MASTER_PLAN → PLAN_INDEX → Plan Parts → repositório atual`, corrigindo inconsistências no arquivo que realmente é dono daquela informação;
6. define Implementation Batches e GOALs, marcando GOALs fundacionais que precisam validar antes do trabalho dependente;
7. define Expected Evidence para cada GOAL, provando o resultado pretendido em vez de depender apenas de "testes passaram";
8. cria o handoff final para Codex.

Depois da implementação, o ChatGPT executa um Convergence Check contra o plano canônico e o repositório atual. Diferenças obrigatórias são classificadas como ausentes, parciais, contraditórias ou não solicitadas, corrigidas em trabalho limitado e verificadas novamente até o comportamento necessário convergir ou restar um bloqueio/decisão real do usuário.

Arquivos de planejamento são limites de segurança do planejamento, não sessões automáticas do Codex nem ciclos individuais de teste. Um GOAL pode usar muitos Plan Parts.

## 9. Cycle Closure e limpeza

Um Convergence Check concluído torna o ciclo elegível para limpeza; ele não inicia a
limpeza.

O ChatGPT faz o Cleanup Preparation como trabalho de planejamento. Quando substancial,
essa preparação segue as mesmas regras de Context Safety, Modo Manual/Contínuo,
checkpoints, commits coerentes e handoff das outras operações pesadas. O ChatGPT resolve
precedência arquitetural, regras de exclusão/preservação, limpeza local de
build/generated, formato dos findings e validação limpa, então prepara
`CODEX_CLEAN_HANDOFF.md` especificamente para que LUA-high possa executá-lo de forma
mecânica.

Quando esse handoff estiver pronto, o ChatGPT para. Você inicia explicitamente o Cleanup
GOAL quando quiser executá-lo.

O Cleanup GOAL é uma missão contínua única para LUA-high. Ele reconcilia a arquitetura
permanente, confere a implementação contra o plano final, remove planejamento/histórico
concluído e resíduos classificados de arquitetura/build/generated, reconstrói a partir de
estado limpo, remove o próprio handoff temporário e deixa `CLEANUP_FINDINGS.md` contendo
somente reconciliações arquiteturais e divergências reais de implementação ainda abertas.

O próximo ciclo de planejamento lê esses findings cedo, absorve/resolve/rejeita/adia cada
um e não mantém findings antigos como arquivo histórico.

O ciclo pretendido é:

`Planejar -> Implementar -> Convergir -> Limpar -> alimentar o próximo Planejamento`

## 10. Armazenamento

GitHub é recomendado porque o planejamento pode ser persistido diretamente em uma pasta dedicada e retomado por outro chat.

Library é alternativa. Ela pode pedir aprovações repetidas de escrita e por isso é menos conveniente para fluxos longos de micro-expansão.

O repositório GitHub de trabalho atual continua sendo a fonte de verdade para fatos de implementação independentemente do backend de planejamento.
