# Metasploit Framework

O Metasploit Framework (MSF) é a plataforma de teste de penetração mais utilizada no mundo. É uma ferramenta open-source que ajuda as equipes de segurança a verificar vulnerabilidades e gerenciar avaliações de segurança.

## Arquitetura do Metasploit

### 1. Msfconsole
A interface de linha de comando mais popular e poderosa do MSF.

### 2. Módulos
- **Exploits**: Código que tira proveito de uma vulnerabilidade.
- **Payloads**: Código que é executado no sistema alvo após a exploração bem-sucedida (ex: Meterpreter).
- **Auxiliary**: Ferramentas para scanning, sniffing e fuzing.
- **Post**: Módulos para atividades pós-exploração.
- **Encoders**: Usados para ofuscar payloads e evitar detecção por antivírus.

## Meterpreter
O Meterpreter é um payload avançado e extensível que utiliza injeção de DLL na memória. Ele reside inteiramente na memória do alvo e não deixa rastros no disco, tornando-o difícil de detectar.

## Fluxo Básico de Trabalho
1. **Search**: Procurar por um exploit adequado.
2. **Use**: Selecionar o módulo.
3. **Show Options**: Verificar os parâmetros necessários.
4. **Set**: Configurar RHOSTS, LHOST, etc.
5. **Exploit/Run**: Executar o ataque.