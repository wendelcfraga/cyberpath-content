# Introdução à Segurança Linux

O Linux é o sistema operacional que move a maioria dos servidores de internet e dispositivos embarcados do mundo. Entender sua segurança é fundamental para qualquer profissional da área.

## Usuários e Grupos
- **Root**: O superusuário com controle total sobre o sistema (UID 0).
- **Usuários Comuns**: Possuem permissões limitadas para proteger o sistema.
- **Grupos**: Forma de agrupar usuários para atribuir permissões coletivas.

## Permissões de Arquivos
Cada arquivo e diretório possui três conjuntos de permissões:
1. **Dono** (User)
2. **Grupo** (Group)
3. **Outros** (Others)

As permissões são:
- **r** (Read - 4): Ler o conteúdo.
- **w** (Write - 2): Modificar o conteúdo.
- **x** (Execute - 1): Executar o arquivo ou entrar no diretório.

Exemplo: `chmod 755 arquivo` (rwxr-xr-x).

## Estrutura de Diretórios Importante
- `/etc/`: Arquivos de configuração do sistema.
- `/etc/passwd` e `/etc/shadow`: Armazenam informações de usuários e hashes de senhas.
- `/bin/` e `/usr/bin/`: Executáveis essenciais.
- `/var/log/`: Logs do sistema e de aplicativos.

## O que é SUID?
O bit **Set Owner User ID (SUID)** permite que um arquivo seja executado com as permissões do dono do arquivo, em vez das permissões do usuário que o está executando. Se um executável com root SUID for vulnerável, ele pode ser usado para escalação de privilégios.