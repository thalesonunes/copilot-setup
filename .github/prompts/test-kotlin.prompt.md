---
description: Gerar testes focados para código Kotlin e Spring.
name: test-kotlin
agent: agent
---

Gere testes para o código selecionado com foco em comportamento, legibilidade e baixo acoplamento.

## Antes de escrever
- Identifique qual comportamento precisa ficar protegido.
- Use a stack e o estilo de teste já existentes no repositório.
- Prefira alterar o mínimo de arquivos necessário.

## Regras
- Prefira o menor teste que prove o comportamento.
- Use nomes claros, com cenário e resultado esperado.
- Cubra caminho feliz, bordas e falhas relevantes.
- Evite mocks excessivos; mocke apenas dependências externas ou custosas.
- Prefira testes de unidade para lógica pura e slice tests para camada web.
- Quando houver parametrização útil, use teste parametrizado em vez de duplicar cenários.

## Quando o código estiver difícil de testar
- Explique o bloqueio de forma objetiva.
- Sugira a menor refatoração necessária para tornar o comportamento testável.
- Evite propor uma reestruturação ampla se uma extração pequena já resolver.

## Saída esperada
- lista dos testes criados ou sugeridos
- o comportamento protegido por cada teste
- lacunas que continuam sem cobertura, se existirem
