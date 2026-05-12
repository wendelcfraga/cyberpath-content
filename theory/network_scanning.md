# 🔍 Scanning e Enumeração: Mapeando a Superfície de Ataque

O scanning é a fase de reconhecimento ativo. Aqui, o objetivo é descobrir quais portas estão abertas e quais serviços estão escutando, para então mapear possíveis vulnerabilidades.

## 📡 Nmap (Network Mapper): O canivete suíço
O Nmap funciona enviando pacotes customizados e analisando as respostas (ou a falta delas) para deduzir o estado de um sistema.

### 🛠️ Entendendo a Lógica dos Scans:
1. **Stealth Scan (SYN) `-sS`**: É o "aperto de mão incompleto". O Nmap envia um SYN, recebe um SYN/ACK (provando que a porta está aberta) e envia um RST para fechar a conexão antes que ela seja logada pela aplicação.
2. **Connect Scan `-sT`**: Completa o handshake TCP de 3 vias. É o que acontece quando você não tem permissões de administrador no seu sistema ou usa um proxy. É mais fácil de ser detectado por firewalls.
3. **UDP Scan `-sU`**: Diferente do TCP, o UDP não tem confirmação. O Nmap assume que a porta está aberta a menos que receba uma mensagem de erro ICMP "Inalcançável". Por isso, é um scan mais lento e menos preciso.
4. **Detecção de Versão `-sV`**: Após descobrir que uma porta está aberta, o Nmap tenta "conversar" com o serviço para que ele se identifique (Banner Grabbing), revelando nomes e versões exatas de softwares.

### 🚀 Flags de Agilidade e Agressividade:
- `-T4`: Aumenta a velocidade do scan (útil para redes rápidas).
- `-A`: O "modo agressivo". Ativa detecção de SO, versão, scan de scripts e traceroute em um único comando.
- `-p-`: Varre todas as 65.535 portas possíveis, em vez de apenas as 1000 mais comuns.

## 📖 Enumeração: Extraindo Dados Valiosos
Enquanto o scan diz "o que está lá", a enumeração diz "quem está lá e o que eles têm".

- **SMB (445)**: Tentar listar usuários, grupos e compartilhamentos de arquivos (shares) sem senha.
- **HTTP/HTTPS**: Usar ferramentas de força bruta (como `Gobuster` ou `Dirb`) para encontrar diretórios ocultos ou arquivos de configuração esquecidos.
- **Banner Grabbing**: Usar o `netcat` (`nc`) para se conectar a uma porta e ler a primeira mensagem que o servidor envia. Isso muitas vezes entrega a tecnologia usada sem nenhum esforço extra.

## 🛡️ A Perspectiva do Defensor
Scanners de rede geram muito "ruído". Sistemas de Detecção de Intrusão (IDS) modernos conseguem identificar padrões de varredura (como o SYN scan) e bloquear o IP de origem automaticamente.

---
**Tags:** `Nmap`, `Scanning`, `Enumeração`, `Recon`, `Network-Security`, `Discovery`