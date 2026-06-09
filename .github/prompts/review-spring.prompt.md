---
description: Revisar uma mudança Kotlin e Spring com foco em correção, performance e manutenção.
name: review-spring
agent: agent
---

Revise o código ou diff selecionado com mentalidade de produção.

## Checklist
1. Kotlin: null-safety, imutabilidade, legibilidade e uso idiomático.
2. Spring: injeção, escopo de beans, transações e binding de configuração.
3. API: validação, tratamento de erro, status code e formato da resposta.
4. Persistência: N+1, queries ineficientes, loading tardio e fronteiras transacionais.
5. Testes: lacunas de cobertura, asserções fracas e mocks frágeis.
6. Segurança: dados sensíveis logados, entradas não sanitizadas, autorização ausente, segredos no código.

## Regras
- Não destaque apenas estilo.
- Não invente contexto ausente.
- Priorize achados com impacto real em comportamento, estabilidade ou manutenção.

## Saída esperada
- resumo curto
- achados ordenados por prioridade
- sugestão concreta para cada achado
- observação final sobre o risco da mudança
