# Introdução à Segurança Linux

O Linux é o sistema operacional que move a maioria dos servidores de internet e dispositivos embarcados do mundo. Entender sua segurança é fundamental para qualquer profissional da área.

## Usuários e Grupos
- **Root**: O superusuário com controle total sobre o sistema (UID 0).
- **Usuários Comuns**: Possuem permissões limitadas para proteger o sistema.
- **Grupos**: Forma de agrupar usuários para atribuir permissões coletivas.

## Permissões de Arquivos (Aprofundado)
Cada arquivo e diretório possui três conjuntos de permissões (Dono, Grupo, Outros).
- **Representação Simbólica**: `rwxr-xr-x`
- **Representação Octal**: 
  - 4 (Leitura) + 2 (Escrita) + 1 (Execução) = 7
  - Exemplo: `chmod 755` significa que o dono faz tudo, o grupo e outros apenas leem e executam.

### 🚩 Permissões Especiais (O perigo mora aqui)
1. **SUID (Set User ID)**: O binário roda com privilégios do DONO (geralmente root). Representado por um `s` no lugar do `x` do dono.
2. **SGID (Set Group ID)**: O binário roda com privilégios do GRUPO.
3. **Sticky Bit**: Apenas o dono do arquivo pode deletá-lo em um diretório compartilhado (ex: `/tmp`). Representado por um `t` no final.

## 📁 Estrutura de Diretórios: Onde o Hacker Procura
- `/etc/passwd`: Lista de usuários. Antigamente continha senhas.
- `/etc/shadow`: Onde os hashes das senhas realmente moram (protegido, só root lê).
- `/etc/sudoers`: Define quem pode usar o comando `sudo`.
- `/root/`: Home do administrador. O objetivo final de quase todo ataque.
- `/tmp/`: Diretório temporário. Ótimo para baixar scripts de ataque e ferramentas.

## 🛡️ Fortalecendo o Linux (Hardening)
1. **SSH Seguro**: Desabilite o login de root (`PermitRootLogin no`) e use chaves SSH em vez de senhas.
2. **Firewall (UFW/IPTables)**: Feche todas as portas que não estão sendo usadas.
3. **Atualizações**: Use `apt update && apt upgrade` regularmente para fechar brechas conhecidas (CVEs).
4. **Fail2Ban**: Bloqueia automaticamente IPs que tentam fazer brute-force no SSH.

---
**Tags:** `Linux`, `Permissions`, `SUID`, `Hardening`, `SSH`, `SysAdmin`
