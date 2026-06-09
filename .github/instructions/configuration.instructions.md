---
name: "Configuração"
description: "Regras para classes @ConfigurationProperties e leitura de propriedades tipadas."
applyTo: "**/*Properties.kt"
---

# Configuração

- Agrupe configuração por domínio funcional, não por tecnologia.
- Prefira propriedades tipadas com `@ConfigurationProperties`.
- Defina defaults próximos da classe de configuração.
- Não leia `env` ou `System.getProperty` diretamente na lógica de negócio.
- Mantenha segredos fora do código e dos exemplos.
- Separe configuração de runtime, profile e teste com clareza.
- Evite chaves soltas em vários arquivos `application*.yml` quando uma classe tipada resolver.
