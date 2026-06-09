# Setup base para GitHub Copilot

Este arquivo é a porta de entrada para organizar o uso do GitHub Copilot neste repositório Kotlin + Spring Boot. A ideia é transformar o setup em uma base clara, reutilizável e replicável em outros projetos.

## Objetivo
- Padronizar o comportamento do Copilot no repositório.
- Separar política global, regras locais e automações reutilizáveis.
- Ajudar na geração de código, testes, revisão e apoio a PRs.
- Servir como referência para novos membros do time.

## Escopo
Este setup cobre:
- instruções globais do projeto
- instruções de modo agente (`AGENTS.md`)
- instruções por caminho/pacote
- prompt files reutilizáveis
- agent skills portáteis
- agentes customizados com personas, ferramentas e handoffs
- critérios de qualidade da documentação

Não cobre:
- regras de produto
- decisões arquiteturais fora do contexto do Copilot
- documentação de domínio ou de negócio

## Princípios
- Seja curto, direto e acionável.
- Evite duplicar regras em arquivos diferentes.
- Prefira exemplos concretos quando houver chance de ambiguidade.
- Separe regra permanente de instrução pontual.
- Escreva para orientar comportamento, não para explicar teoria.
- Mantenha tudo fácil de revisar e atualizar.

## Estrutura dos arquivos

### 1. Instruções globais do repositório
Arquivo: `.github/copilot-instructions.md`

É a base comum para todo o projeto. Use para definir:
- contexto do projeto
- stack e objetivos gerais
- arquitetura e fronteiras entre camadas
- convenções de Kotlin e Spring
- expectativas de teste
- comandos úteis de build, teste, lint e formatação

### 2. Instruções do agente autônomo
Arquivo: `AGENTS.md`

Aplicadas automaticamente ao usar o agente de codificação (cloud agent, CLI agent ou modo agente no VS Code). Use para documentar:
- como fazer build, teste e lint no projeto
- estrutura de pastas e onde encontrar as camadas
- convenções obrigatórias que o agente deve sempre respeitar
- checklist de validação antes de criar ou atualizar um PR

### 3. Instruções por caminho
Arquivo: `.github/instructions/*.instructions.md`

Use para regras específicas de contexto. Cada arquivo usa:
- `applyTo` (glob) para ativar automaticamente quando um arquivo correspondente está aberto
- `description` para ativar por matching semântico quando o contexto da tarefa é relevante
- `name` como rótulo exibido no editor

Cobrem: Kotlin, controllers e API, persistência, testes, segurança e configuração.

### 4. Prompt files
Arquivo: `.github/prompts/*.prompt.md`

Use para tarefas repetíveis e bem delimitadas. São invocados com `/nome-do-prompt` no chat. Cobrem: revisão de código, geração de testes, scaffold de feature e preparo de PR.

### 5. Agent Skills
Pasta: `.github/skills/<nome-da-skill>/SKILL.md`

Padrão aberto ([agentskills.io](https://agentskills.io)), portátil entre VS Code, Copilot CLI e cloud agent. Use para:
- encapsular workflows reutilizáveis com scripts e exemplos
- tarefas especializadas que vão além de instruções simples
- capacidades que devem funcionar em múltiplas ferramentas de IA

### 6. Custom agents
Arquivo: `.github/agents/*.agent.md`

Use quando precisar de:
- persona fixa com ferramentas e modelo específicos
- fluxo com múltiplas etapas
- handoffs entre agentes (planejar → revisar → replanejar)
- revisão ou implementação com foco e escopo controlados

## Como usar cada arquivo
- `.github/copilot-instructions.md`: descreva o padrão do repositório. Aplica-se a toda interação.
- `AGENTS.md`: documente build, testes, estrutura e convenções para o agente autônomo.
- `.github/instructions/*.instructions.md`: trate exceções e regras por contexto. Use `applyTo` ou `description`.
- `.github/prompts/*.prompt.md`: automatize tarefas recorrentes. Invoque com `/nome-do-prompt` no chat.
- `.github/skills/<nome>/SKILL.md`: encapsule capacidades portáteis com scripts e exemplos.
- `.github/agents/*.agent.md`: encapsule fluxos complexos com persona, ferramentas e handoffs.

## Comandos de chat para gerar customizações
O VS Code oferece comandos para gerar automaticamente os arquivos de configuração:

| Comando | O que gera |
|---|---|
| `/init` | `.github/copilot-instructions.md` baseado no repositório atual |
| `/create-instruction` | Arquivo `.instructions.md` com `applyTo` e conteúdo adequado |
| `/create-prompt` | Arquivo `.prompt.md` para uma tarefa recorrente |
| `/create-skill` | Pasta e `SKILL.md` para uma nova skill |
| `/create-agent` | Arquivo `.agent.md` com persona e ferramentas |

Use esses comandos como ponto de partida e refine manualmente.

## Guia de revisão de código
Escolha a ferramenta de revisão de acordo com o cenário:

| Cenário | Ferramenta |
|---|---|
| Revisar meu próprio código antes de abrir PR | `/review-spring` |
| Revisar a PR de outro membro do time | `/revisar-pr-colega` |
| Mudança crítica ou com impacto em produção | `/revisar-mudanca-critica` |
| Revisão autônoma e profunda com busca no codebase | agente `review-agent` |

As ferramentas são complementares: `/revisar-pr-colega` pode referenciar `/review-spring` para aprofundar a análise técnica de um arquivo específico.

## Fluxo recomendado
1. Defina o comportamento padrão em `.github/copilot-instructions.md`.
2. Crie o `AGENTS.md` com build, testes e estrutura do projeto.
3. Refine exceções em `.github/instructions/`.
4. Crie prompts para tarefas repetíveis.
5. Crie skills para capacidades portáteis com scripts ou exemplos.
6. Crie agents para fluxos mais complexos com handoffs.
7. Revise a documentação periodicamente para remover ruídos e contradições.

## Critérios de qualidade
Um bom setup deve ser:
- claro: fácil de entender em poucos segundos
- objetivo: sem blocos longos desnecessários
- consistente: sem regras conflitantes
- reutilizável: útil em mais de um cenário
- verificável: com comandos e expectativas explícitas
- compartilhável: bom o bastante para ser entendido por outro desenvolvedor sem contexto prévio

## Manutenção da documentação
- Atualize os arquivos quando o processo mudar.
- Revise comandos, nomes de pastas e convenções sempre que houver refatoração.
- Remova regras duplicadas ou obsoletas.
- Mantenha a estrutura alinhada entre o que está documentado e o que existe no repositório.
- Prefira pequenas revisões frequentes a grandes reescritas.

## Checklist final
- [ ] O arquivo global descreve o contexto e os comandos principais
- [ ] O `AGENTS.md` documenta build, testes e estrutura para o agente autônomo
- [ ] As instruções por caminho cobrem exceções reais e têm `name` e `description`
- [ ] Os prompts representam tarefas recorrentes
- [ ] As skills encapsulam capacidades reutilizáveis e portáteis
- [ ] Os agents têm escopo claro, ferramentas definidas e handoffs configurados
- [ ] Não há regras duplicadas sem necessidade
- [ ] A documentação está concisa e fácil de entender
- [ ] Os exemplos e caminhos citados existem no repositório

## Entregáveis criados como referência
- `AGENTS.md`
- `.github/copilot-instructions.md`
- `.github/instructions/kotlin-spring.instructions.md`
- `.github/instructions/api-web.instructions.md`
- `.github/instructions/tests.instructions.md`
- `.github/instructions/persistence.instructions.md`
- `.github/instructions/security.instructions.md`
- `.github/instructions/configuration.instructions.md`
- `.github/instructions/configuration-yaml.instructions.md`
- `.github/prompts/review-spring.prompt.md`
- `.github/prompts/revisar-pr-colega.prompt.md`
- `.github/prompts/gerar-testes.prompt.md`
- `.github/prompts/preparar-pr.prompt.md`
- `.github/prompts/revisar-mudanca-critica.prompt.md`
- `.github/agents/review-agent.agent.md`
- `.github/agents/planejamento-spring.agent.md`
- `.github/skills/criar-endpoint-spring/SKILL.md`
- `.github/pull_request_template.md`

## Regra de ouro
Se a instrução vale para todo o repositório, ela deve ir no arquivo global.
Se vale para o agente autônomo em modo de codificação, ela deve ir no `AGENTS.md`.
Se vale só para um contexto específico, ela deve ir em uma instrução por caminho ou em um prompt file.
Se encapsula uma capacidade portátil com scripts ou exemplos, ela deve ir em uma skill.
