# Fundamentos de Segurança Windows

A segurança no ecossistence Windows gira em torno do gerenciamento de identidades, autenticação e controle de acesso em larga escala.

## Active Directory (AD)
O AD é o serviço de diretório da Microsoft que gerencia usuários, computadores e outros recursos em uma rede Windows.
- **Domínio**: Um agrupamento lógico de objetos de rede.
- **Controlador de Domínio (DC)**: O servidor que responde às solicitações de autenticação de segurança dentro de um domínio Windows.

## Autenticação
- **Kerberos**: O protocolo de autenticação padrão no AD. Utiliza "tickets" para provar a identidade.
- **NTLM**: Protocolo mais antigo e menos seguro, ainda comum em ambientes legados.

## PowerShell e Segurança
O PowerShell é uma ferramenta poderosa de automação e configuração. Do ponto de vista de segurança:
- **Execution Policy**: Define o nível de permissão para execução de scripts (pode ser contornado).
- **Logging**: O PowerShell moderno (v5+) possui excelentes capacidades de log (Script Block Logging) para detectar ataques.

## UAC (User Account Control)
O Controle de Conta de Usuário ajuda a evitar que softwares maliciosos façam alterações não autorizadas no sistema, solicitando permissão sempre que uma tarefa exige privilégios administrativos.

## Defesas Modernas
- **Windows Defender Antivirus**.
- **BitLocker**: Criptografia de disco.
- **AppLocker**: Controle de quais aplicativos podem ser executados.