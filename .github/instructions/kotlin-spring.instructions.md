---
name: "Kotlin e Spring Boot"
description: "Convenções de Kotlin e Spring Boot. Aplicar ao gerar, refatorar ou revisar código Kotlin em qualquer camada."
applyTo: "**/*.kt"
---

# Kotlin + Spring Boot base

- Prefira `val`; use `var` só quando houver mutação real.
- Mantenha classes e funções pequenas; uma responsabilidade por tipo.
- Use `data class` para DTOs, comandos e respostas.
- Separe claramente entrada da API, regra de negócio e acesso a dados.
- Use `when` exaustivo e evite `if` aninhado quando um guard clause resolver.
- Prefira tipos explícitos nas bordas públicas e nomes descritivos em português técnico ou inglês consistente.
- Extraia mapeamentos repetidos para funções de extensão ou mappers pequenos.
- Não exponha entidades JPA fora da camada de persistência.

# Spring Boot base

- Controllers devem só orquestrar entrada, saída e validação.
- Services concentram regra de negócio e transações.
- Repositórios fazem apenas acesso a dados.
- Prefira exceções de domínio ou aplicação e tradução centralizada de erros.
- Use `@ConfigurationProperties` para configuração tipada.
- Prefira construtor com dependências mínimas e explícitas.
