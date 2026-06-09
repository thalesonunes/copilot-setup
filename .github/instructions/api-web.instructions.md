---
name: "API e Web"
description: "Regras para controllers, endpoints REST, validação de entrada e contratos HTTP."
applyTo: "**/*Controller.kt"
---

# API e Web

- Receba e devolva DTOs; não use entidade de persistência na API.
- Valide a entrada no limite com Bean Validation e `@Validated`.
- Use `ResponseEntity` só quando status, headers ou body exigirem controle explícito.
- Retorne códigos HTTP previsíveis e consistentes com a operação.
- Mantenha controllers finos: sem regra de negócio, sem acesso direto a repositório.
- Faça paginação, ordenação e filtros como parâmetros explícitos do endpoint.
- Converta exceções em respostas claras em um handler central.
- Registre somente dados úteis para diagnóstico; nunca logue payload sensível.
