# Como usar o AN-chatNcodex-WorkFlow

Este e o guia para o usuario. Os documentos operacionais, templates e instrucoes para ChatGPT/Codex permanecem em ingles para manter um unico protocolo canonico.

## 1. Crie um Projeto no ChatGPT

Crie um novo Projeto do ChatGPT para o trabalho que deseja planejar.

Copie o conteudo de templates/PROJECT_INSTRUCTIONS.md para a area de instrucoes do Projeto.

Essas instrucoes sao genericas. Elas apontam para o manual publico e permitem que um chat novo descubra como trabalhar mesmo quando nao possui o contexto da conversa anterior.

## 2. Inicie o primeiro chat

Abra um novo chat dentro do Projeto e cole o conteudo de templates/START_PROMPT.md.

O ChatGPT devera:

1. ler as instrucoes do Projeto;
2. ler o manual canonico deste repositorio;
3. descobrir se e um fluxo novo ou continuacao;
4. perguntar qual e o repositorio GitHub de trabalho caso ainda nao esteja registrado;
5. verificar a existencia e o estado desse repositorio antes de planejar.

Existem dois repositorios diferentes:

- repositorio do workflow: este manual publico e reutilizavel;
- repositorio de trabalho: o projeto de software que sera planejado e implementado.

## 3. Escolha onde os planos serao armazenados

Depois de confirmar o repositorio de trabalho, o ChatGPT oferecera duas opcoes: Library ou GitHub.

### Library

Escolha Library quando quiser manter o planejamento separado do repositorio GitHub ate ele estar completamente expandido e auditado.

Depois que o plano principal for aprovado para planejamento de implementacao, o ChatGPT cria uma pasta persistente dedicada na Library.

Gravacoes na Library podem mostrar pedidos de permissao. Fique disponivel para aprova-los. Caso o app nativo de smartphone nao mostre esses pedidos, use o ChatGPT pelo navegador. Pode ser navegador de desktop ou navegador do smartphone.

### GitHub

Escolha GitHub quando aceitar commits incrementais de planejamento e quiser evitar os pedidos frequentes de permissao da Library.

O ChatGPT verifica se o projeto ja possui uma pasta ou convencao para planos. Sempre cria uma nova subpasta para o novo plano. Quando nao existir uma convencao melhor, o padrao sera:

    plans/<nome-do-plano>/

Antes de comecar, o ChatGPT avisara que as gravacoes podem gerar commits e pedira autorizacao para manter os arquivos dentro dessa pasta.

Depois dessa autorizacao, nao e necessario pedir confirmacao para cada arquivo criado ou atualizado dentro da pasta autorizada. Alteracoes fora dela continuam exigindo autorizacao separada.

## 4. Construa o plano principal

Explique ao ChatGPT o projeto ou mudanca completa.

Isso pode acontecer durante muitas mensagens. Faca brainstorm, reflexao, pesquisas, comparacoes e perguntas. O ChatGPT tambem deve consultar o codigo atual sempre que isso ajudar nas decisoes.

O primeiro artefato canonico e MASTER_PLAN.md.

Ele e a espinha dorsal compacta do projeto e deve registrar:

- requisitos;
- decisoes arquiteturais;
- restricoes;
- dependencias;
- nao-objetivos;
- principais sistemas envolvidos;
- resultado esperado.

O plano principal nao deve ser uma expansao detalhada da implementacao e nao deve ficar cheio de grandes exemplos ou blocos de codigo.

Se ate a espinha dorsal ficar grande demais, o ChatGPT pode dividi-la em subarquivos mantendo um MASTER_PLAN.md principal compacto.

## 5. Libere o planejamento para implementacao

Continue discutindo e corrigindo o plano ate acreditar que ele esta pronto.

Quando voce disser explicitamente que o plano esta pronto para planejamento de implementacao, o ChatGPT atravessa esse gate.

Nesse momento ele:

1. persiste o projeto no armazenamento escolhido;
2. cria/atualiza PROJECT.md;
3. guarda backup/MASTER_PLAN.original.md;
4. inicia a decomposicao.

Esse backup representa a versao aprovada do plano antes da expansao.

## 6. Primeiro decompor, depois expandir

O ChatGPT pega o plano completo e identifica macroblocos e micro passos.

Nesta etapa ele cria PLAN_INDEX.md e, quando util, pequenos arquivos-esqueleto para cada passo.

Ainda nao e hora de expandir a implementacao.

Cada micro passo recebe uma classificacao inicial:

- LUA-high: agente preferencial, leve, rapido e mais barato;
- SOL-high: agente mais capaz e caro, reservado para trabalho realmente complexo;
- UNASSIGNED: classificacao temporaria enquanto faltam informacoes.

Nenhum UNASSIGNED pode permanecer no handoff final.

## 7. Expansao dos arquivos

So depois de todos os micro passos estarem identificados comeca a expansao.

Normalmente o ChatGPT expande um arquivo substancial por invocacao. Arquivos claramente pequenos podem ser tratados juntos quando for seguro.

Antes de expandir cada parte, o ChatGPT deve ler novamente o codigo atual relevante diretamente no repositorio GitHub de trabalho.

Ele nao deve depender apenas de memoria, de uma leitura antiga do repositorio ou dos proprios planos.

Arquivos expandidos devem mirar aproximadamente 1.200-1.600 linhas. Por volta de 1.700-1.800 linhas o ChatGPT deve considerar divisao preventiva e nao deve tentar produzir intencionalmente um arquivo acima de aproximadamente 2.000 linhas.

Complexidade de raciocinio, pesquisa e leitura de codigo pode exigir divisao muito antes disso.

Se necessario, um arquivo pode ser subdividido sucessivamente em A/B/C e depois novamente.

### O que o ChatGPT deve responder no chat

Durante a expansao, o arquivo persistido e o resultado principal.

O ChatGPT nao precisa copiar, explicar ou resumir no chat todo o conteudo que acabou de gravar, a menos que voce solicite.

A resposta deve ficar concentrada em informacoes necessarias para continuar:

- arquivo concluido, atualizado ou subdividido;
- permissao de armazenamento que precisa ser aprovada;
- bloqueio ou decisao que depende de voce;
- proximo arquivo ou acao;
- aviso de seguranca de contexto;
- necessidade de trocar de chat.

Isso economiza contexto para o trabalho de planejamento.

## 8. Seguranca de contexto e troca de chat

Chats muito longos podem comecar a perder confiabilidade. O ChatGPT nao possui um contador exato e confiavel dizendo quanto contexto ainda resta.

Antes de uma operacao grande ele deve fazer uma avaliacao preventiva:

- SAFE: pode continuar;
- CAUTION: termina somente a operacao pequena atual e reavalia;
- HANDOFF: nao inicia a proxima operacao substancial nesse chat.

Se houver duvida se a proxima tarefa grande cabe com seguranca, deve preferir uma troca planejada de chat.

Essa regra vale desde a criacao do MASTER_PLAN ate decomposicao, expansao, pesquisas, auditoria final e preparacao do handoff para o Codex.

Quando for necessario trocar, o ChatGPT atualiza CHAT_HANDOFF.md e entrega o prompt para o novo chat.

## 9. Continue em um chat novo

Abra outro chat dentro do mesmo Projeto e cole templates/CHAT_CONTINUATION_PROMPT.md.

O novo chat deve reconstruir o contexto usando os arquivos persistentes, nao tentando adivinhar o que aconteceu na conversa anterior.

A ordem inicial e:

1. instrucoes do Projeto;
2. manual do workflow;
3. PROJECT.md;
4. CHAT_HANDOFF.md;
5. MASTER_PLAN.md;
6. PLAN_INDEX.md.

Depois ele inventaria os outros arquivos e carrega integralmente apenas aqueles necessarios para a proxima operacao.

Sempre que precisar de fatos sobre a implementacao, volta ao codigo atual do GitHub.

## 10. Auditoria final de otimizacao

Depois que todos os arquivos estiverem expandidos, o ChatGPT percorre o plano arquivo por arquivo.

Ele procura:

- detalhes ainda faltando;
- premissas antigas sobre o codigo;
- contratos, pseudocodigo, codigo, algoritmos e testes que possam ser preparados;
- arquivos que ainda devam ser subdivididos;
- sobreposicoes e lacunas;
- tarefas ainda UNASSIGNED;
- tarefas SOL-high que, depois de bem preparadas, possam ser executadas pelo LUA-high.

A intencao e deixar o trabalho pesado de raciocinio pronto antes da implementacao.

## 11. Batches e GOALs

Quantidade de arquivos de plano nao e quantidade de execucoes do Codex.

O ChatGPT agrupa micro passos compativeis em Implementation Batches e GOALs maiores.

Um GOAL e uma missao autonoma continua para um agente. Ele pode ler dezenas ou centenas de arquivos de plano durante a mesma execucao.

A troca manual entre agentes deve ser minimizada.

A preferencia e entregar o maximo possivel ao LUA-high. O SOL-high entra quando a tarefa ainda exigir maior capacidade mesmo depois da preparacao.

Tambem nao e necessario fazer um build/test completo depois de cada pequeno arquivo. Os testes devem ocorrer em limites tecnicos relevantes, ou antes quando forem necessarios para continuar com seguranca.

## 12. Handoff para implementacao

No final da auditoria o ChatGPT prepara CODEX_HANDOFF.md com a ordem dos GOALs, arquivos, dependencias e validacoes.

Se o armazenamento escolhido foi GitHub, todo o planejamento ja esta no repositorio.

Se foi Library, o ChatGPT pede autorizacao antes de publicar o pacote final de planejamento no local correto do repositorio de trabalho.

Depois disso os agentes de implementacao podem executar os GOALs.

## Prompts para copiar

Primeiro chat:
templates/START_PROMPT.md

Troca/continuacao de chat:
templates/CHAT_CONTINUATION_PROMPT.md

Manual canonico:
https://github.com/Armoredweb/AN-chatNcodex-WorkFlow.git
