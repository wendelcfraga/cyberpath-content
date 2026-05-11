# Escalação de Privilégios em Linux

Escalação de privilégios é o ato de explorar um bug, falha de design ou erro de configuração em um software para ganhar acesso elevado a recursos que normalmente seriam protegidos.

## Vetores Comuns de Escalação

### 1. Configurações Sudo Incorretas
Verificar o que o usuário atual pode executar como root sem senha: `sudo -l`.
Alguns binários legítimos (como `find`, `vim` ou `less`) podem ser usados para obter um shell root se permitidos no sudoers.

### 2. Binários SUID
Arquivos que rodam com permissões de root. Podemos procurá-los com:
`find / -perm -u=s -type f 2>/dev/null`

### 3. Exploits de Kernel
Versões desatualizadas do kernel Linux podem ter vulnerabilidades conhecidas (ex: Dirty COW) que permitem acesso root imediato.

### 4. Tarefas Agendadas (Cron Jobs)
Se uma tarefa do cron executa um script que o usuário comum pode editar, ele pode inserir comandos maliciosos para serem executados como root.

### 5. Arquivos de Configuração com Senhas
Procurar em `/var/www/`, arquivos de log ou arquivos ocultos no home por credenciais esquecidas.

## Ferramentas de Enumeração
- **LinPEAS**: Script automatizado extremamente completo para encontrar vetores de escalação.
- **Linux Exploit Suggester**: Sugere exploits de kernel baseados na versão do sistema.