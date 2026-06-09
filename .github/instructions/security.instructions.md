---
name: "Segurança"
description: "Regras para configuração Spring Security, autorização, autenticação e proteção de dados sensíveis."
applyTo: "**/*Security*.kt"
---

# Segurança

- Autorize no ponto de entrada; não confie em checagens tardias dentro do serviço.
- Use roles e authorities explícitas, com nomes consistentes.
- Prefira recursos nativos do Spring Security antes de soluções próprias.
- Nunca logue senha, token, chave ou header sensível.
- Valide claims, headers e identificadores externos antes de usá-los.
- Não desative proteções por padrão; cada exceção de segurança deve ter motivo claro.
- Trate falhas de autenticação e autorização com respostas previsíveis.
