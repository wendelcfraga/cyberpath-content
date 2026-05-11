# Análise de Tráfego e Wireshark

A análise de tráfego é o processo de interceptar e examinar mensagens de dados em trânsito em uma rede.

## Wireshark
O Wireshark é o analisador de protocolo de rede mais importante do mundo. Ele permite que você veja o que está acontecendo em sua rede em um nível microscópico.

### Funcionalidades:
- **Captura em tempo real**: Intercepta pacotes de uma interface de rede ativa.
- **Filtragem poderosa**: Permite isolar tráfego específico (ex: `http`, `ip.addr == 192.168.1.1`, `tcp.port == 80`).
- **Inspeção profunda**: Decodifica centenas de protocolos.
- **Seguir Fluxos**: reconstrói uma conversa completa de TCP ou HTTP.

## O que procurar?
- Senhas enviadas em texto simples (HTTP, FTP, Telnet).
- Anomalias de tráfego que podem indicar uma invasão.
- Exfiltração de dados.
- Varreduras de rede.