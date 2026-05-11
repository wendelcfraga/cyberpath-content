# 🌐 Fundamentos de Web: O Coração da Internet

Para ser um hacker ético de sucesso, você precisa entender como a Web funciona sob o capô. Não é apenas abrir um navegador; é uma dança complexa de protocolos, linguagens e transferências de dados.

## 🏗️ O Modelo Cliente-Servidor
A Web opera em um modelo de requisição e resposta:
- **Cliente (Browser)**: O seu navegador (Chrome, Firefox, Burp Suite) que inicia a conversa.
- **Servidor**: Um computador remoto (Apache, Nginx, Node.js) que "serve" o conteúdo.
- **DNS (Domain Name System)**: O "catálogo telefônico" que transforma `google.com` no endereço IP `142.250.190.46`.

## ✉️ Protocolo HTTP/HTTPS: O Idioma da Web
O HTTP (HyperText Transfer Protocol) é a base de toda troca de dados na Web. O HTTPS adiciona uma camada de criptografia (TLS/SSL) para proteger os dados em trânsito contra ataques de **Man-in-the-Middle (MitM)**.

### 🛠️ Estrutura de uma Requisição (Request)
1. **Linha de Comando**: Método, Caminho e Versão (ex: `GET /index.html HTTP/1.1`).
2. **Headers**: Metadados cruciais para segurança.
   - `User-Agent`: Identifica o navegador (pode ser usado para filtrar bots).
   - `Host`: Indica qual domínio está sendo acessado (vital em servidores com múltiplos sites).
   - `Authorization`: Onde tokens JWT ou credenciais Basic são enviados.
   - `Referer`: De onde o usuário veio (pode ser usado para bypassar CSRF se mal configurado).
3. **Body**: Dados enviados ao servidor (comum em POST/PUT).

### 🛠️ Métodos que você DEVE dominar:
- **GET**: Solicita um recurso. **Regra de Ouro**: Nunca use GET para enviar senhas, pois elas ficam salvas nos logs do servidor e no histórico do navegador.
- **POST**: Envia dados. Mais seguro para formulários, mas não imune a interceptação.
- **PUT vs PATCH**: PUT substitui o recurso inteiro; PATCH faz uma alteração parcial.
- **OPTIONS**: Usado no pré-vôo (pre-flight) do CORS para saber se o navegador tem permissão para fazer uma requisição.

### 🔢 Códigos de Status (HTTP Status Codes) - Visão de Hacker
- **200 OK**: Alvo atingido com sucesso.
- **204 No Content**: Sucesso, mas sem corpo (comum em APIs).
- **302/301**: Redirecionamento. Atacantes usam isso para **Open Redirects** (levar o usuário para sites maliciosos).
- **401 Unauthorized**: Falta login.
- **403 Forbidden**: O servidor entendeu, mas se recusa a obedecer. Alvo de tentativas de **Bypass de WAF**.
- **404 Not Found**: Ótimo para **Fuzzing** de diretórios e arquivos escondidos.
- **500 Internal Error**: Frequentemente revela falhas de código ou **Stack Traces** que expõem a estrutura do backend.

## 🎨 HTML, CSS e JavaScript
- **HTML**: A estrutura (esqueleto) da página.
- **CSS**: O estilo (aparência).
- **JavaScript**: A lógica e interatividade. É aqui que moram ataques como **XSS**.

## 🍪 Gerenciamento de Estado: Cookies e Sessões
O HTTP é "stateless" (não guarda memória). Para o servidor saber que você ainda está logado:
- **Cookies**: Dados armazenados no seu navegador pelo servidor.
- **Sessions**: O servidor guarda seus dados e te dá um `Session ID` via cookie para te identificar.
- **⚠️ Risco**: Se um atacante roubar seu `Session ID`, ele pode "sequestrar" sua conta sem saber sua senha (Session Hijacking).

## 🛡️ Segurança e Origens: SOP e CORS
- **SOP (Same-Origin Policy)**: O navegador impede que o domínio `malicioso.com` leia dados de `banco.com`. É a defesa nº 1 da Web.
- **CORS (Cross-Origin Resource Sharing)**: Se o `banco.com` responder com o header `Access-Control-Allow-Origin: *`, ele quebra a própria segurança. Atacantes buscam configurações de CORS mal feitas para roubar dados sensíveis via scripts.

## 🔨 Ferramentas Essenciais do Dia a Dia
1. **Burp Suite**: O "Canivete Suíço". Permite interceptar e modificar cada byte que sai do seu computador.
2. **DevTools (F12)**: Para analisar o DOM, Console (JS) e Network em tempo real.
3. **Wappalyzer**: Extensão que revela quais tecnologias (CMS, Server, Framework) o site usa.

---
**Tags:** `HTTP`, `Client-Server`, `Status-Codes`, `DOM`, `Cookies`, `CORS`