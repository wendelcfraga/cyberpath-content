# Protocolos de VPN e Segurança

Uma VPN (Virtual Private Network) cria uma conexão segura e criptografada sobre uma rede menos segura, como a Internet.

## Como Funciona?
A VPN utiliza protocolos de tunelamento para encapsular pacotes de dados dentro de outros pacotes e os envia através de um túnel virtual.

## Principais Protocolos

### 1. OpenVPN
Protocolo open-source que utiliza a biblioteca OpenSSL para criptografia. É altamente configurável e seguro.

### 2. IPsec (Internet Protocol Security)
Frequentemente usado para VPNs site-to-site. Oferece autenticação, integridade e confidencialidade na camada de rede.

### 3. WireGuard
Um protocolo moderno que visa ser mais rápido, simples e enxuto que o IPsec e o OpenVPN, utilizando criptografia de ponta.

### 4. L2TP/IPsec
O Layer 2 Tunneling Protocol não fornece criptografia por si só, por isso é quase sempre combinado com o IPsec.

## Benefícios de Segurança
- **Confidencialidade**: Protege contra sniffing em redes Wi-Fi públicas.
- **Anonimato**: Oculta o endereço IP real do usuário.
- **Integridade**: Garante que os dados não foram alterados em trânsito.

## Riscos e Considerações
- **Vulnerabilidades de Software**: Falhas no cliente ou servidor VPN.
- **Logging**: O provedor de VPN pode registrar seu tráfego.
- **Split Tunneling**: Se mal configurado, parte do tráfego pode sair fora do túnel seguro.