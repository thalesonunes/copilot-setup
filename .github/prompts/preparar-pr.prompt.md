---
description: Preparar uma Pull Request com título, resumo, testes e riscos.
name: preparar-pr
agent: agent
---

Prepare uma Pull Request pronta para revisão.

## Objetivo
- Resumir a mudança com clareza.
- Explicar impacto funcional e técnico.
- Deixar explícito o que foi testado.
- Apontar riscos, pendências e rollback, se houver.

## Instruções
- Leia a diff e identifique o propósito principal da mudança.
- Estruture a PR para alguém que não viu o contexto anterior.
- Use português objetivo e tom profissional.
- Não invente testes, decisões ou resultados.
- Se faltar informação, marque como pendente em vez de supor.
- Se houver alteração de contrato de API, payload, banco ou comportamento visível externamente, classifique como breaking change e documente o impacto.
- Se houver issue ou ticket relacionado, inclua a referência (`Fixes #número`).

## Entrega
- título sugerido da PR (prefixo: feat/fix/refactor/chore/breaking)
- resumo executivo em 3 a 5 linhas
- tipo de mudança identificado
- lista de mudanças relevantes
- testes executados
- breaking changes, se houver
- impactos e riscos
- checklist de revisão
- sugestão de rollback, quando aplicável
- recomendação de usar `/revisar-mudanca-critica` se a mudança for de alto risco
