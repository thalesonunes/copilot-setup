---
description: Gerar um plano prático de testes para uma mudança Kotlin e Spring.
name: gerar-testes
agent: agent
---

Gere um plano de testes prático para a mudança selecionada.

## Instruções
- Foque no comportamento mais importante primeiro.
- Separe testes obrigatórios de testes opcionais.
- Prefira cenários pequenos e verificáveis.
- Considere regressões, bordas e falhas de validação.
- Se houver integração com banco, fila, cache ou HTTP, cubra o contrato relevante.

## Saída
- casos de teste sugeridos
- objetivo de cada caso
- tipo de teste recomendado
- dados de entrada necessários
- observações sobre mocks, fixtures ou massa de dados

## Critérios
- Evite duplicar cobertura já existente.
- Não sugira testes frágeis sem valor de regressão.
- Se a cobertura ideal exigir refatoração, diga exatamente o que mudar.
