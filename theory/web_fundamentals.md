# 🌐 Fundamentos de Web: O Coração da Internet

Para ser um hacker ético de sucesso, você precisa entender como a Web funciona sob o capô. Não é apenas abrir um navegador; é uma dança complexa de protocolos, linguagens e transferências de dados.

## 🏗️ O Modelo Cliente-Servidor
A Web opera em um modelo de requisição e resposta:
- **Cliente (Browser)**: O seu navegador (Chrome, Firefox, Burp Suite) que inicia a conversa.
- **Servidor**: Um computador remoto (Apache, Nginx, Node.js) que "serve" o conteúdo.
- **DNS (Domain Name System)**: O "catálogo telefônico" que transforma `google.com` no endereço IP `142.250.190.46`.

## ✉️ Protocolo HTTP/HTTPS
O HTTP (HyperText Transfer Protocol) é a base de toda troca de dados na Web.

### 🛠️ Estrutura de uma Requisição (Request)
1. **Linha de Comando**: Método, Caminho e Versão (ex: `GET /index.html HTTP/1.1`).
2. **Headers**: Metadados (ex: `User-Agent`, `Host`, `Cookie`).
3. **Body**: Dados enviados ao servidor (comum em POST).

### 🛠️ Métodos que você DEVE dominar:
- **GET**: Solicita um recurso. Os parâmetros são visíveis na URL.
- **POST**: Envia dados para processamento. Usado em formulários e uploads.
- **PUT**: Substitui ou cria um recurso específico.
- **DELETE**: Remove o recurso especificado.
- **OPTIONS**: Pergunta ao servidor quais métodos são suportados. Útil para descobrir vetores de ataque.

### 🔢 Códigos de Status (HTTP Status Codes)
- **2xx (Sucesso)**: `200 OK` (Tudo certo).
- **3xx (Redirecionamento)**: `301 Moved Permanently`, `302 Found`.
- **4xx (Erro do Cliente)**: `403 Forbidden` (Sem permissão), `404 Not Found`.
- **5xx (Erro do Servidor)**: `500 Internal Server Error`, `503 Service Unavailable`.

## 🎨 HTML, CSS e JavaScript
- **HTML**: A estrutura (esqueleto) da página.
- **CSS**: O estilo (aparência).
- **JavaScript**: A lógica e interatividade. É aqui que moram ataques como **XSS**.

## 🍪 Gerenciamento de Estado: Cookies e Sessões
O HTTP é "stateless" (não guarda memória). Para o servidor saber que você ainda está logado:
- **Cookies**: Dados armazenados no seu navegador pelo servidor.
- **Sessions**: O servidor guarda seus dados e te dá um `Session ID` via cookie para te identificar.
- **⚠️ Risco**: Se um atacante roubar seu `Session ID`, ele pode "sequestrar" sua conta sem saber sua senha (Session Hijacking).

## 🛡️ Mesmas Origens (SOP) e CORS
- **SOP (Same-Origin Policy)**: Uma regra de segurança que impede que um site leia dados de outro site.
- **CORS (Cross-Origin Resource Sharing)**: Um mecanismo que permite "relaxar" a SOP para permitir integrações legítimas entre domínios diferentes.

---
**Tags:** `HTTP`, `Client-Server`, `Status-Codes`, `DOM`, `Cookies`, `CORS`