# Ataques Man-in-the-Middle (MitM)

Um ataque Man-in-the-Middle ocorre quando um invasor se posiciona secretamente entre duas partes que acreditam estar se comunicando diretamente.

## Como Funciona
O invasor intercepta a comunicação, podendo ler, modificar ou inserir novas mensagens no fluxo de dados sem que nenhuma das partes perceba.

## Técnicas Comuns

### ARP Spoofing
O invasor envia mensagens ARP falsas para uma rede local para associar seu endereço MAC ao endereço IP de um gateway legítimo (ou outro host). Isso faz com que o tráfego destinado a esse IP seja enviado ao invasor.

### DNS Spoofing (Cache Poisoning)
O invasor introduz dados falsos no cache de um servidor DNS, fazendo com que as consultas retornem um endereço IP incorreto (geralmente controlado pelo invasor).

### SSL/TLS Stripping
O invasor força o navegador da vítima a usar uma conexão HTTP não criptografada em vez de uma conexão HTTPS segura, permitindo a interceptação de dados sensíveis.

## Como Prevenir
- **Uso de HTTPS**: Criptografia ponta a ponta.
- **VPN**: Cria um túnel criptografado para o tráfego.
- **Segurança de Porta (Port Security)** em switches.
- **Inspeção ARP Dinâmica (DAI)**.
- **HSTS (HTTP Strict Transport Security)**.