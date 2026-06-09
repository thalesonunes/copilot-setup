---
name: criar-endpoint-spring
description: Cria um endpoint REST completo em Kotlin + Spring Boot com controller, service, repository e testes unitários e de slice.
---

# Criar endpoint REST — Kotlin + Spring Boot

Use esta skill quando precisar adicionar um novo endpoint ao projeto. Ela garante que a geração segue a arquitetura em camadas do projeto e inclui os testes relevantes.

## Artefatos a gerar

Para cada novo endpoint, gere obrigatoriamente:

1. **DTO de entrada** — `data class` com anotações Bean Validation
2. **DTO de saída** — `data class` sem dependências de persistência
3. **Controller** — delega para o service; use `@Validated` e `ResponseEntity` quando status explícito for necessário
4. **Service** — encapsula a regra de negócio; controla transações com `@Transactional`
5. **Repository** — interface de acesso a dados (JPA ou similar)
6. **Testes**:
   - Unit test do service (mock de repositório com MockK ou Mockito)
   - Slice test do controller com `@WebMvcTest`

## Estrutura de pacotes esperada

```
api/
  <NomeFuncionalidade>Controller.kt
  dto/
    <NomeFuncionalidade>Request.kt
    <NomeFuncionalidade>Response.kt
application/
  <NomeFuncionalidade>Service.kt
domain/
  <NomeFuncionalidade>.kt           # entidade ou value object, se necessário
infrastructure/
  Jpa<NomeFuncionalidade>Repository.kt
```

## Regras de geração

- Prefira `val` em todos os data classes.
- O controller não acessa repositório diretamente.
- O service não depende de `HttpServletRequest` ou tipos web.
- Devolva `204 No Content` para operações sem body de resposta.
- Registre tratamento de erros no `@ControllerAdvice`, não no controller.
- Não logue dados pessoais, tokens ou informações sensíveis.
- Mantenha funções pequenas e com um único propósito.
