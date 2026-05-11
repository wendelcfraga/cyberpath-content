# 🌐 Fundamentos de Web: O Coração da Internet

Para ser um hacker ético, você precisa entender como a Web funciona sob o capô. Não é apenas abrir um navegador; é uma dança complexa de protocolos e dados.

## 🏗️ O Modelo Cliente-Servidor
Imagine um restaurante:
- **Você (Cliente/Browser)**: Faz o pedido (Request).
- **Garçom (Protocolo HTTP)**: Leva o pedido até a cozinha.
- **Cozinha (Servidor)**: Prepara o prato (Processa os dados) e o envia de volta.

## ✉️ Protocolo HTTP (HyperText Transfer Protocol)
É a linguagem que o navegador e o servidor usam para conversar.

### 🛠️ Métodos que você DEVE conhecer:
- **GET**: "Me dê esse arquivo". Usado para carregar páginas. Os dados aparecem na URL (ex: `?id=123`).
- **POST**: "Aqui estão meus dados". Usado em logins e formulários. Mais seguro pois os dados vão no "corpo" da mensagem.
- **PUT/PATCH**: "Atualize isso". Usado para modificar dados existentes.
- **DELETE**: "Apague isso". Autoexplicativo, e perigoso se mal configurado!

## 🔐 HTTPS: O Escudo de Criptografia
O HTTPS é o HTTP com uma camada extra de segurança (TLS/SSL).
- **Sem HTTPS**: Qualquer um na mesma rede (Wi-Fi pública) pode ver sua senha em texto puro (Sniffing).
- **Com HTTPS**: Seus dados são transformados em um código ilegível antes de saírem do seu dispositivo.

## 🍪 Cookies e Sessões: A Memória da Web
O HTTP é "stateless" (não tem memória). Sem cookies, você teria que fazer login em cada página que clicasse!
- **Cookies**: Pequenos arquivos que o servidor guarda no seu navegador.
- **Session ID**: Um código único no seu cookie que diz ao servidor: "Ei, eu sou o usuário que logou há 5 minutos".

---
**Tags:** `HTTP`, `Client-Server`, `Methods`, `HTTPS`, `Cookies`, `Web-Basics`