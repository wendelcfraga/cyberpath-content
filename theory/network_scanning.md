# Scanning e Enumeração

O scanning é a fase onde o atacante tenta identificar sistemas ativos, portas abertas e serviços rodando em uma rede.

## Nmap (Network Mapper)
A ferramenta mais popular para scanning.

### Comandos Comuns:
- `nmap -sP 192.168.1.0/24`: Ping sweep para encontrar hosts ativos.
- `nmap -sS <alvo>`: Stealth Scan (SYN scan), o mais comum.
- `nmap -sV <alvo>`: Detecta versões dos serviços.
- `nmap -O <alvo>`: Tenta identificar o Sistema Operacional.
- `nmap -A <alvo>`: Scan agressivo (SO, versão, scripts e traceroute).

## Enumeração
Processo de extrair informações detalhadas de um serviço, como nomes de usuários, compartilhamentos de rede, versões de software, etc.
- **HTTP**: Enumeração de diretórios (Gobuster, Dirb).
- **SMB**: Listagem de compartilhamentos (Enum4linux).
- **DNS**: Transferência de zona.

## Banner Grabbing
Técnica para ler a mensagem de boas-vindas (banner) de um serviço para identificar sua versão. Pode ser feito via `nc` ou `telnet`.