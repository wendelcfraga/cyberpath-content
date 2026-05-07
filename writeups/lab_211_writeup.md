# Write-up: Scanning com Nmap (Mapeamento de Rede)

**Autor:** @cyberpath_staff  
**Dificuldade:** Fácil  
**Data:** 07/05/2026

## 🎯 Objetivo
Identificar portas abertas, serviços e versões em um servidor alvo (`192.168.1.10`) utilizando o Nmap, além de entender a interpretação dos estados de porta.

## 🔍 Reconhecimento
O Nmap é a ferramenta fundamental para a fase de *Footprinting*. Iniciamos tentando entender o que está exposto no host alvo.

## 🚀 Exploração
O laboratório focou em três pontos principais de uso do Nmap:

1.  **Varredura Agressiva:**
    Utilizamos o comando:
    ```bash
    nmap -A 192.168.1.10
    ```
    A flag `-A` ativa detecção de Sistema Operacional, detecção de versão, escaneamento de scripts e traceroute. É ideal para obter o máximo de informação rapidamente.

2.  **Identificação de Firewall (Estados de Porta):**
    Quando o Nmap retorna uma porta como `Filtered`, significa que ele não recebeu nenhuma resposta. Isso geralmente indica que um Firewall ou IDS/IPS descartou o pacote silenciosamente.

3.  **Detecção de Versão Específica:**
    Para descobrir qual software está rodando em uma porta específica (ex: 8080), usamos:
    ```bash
    nmap -sV -p 8080 192.168.1.10
    ```
    O `-sV` envia sondas específicas para os protocolos para extrair o banner e a versão exata do serviço.

## 🏁 Conclusão e Flag
O mapeamento correto de uma rede é metade do caminho para um ataque bem-sucedido ou uma defesa eficiente. Saber ler os estados das portas (Open, Closed, Filtered) permite identificar onde estão os controles de segurança.

**Dica:** Sempre use `-oN` ou `-oX` para salvar seus resultados do Nmap para análise posterior!
