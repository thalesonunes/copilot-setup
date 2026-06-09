# Instruções para o agente autônomo

Este arquivo fornece ao agente de codificação (cloud agent, CLI agent ou modo agente no VS Code) as informações necessárias para trabalhar neste repositório Kotlin + Spring Boot sem precisar explorar o código a cada tarefa.

## Stack e runtimes

- Linguagem: Kotlin `<versão>`
- Framework: Spring Boot `<versão>`
- Build: `<gradle|maven>` `<versão>`
- Java: `<versão>`

## Comandos essenciais

**Execute nesta ordem antes de criar ou atualizar um pull request:**

```sh
# 1. Build
<build-command>

# 2. Suite completa de testes
<test-command>

# 3. Lint e verificação de qualidade
<lint-command>
```

Para validar uma classe específica sem rodar a suite inteira:

```sh
<single-test-command>
# exemplo: ./gradlew test --tests "com.example.pacote.MinhaClasseTest"
```

## Estrutura do projeto

```
src/main/kotlin/<pacote-base>/
  api/              # controllers e DTOs de entrada/saída
  application/      # use cases e serviços de aplicação
  domain/           # entidades, value objects, interfaces de domínio
  infrastructure/   # repositórios, clients externos e configuração
src/test/kotlin/<pacote-base>/
  # espelha a estrutura principal
src/main/resources/
  application.yml             # configuração base
  application-<profile>.yml   # overrides por ambiente
```

## Convenções obrigatórias

- Não exponha entidades JPA fora da camada de infraestrutura.
- Controllers recebem e devolvem DTOs; regras de negócio ficam nos serviços.
- Coloque transações na camada de serviço, não no controller.
- Valide entrada com Bean Validation na borda da API.
- Nunca adicione segredos, tokens ou senhas ao código ou à configuração.
- Prefira `val`; use `var` apenas quando houver mutação real.
- Use `data class` para DTOs, comandos e respostas.

## Validação antes de finalizar

Confirme os itens abaixo antes de entregar a mudança:

1. O build compila sem erros ou novos warnings.
2. Todos os testes passam.
3. Nenhum segredo foi adicionado ao código ou à configuração.
4. A mudança não introduz N+1 queries.
5. Os contratos de API existentes não foram quebrados silenciosamente.
6. Novos comportamentos têm cobertura de teste correspondente.
