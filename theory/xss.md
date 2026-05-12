# 💉 XSS (Cross-Site Scripting): Manipulando o Navegador

O XSS ocorre quando uma aplicação web permite que dados não confiáveis (geralmente enviados por um usuário) sejam incluídos em uma página sem a devida validação ou codificação. Isso permite que um atacante execute scripts (geralmente JavaScript) no contexto do navegador da vítima.

## 🧠 A Lógica do Ataque
O navegador não sabe distinguir o que é um script legítimo do desenvolvedor e o que é um script injetado. Se o script está na página, o navegador o executa com as mesmas permissões do site (acesso a cookies, DOM, etc).

## 👺 Os 3 Pilares do XSS

### 1. 📬 Refletido (Reflected)
O script "bate e volta". Ele é enviado em uma requisição (como um parâmetro de busca na URL) e o servidor o exibe imediatamente na resposta.
- **Identificação**: Procure por qualquer dado que você envia via URL ou formulário e que aparece escrito na página.
- **Ponto Crítico**: Se você pode enviar HTML, você pode enviar `<script>`.

### 2. 💾 Armazenado (Stored)
O script é salvo no "coração" da aplicação (banco de dados). Toda vez que alguém visitar a página afetada, o script será executado.
- **Identificação**: Campos de perfil, comentários, mensagens de fórum ou qualquer dado persistente.
- **Impacto**: É o mais perigoso, pois não exige que a vítima clique em um link específico; basta visitar a página legítima.

### 3. 🌳 Baseado em DOM (DOM-based)
A falha não está no servidor, mas no JavaScript da própria página que manipula dados da URL de forma insegura e os injeta no DOM.
- **Fontes (Sources)**: `location.hash`, `location.search`.
- **Sumidouros (Sinks)**: Funções que interpretam strings como HTML/Código, como `.innerHTML` ou `eval()`.

## 🛠️ Como Pensar em Payloads?
Não decore payloads. Entenda o contexto:
- **Contexto HTML**: Você está entre tags? Precisa abrir uma nova tag (ex: `<script>`).
- **Contexto de Atributo**: Você está dentro de um `value="..."`? Precisa fechar as aspas e a tag, ou usar eventos (ex: `onmouseover`).
- **Contexto JavaScript**: Você está dentro de uma variável JS? Precisa fechar as aspas e o comando original.

## 🛡️ Mentalidade de Defesa
1. **Codificação de Saída (Output Encoding)**: Trate todo dado do usuário como texto, transformando `<` em `&lt;`.
2. **CSP (Content Security Policy)**: Uma lista branca que diz ao navegador: "Só execute scripts destes domínios confiáveis".
3. **HttpOnly**: Proteja seus cookies. Se o JS não consegue ler o cookie, o XSS não consegue roubar a sessão.

---
**Tags:** `XSS`, `JavaScript-Security`, `Client-Side`, `Security-Mindset`, `CSP`