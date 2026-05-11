# 🔍 Scanning e Enumeração: Mapeando o Alvo

O scanning é a fase onde o atacante tenta identificar sistemas ativos, portas abertas e serviços rodando em uma rede. É o alicerce de qualquer teste de invasão bem-sucedido.

## 📡 Nmap (Network Mapper): A Espada do Pentester
O Nmap é a ferramenta padrão da indústria para descoberta de rede.

### 🛠️ Tipos de Scan Essenciais:
1. **TCP SYN Scan (`-sS`)**: O padrão do Nmap. Ele envia um pacote SYN e espera o SYN/ACK. Se receber, ele sabe que a porta está aberta, mas envia um RST em vez de completar a conexão. Isso evita o log de conexão completa em muitos sistemas.
2. **TCP Connect Scan (`-sT`)**: Usado quando o usuário não tem privilégios de root para enviar pacotes crus. Completa o handshake, sendo mais fácil de detectar.
3. **UDP Scan (`-sU`)**: Crucial para encontrar serviços como DNS (53), SNMP (161) e DHCP. Como UDP não tem handshake, o Nmap espera por uma resposta ou por um erro ICMP "Port Unreachable".
4. **Service Version Detection (`-sV`)**: Não confie apenas no número da porta. O `-sV` envia probes para determinar se na porta 80 está rodando um Apache 2.4.41 ou um Nginx.
5. **OS Detection (`-O`)**: Identifica o sistema operacional analisando nuances como o TTL (Time to Live) e o tamanho da janela TCP.

### 📜 Scripts Nmap (NSE) - O Poder da Automação:
O `Nmap Scripting Engine` transforma o Nmap em um scanner de vulnerabilidades:
- `nmap --script safe <alvo>`: Executa apenas scripts que não vão derrubar o serviço.
- `nmap --script auth <alvo>`: Tenta bypassar ou testar autenticações comuns.
- `nmap --script vuln <alvo>`: Procura por CVEs conhecidas nos serviços identificados.

## 📖 Enumeração: Mergulhando nos Detalhes
Enumeração é a arte de extrair nomes de usuários, grupos, compartilhamentos e configurações de serviços específicos.

- **SMB (445)**:
  - `enum4linux -a <IP>`: Uma ferramenta clássica para extrair tudo de sistemas Windows/Samba.
  - `nmap --script smb-os-discovery <IP>`: Descobre a versão exata do Windows.
- **HTTP/HTTPS (80/443)**:
  - **Fuzzing**: Usar ferramentas como `ffuf`, `gobuster` ou `dirsearch` para encontrar diretórios como `/admin`, `/.git` ou `/config.php`.
- **SNMP (161)**:
  - Se a community string (senha) for `public`, use `snmp-check` para ler informações do sistema, processos rodando e interfaces de rede.

## 📖 Enumeração: O Detalhe que Faz a Diferença
Diferente do scanning, a enumeração foca em extrair informações específicas de um serviço identificado.

- **SMB (Portas 139/445)**: Tentar listar compartilhamentos sem senha (`smbclient -L`) ou encontrar usuários (`enum4linux`).
- **SNMP (Porta 161)**: Se a "community string" for `public`, você pode extrair quase toda a configuração do dispositivo.
- **DNS (Porta 53)**: Tentar uma "Zone Transfer" (`axfr`) para listar todos os subdomínios de uma empresa.

## 🚩 Banner Grabbing
Ler a mensagem de boas-vindas de um serviço para identificar sua versão manualmente.
- **Comando**: `nc -nv <IP> <Porta>`
- **Exemplo**: Conectar na porta 80 e enviar `HEAD / HTTP/1.0` pode revelar se o servidor é Apache, Nginx ou IIS.

---
**Tags:** `Nmap`, `Scanning`, `Enumeração`, `Network-Security`, `Recon`, `OSINT`