---
description: Revisar uma mudança crítica com foco em risco, regressões e rollback.
name: revisar-mudanca-critica
agent: agent
---

Revise a mudança como se ela fosse para produção hoje.

## Foco
- segurança
- perda ou corrupção de dados
- compatibilidade com versões anteriores
- migrações e rollback
- observabilidade e comportamento em falha
- impacto em usuários e integrações externas

## Instruções
- Seja mais rigoroso do que numa revisão comum.
- Priorize problemas que possam quebrar produção ou gerar incidente.
- Se algo depender de contexto ausente, declare a suposição.
- Não trate dúvidas de estilo como achado relevante.

## Saída
- resumo curto do risco geral
- achados bloqueantes
- achados importantes não bloqueantes
- recomendações de validação antes do merge
- pontos que precisam de plano de rollback
