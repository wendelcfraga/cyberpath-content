# Burp Suite: Interceptação e Proxy

O Burp Suite é a ferramenta líder de mercado para testes de segurança em aplicações web. Sua função principal é atuar como um proxy de interceptação.

## O que é um Proxy de Interceptação?
Ele se posiciona entre o seu navegador e o servidor web. Isso permite que você capture, analise e até modifique as requisições HTTP antes que elas cheguem ao servidor, e as respostas antes que cheguem ao navegador.

## Componentes Principais do Burp

### 1. Proxy
O coração do Burp. Permite interceptar o tráfego. No "Intercept Tab", você pode pausar uma requisição, alterar campos (como cookies ou parâmetros POST) e então enviá-la.

### 2. Repeater
Permite reenviar uma única requisição HTTP repetidamente, facilitando o teste manual de vulnerabilidades ao ajustar parâmetros e observar as mudanças na resposta.

### 3. Intruder
Ferramenta para ataques automatizados e customizados, como força bruta em formulários de login ou fuzzing de parâmetros para encontrar injeções.

### 4. Decoder
Uma ferramenta simples para converter dados entre diversos formatos de codificação (URL, HTML, Base64, Hex, etc.).

## Configuração Básica
Para usar o Burp, você deve configurar seu navegador para usar o proxy (geralmente `127.0.0.1:8080`) e instalar o certificado CA do Burp para poder interceptar tráfego HTTPS.