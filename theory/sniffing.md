# Sniffing em Redes Locais

Sniffing é o processo de monitorar e capturar todos os pacotes de dados que passam por uma rede usando uma ferramenta de sniffing.

## Como funciona?
Em uma rede Ethernet tradicional, todos os hosts na mesma rede local (LAN) podem tecnicamente "ouvir" o tráfego uns dos outros se a placa de rede estiver em **Modo Promíscuo**. No entanto, switches modernos limitam o tráfego apenas às portas de destino.

## Técnicas para Sniffing em Switches
1. **ARP Spoofing**: Engana o switch para enviar tráfego de outros hosts para o atacante.
2. **MAC Flooding**: Inunda a tabela CAM do switch, forçando-o a agir como um hub (enviando tráfego para todas as portas).
3. **Port Mirroring (SPAN)**: Recurso legítimo de switches gerenciáveis usado para monitoramento.

## Protocolos Vulneráveis (Texto Simples)
- **HTTP**: Senhas e cookies.
- **FTP**: Credenciais de transferência de arquivos.
- **Telnet**: Sessões de terminal inteiras.
- **SMTP/POP3**: Conteúdo de e-mails.

## Prevenção
- **Criptografia**: Usar protocolos seguros (HTTPS, SSH, SFTP, SMTPS).
- **Segmentação de Rede (VLANs)**: Limita o domínio de broadcast.
- **Segurança de Porta**: Limita o número de endereços MAC por porta.
- **VPN**: Criptografa todo o tráfego da camada de rede para cima.