# 🌐 Fundamentos de Redes: A Autoestrada da Informação

Entender redes é entender como os dados viajam de um ponto A para um ponto B. Sem isso, você está apenas "atirando no escuro".

## 🏗️ O Modelo OSI: As 7 Camadas do Poder
Imagine enviar uma carta: você escreve, põe no envelope, leva ao correio, o caminhão transporta, etc.
1. **Física**: Os cabos e sinais. O "asfalto" da estrada.
2. **Enlace**: Endereço MAC. Identifica seu computador na rede local.
3. **Rede**: O GPS. Usa o **IP** para encontrar o caminho entre redes.
4. **Transporte**: O controle de qualidade. **TCP** (garante a entrega) vs **UDP** (entrega rápida, mas pode perder algo).
5. **Sessão**: Inicia e termina a conversa.
6. **Apresentação**: Tradutor. Garante que os dados estejam em um formato que você entenda (ex: JPEG, Criptografia).
7. **Aplicação**: O que você vê. HTTP (Browser), SSH (Terminal).

## 🌍 Protocolos que Governam o Mundo
- **DNS**: O catálogo telefônico da Internet. Converte `google.com` em `142.250.191.46`.
- **DHCP**: O recepcionista que te dá um crachá (Endereço IP) assim que você entra na rede.
- **ARP**: O fofoqueiro. Pergunta: "Quem tem o IP tal? Me dê seu MAC!". Essencial para ataques de *Man-in-the-Middle*.

## 🛠️ Ferramentas de Exploração
- **Ping**: "Você está aí?"
- **Traceroute**: "Qual caminho você fez para chegar até aqui?"
- **Wireshark**: O microscópio que permite ver cada pacote de dados passando pela rede.

---
**Tags:** `OSI-Model`, `TCP-UDP`, `IP-Address`, `DNS`, `DHCP`, `Networking`