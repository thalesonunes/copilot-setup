---
name: "Configuração YAML"
description: "Regras para application.yml, profiles e externalização de configuração em projetos Spring Boot."
applyTo: "**/application*.yml"
---

# Configuração em YAML

- Mantenha o YAML simples e legível; evite duplicação entre profiles.
- Use placeholders para valores de ambiente e segredos.
- Agrupe chaves por domínio funcional.
- Prefira nomes estáveis e consistentes com as classes `@ConfigurationProperties`.
- Não coloque comportamento de negócio em configuração.
