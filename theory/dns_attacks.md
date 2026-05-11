# Ataques de DNS

O DNS (Domain Name System) é o "catálogo telefônico" da Internet, convertendo nomes de domínio em endereços IP. Devido à sua natureza fundamental e muitas vezes sem segurança, é alvo constante de ataques.

## Principais Vulnerabilidades

### 1. DNS Spoofing / Cache Poisoning
O atacante introduz dados falsos no cache de um resolvedor DNS. Quando um usuário tenta acessar um site legítimo, o resolvedor retorna o IP do atacante.

### 2. DNS Tunneling
Utiliza o protocolo DNS para encapsular outros protocolos (como SSH ou HTTP), permitindo a exfiltração de dados ou comando e controle (C2) através de firewalls que permitem tráfego DNS.

### 3. Ataques de Amplificação DNS (DDoS)
O atacante envia pequenas consultas DNS com o IP de origem forjado (da vítima) para servidores DNS abertos que retornam respostas muito maiores, inundando a vítima com tráfego.

## Como Mitigar
- **DNSSEC**: Adiciona assinaturas digitais aos registros DNS para garantir autenticidade e integridade.
- **Configuração de Servidores**: Desativar recursão em servidores DNS autoritativos públicos.
- **Monitoramento**: Analisar tráfego DNS em busca de padrões anômalos.