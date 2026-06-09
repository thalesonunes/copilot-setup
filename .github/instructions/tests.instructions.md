---
name: "Testes"
description: "Convenções para arquivos de teste Kotlin: nomeação, escopo, mocks e cobertura por camada."
applyTo: "**/*Test.kt"
---

# Testes

- Prefira o menor teste que prove o comportamento.
- Nomeie testes pelo cenário e resultado esperado.
- Use unit test para regra pura, slice test para web e integração só quando o fluxo completo importar.
- Mantenha mocks mínimos e explícitos.
- Verifique casos de sucesso, erro e bordas relevantes.
- Evite testes frágeis presos a detalhes de implementação.
- Para controller, teste contrato, validação e status HTTP.
- Para persistência, valide queries, mapeamento e transações.
