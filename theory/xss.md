# XSS (Cross-Site Scripting)

O Cross-Site Scripting (XSS) é uma vulnerabilidade que permite a um atacante injetar scripts maliciosos (geralmente JavaScript) em páginas web visualizadas por outros usuários.

## Tipos de XSS

### 1. XSS Refletido (Reflected)
O script malicioso é "refletido" de uma aplicação web para o navegador da vítima. Geralmente é entregue via um link por e-mail ou outra mensagem.
*Exemplo:* Um parâmetro de busca que exibe o termo pesquisado na tela sem sanitização.

### 2. XSS Armazenado (Stored)
O script malicioso é armazenado permanentemente no servidor (ex: banco de dados, fórum, campo de comentário). Quando o usuário visita a página afetada, o script é executado.

### 3. XSS Baseado em DOM
A vulnerabilidade existe no código do lado do cliente (JavaScript) em vez de no lado do servidor. O script manipula o Document Object Model (DOM).

## Impacto
- Roubo de cookies de sessão.
- Sequestro de conta.
- Redirecionamento para sites maliciosos.
- Alteração do conteúdo da página (Defacement).

## Como Prevenir
- **Escaping de Saída**: Converter caracteres especiais em entidades HTML.
- **Content Security Policy (CSP)**: Camada de segurança que ajuda a detectar e mitigar ataques XSS.
- **Uso de Frameworks Modernos**: React, Angular e Vue possuem proteções automáticas contra XSS.