# 🔍 Scanning e Enumeração: Mapeando o Alvo

O scanning é a fase onde o atacante tenta identificar sistemas ativos, portas abertas e serviços rodando em uma rede. É o alicerce de qualquer teste de invasão bem-sucedido.

## 📡 Nmap (Network Mapper): A Espada do Pentester
O Nmap é a ferramenta padrão da indústria para descoberta de rede.

### 🛠️ Tipos de Scan Essenciais:
1. **TCP SYN Scan (`-sS`)**: Conhecido como "Stealth Scan". Ele não completa a conexão TCP (não envia o ACK final), tornando-o mais silencioso.
2. **TCP Connect Scan (`-sT`)**: Completa o handshake de 3 vias. Mais barulhento e fácil de detectar por firewalls.
3. **UDP Scan (`-sU`)**: Verifica portas UDP (como DNS, DHCP, SNMP). É muito mais lento que o scan TCP.
4. **Service Version Detection (`-sV`)**: Interroga as portas abertas para determinar qual software e versão estão rodando.
5. **OS Detection (`-O`)**: Analisa as respostas da pilha TCP/IP para adivinhar o Sistema Operacional.

### 📜 Scripts Nmap (NSE):
O `Nmap Scripting Engine` permite automatizar tarefas:
- `nmap --script vuln <alvo>`: Verifica vulnerabilidades conhecidas nos serviços encontrados.
- `nmap --script http-enum <alvo>`: Tenta enumerar diretórios e arquivos em servidores web.

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