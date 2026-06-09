---
name: "Persistência"
description: "Regras para repositórios JPA, entidades, transações e prevenção de N+1 queries."
applyTo: "**/*Repository.kt"
---

# Persistência

- Coloque transações na camada de serviço, não no controller.
- Faça consultas pequenas e objetivas; prefira métodos de repositório legíveis.
- Evite carregar relações por acidente: revise `LAZY`, joins e projeções.
- Não faça processamento de negócio dentro de entidades ou repositórios.
- Prefira projeções ou consultas dedicadas quando a tela precisar de poucos campos.
- Use IDs, enums e tipos de data de forma consistente com o banco.
- Cuide de concorrência quando houver escrita simultânea; avalie bloqueio otimista quando fizer sentido.
- Não exponha entidades fora da camada de persistência.
