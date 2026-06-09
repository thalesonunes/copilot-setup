---
description: Revisar a Pull Request de outro membro do time com foco em clareza, correção e feedback construtivo.
name: revisar-pr-colega
agent: agent
---

Revise a Pull Request indicada como um revisor sênior do time.

## Objetivo
- Entender a intenção da mudança antes de analisar o código.
- Identificar problemas reais que impactam comportamento, segurança ou manutenção.
- Oferecer feedback claro, objetivo e acionável.
- Distinguir o que é bloqueante do que é sugestão.

## Instruções
- Leia a descrição da PR e o ticket/issue vinculado antes de analisar a diff.
- Se não houver descrição suficiente, aponte isso como observação antes de prosseguir.
- Foque em correção, contratos, validação, persistência e testes.
- Não comente apenas estilo ou formatação.
- Não invente contexto que não está na diff ou no código.
- Para cada achado relevante, proponha uma alternativa concreta.
- Trate o autor com respeito: o objetivo é melhorar o código, não criticar a pessoa.

## Classificação dos achados
Use as seguintes categorias para cada comentário:

- **🚫 Bloqueante** — deve ser corrigido antes do merge. Impacta comportamento, segurança, dados ou contrato da API.
- **💡 Sugestão** — melhoria relevante mas não impeditiva. Vale discutir antes do merge.
- **📝 Observação** — dúvida, inconsistência menor ou ponto de atenção para o futuro. Não bloqueia.

## Entrega
- resumo curto da mudança com base na PR
- lista de achados classificados (🚫 / 💡 / 📝) com localização no código
- sugestão concreta para cada achado bloqueante ou sugestão relevante
- nota final: a PR está pronta para merge, precisa de ajustes pontuais ou exige revisão mais profunda?

## Dica
Para aprofundar a análise técnica de um arquivo específico, use `/review-spring` com o arquivo selecionado.
Para mudanças de alto risco, use `/revisar-mudanca-critica`.
