# Instruções do repositório para o Copilot

## Sobre este repositório
Este repositório é uma **coleção de templates** de configuração do GitHub Copilot para projetos Kotlin + Spring Boot. Ele não contém código de aplicação — contém documentação, instruções e prompts prontos para serem copiados e adaptados em outros projetos.

Ao trabalhar aqui, o objetivo é criar ou melhorar os arquivos de configuração do Copilot, mantendo a consistência entre eles.

## Estrutura e convenções dos arquivos

### Instrução global — `.github/copilot-instructions.md`
- Aplicada automaticamente em todas as interações do repositório.
- Deve conter o contexto do projeto, stack, arquitetura e regras centrais.
- Regras detalhadas ficam nos arquivos de instrução por caminho.

### Instruções do agente autônomo — `AGENTS.md`
- Aplicadas ao usar o agente de codificação (cloud, CLI ou modo agente no VS Code).
- Documente: comandos de build/teste/lint, estrutura de pastas e convenções obrigatórias.
- O agente usa este arquivo para trabalhar sem precisar explorar o repositório a cada tarefa.

### Instruções por caminho — `.github/instructions/*.instructions.md`
- `applyTo:` (glob) ativa a instrução quando o arquivo aberto corresponde ao padrão.
- `description:` ativa por matching semântico quando o contexto da tarefa é relevante.
- `name:` define o rótulo exibido no editor; os três campos são opcionais mas recomendados.
- Exemplo: `applyTo: "**/*Controller.kt"` para regras de controller.
- O conteúdo deve ser curto, direto e sem duplicar o que está na instrução global.

### Prompt files — `.github/prompts/*.prompt.md`
- Frontmatter obrigatório: `description` e `name`.
- Campos opcionais: `agent` (`ask` | `agent` | `plan`), `model`, `tools`.
- São invocados manualmente no chat com `/nome-do-prompt`.
- Use para tarefas repetíveis com saída bem definida.

### Agent Skills — `.github/skills/<nome>/SKILL.md`
- Frontmatter obrigatório: `name` e `description`.
- Padrão aberto ([agentskills.io](https://agentskills.io)), portátil entre VS Code, Copilot CLI e cloud agent.
- Pode incluir scripts, exemplos e outros recursos além do `SKILL.md`.
- Use para capacidades especializadas que vão além de instruções simples.

### Custom agents — `.github/agents/*.agent.md`
- Frontmatter: `name`, `description`, `model`, `tools`.
- Campo opcional `handoffs:` define transições para outros agents (label, agent, prompt, send).
- Define persona, ferramentas disponíveis e comportamento esperado.
- Use para fluxos multi-step ou revisões com persona e escopo controlados.

## Contexto do projeto (preencher ao copiar para outro repositório)
- Projeto: `<project-name>`
- Objetivo: `<descreva o problema de negócio e o resultado esperado>`
- Domínio principal: `<domínio / subdomínios>`
- Público das APIs: `<interno / externo / parceiros>`

## Stack e convenções
- Linguagem: Kotlin
- Framework: Spring Boot
- Persistência: `<database>`, JPA/Hibernate ou `<outra>`
- Testes: `<test-framework>`, `<mocking-framework>`
- Build: `<build-command>`
- Testes: `<test-command>` — teste único: `<single-test-command>`
- Lint/qualidade: `<lint-command>`
- Formatação: `<format-command>`

## Arquitetura por camadas
- Mantenha controllers finos: recebem, validam e delegam.
- Centralize regras de negócio em services/use cases.
- Isole acesso a dados em repositories/clients.
- Separe DTOs da modelagem de domínio.
- Evite dependências cruzadas entre camadas.
- Prefira contratos explícitos entre API, aplicação, domínio e infraestrutura.

## Princípios Kotlin
- Prefira `val`; use `var` só quando houver mutação real.
- Use nulabilidade e safe calls antes de recorrer a `!!`.
- Prefira funções pequenas, expressivas e com um único propósito.
- Use data classes para DTOs e objetos de transporte.
- Prefira `when`, `let`, `run`, `also`, `apply` e coleções idiomáticas quando melhorarem a clareza.
- Explicite tipos em APIs públicas e em pontos onde a inferência atrapalhe a leitura.

## Princípios Spring
- Prefira injeção por construtor.
- Use `@ConfigurationProperties` para configuração tipada.
- Mantenha beans stateless sempre que possível.
- Evite lógica de negócio em controllers, filters e annotations.
- Prefira `ResponseEntity` e status HTTP corretos para contratos públicos.
- Configure comportamento por propriedades, não por valores espalhados no código.

## Validação
- Valide na borda: request body, query params, path variables e headers relevantes.
- Combine anotações Bean Validation com validações explícitas quando houver regra de domínio.
- Rejeite entradas inválidas cedo e com mensagens objetivas.
- Padronize erros de validação e não exponha detalhes internos.

## Segurança
- Nunca registre segredos, tokens, chaves, senhas ou dados sensíveis.
- Nunca confie em dados de entrada sem validação/sanitização.
- Presuma autenticação/autorização explícitas em endpoints protegidos.
- Evite concatenar SQL, URLs, headers ou comandos com dados não confiáveis.
- Trate exceções sem vazar stack trace, credenciais ou informações internas.

## Performance
- Evite N+1 queries e carregamentos desnecessários.
- Prefira paginação/limites em consultas e respostas grandes.
- Não carregue objetos ou listas completas quando um recorte resolver.
- Cuidado com streams, conversões e mapeamentos repetidos em caminhos quentes.
- Meça antes de otimizar; se houver troca de complexidade, explique no PR.

## Persistência
- Mantenha entidades e tabelas com responsabilidades claras.
- Prefira repositórios expressivos e pequenos.
- Controle transações no nível de serviço quando houver unidade de trabalho.
- Revise eager/lazy loading para evitar surpresa em runtime.
- Em migrações, preserve compatibilidade e dados existentes.

## Testes
- Cubra regras de negócio com testes unitários.
- Use testes de slice para controllers e camadas isoladas quando fizer sentido.
- Use testes de integração apenas quando o comportamento real do stack importar.
- Dê nomes descritivos aos testes e foque em comportamento.
- Sempre valide casos de erro, bordas e regressões críticas.

## Revisão de PR
- Procure bugs, regressões, N+1, falta de validação e contratos ambíguos.
- Verifique impacto em segurança, performance, persistência e observabilidade.
- Prefira mudanças pequenas, fáceis de revisar e com intenção clara.
- Se houver dúvida, explique o trade-off no comentário do PR.

## Regras de convivência entre instruções
- Esta instrução global se aplica a todas as interações.
- Se existir conflito com `.github/instructions/*.instructions.md`, prevalece a instrução mais específica.
- Não repita a mesma regra em múltiplos arquivos.
- Se uma seção ficar longa, mova o detalhe para um arquivo de instrução específico.
- Mantenha este arquivo curto o suficiente para o Copilot consumir sem perda de contexto.

## Comandos do projeto (preencher ao copiar para outro repositório)
- Build: `<build-command>`
- Testes (suite completa): `<test-command>`
- Teste único: `<single-test-command>` — ex.: `./gradlew test --tests "com.example.MyTest"`
- Lint: `<lint-command>`
- Formatação: `<format-command>`
- Execução local: `<run-command>`

## Checklist para novas mudanças
- [ ] Segue a arquitetura por camadas
- [ ] Respeita princípios de Kotlin e Spring
- [ ] Valida entradas corretamente
- [ ] Não expõe segredos nem dados sensíveis
- [ ] Evita N+1 e excesso de carga
- [ ] Tem testes relevantes
- [ ] Está pronto para revisão de PR
