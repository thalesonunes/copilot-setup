---
name: tratamento-erros-api
description: Cria um @ControllerAdvice global com respostas de erro padronizadas para APIs Kotlin + Spring Boot.
---

# Tratamento de erros global — Kotlin + Spring Boot

Use esta skill quando precisar criar ou atualizar o handler global de excecoes da API. Ela garante respostas consistentes para erros de validacao, regras de negocio, erros de infraestrutura e excecoes nao tratadas.

## Artefatos a gerar

1. **ErrorResponse** — `data class` padronizada com `status`, `message`, `timestamp` e `details` opcionais
2. **ApiExceptionHandler** — classe anotada com `@RestControllerAdvice` contendo handlers para cada tipo de excecao
3. **Excecoes de dominio** — `sealed class` ou hierarquia de excecoes semanticas (opcional, se o projeto nao tiver)

## Estrutura esperada

```
api/
  exception/
    ErrorResponse.kt
    ApiExceptionHandler.kt
domain/
  exception/
    BusinessException.kt          # excecao de regra de negocio
    ResourceNotFoundException.kt  # 404
    InvalidStateException.kt      # 409
```

## Status HTTP e excecoes cobertas

| Excecao | Status |
|---|---|
| `MethodArgumentNotValidException` | 400 |
| `HttpMessageNotReadableException` | 400 |
| `MissingServletRequestParameterException` | 400 |
| `ConstraintViolationException` | 400 |
| `ResourceNotFoundException` (dominio) | 404 |
| `HttpRequestMethodNotSupportedException` | 405 |
| `InvalidStateException` (dominio) | 409 |
| `HttpMediaTypeNotSupportedException` | 415 |
| `BusinessException` (dominio) | 422 |
| `DataIntegrityViolationException` | 409 |
| Qualquer outra nao tratada | 500 |

## Regras de geracao

- `ErrorResponse.details` usa lista de strings, nao o objeto BindingResult completo.
- Nunca exponha stack traces ou mensagens tecnicas nas respostas de producao.
- Use `@Profile` para diferenciar mensagens entre ambientes se necessario.
- Excecoes de dominio devem ter mensagens em portugues (ou idioma do projeto).
- Nao logue dados pessoais, tokens ou informacoes sensiveis nos handlers.
- O handler de 500 deve logar o erro completo no servidor (via logger).
- Excecoes de validacao devem retornar o nome do campo e a mensagem por campo.
