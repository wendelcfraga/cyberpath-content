# Hardening de Sistemas Operacionais

Hardening é o processo de proteger um sistema reduzindo sua superfície de ataque, ou seja, eliminando o maior número possível de vetores de segurança.

## Princípios de Hardening

### 1. Minimizar Software Instalado
Remova todos os pacotes, serviços e utilitários desnecessários. Menos código significa menos vulnerabilidades potenciais.

### 2. Gerenciamento de Patches
Mantenha o sistema operacional e todos os aplicativos instalados atualizados com as últimas correções de segurança.

### 3. Configuração de Usuários e Senhas
- Desativar logins de root via SSH.
- Implementar políticas de senhas fortes.
- Remover usuários inativos.
- Usar autenticação via chaves SSH em vez de senhas.

### 4. Firewall e Rede
- Fechar todas as portas que não são estritamente necessárias.
- Configurar o `iptables` (Linux) ou Windows Firewall para permitir apenas tráfego conhecido.

### 5. Logging e Auditoria
Configurar o sistema para registrar eventos importantes de segurança. No Linux, use o `auditd`. No Windows, configure as Políticas de Auditoria.

### 6. Proteção de Memória e Kernel
No Linux, habilitar proteções como ASLR (Address Space Layout Randomization) e usar módulos de segurança como SELinux ou AppArmor.

## Checklists
Utilize guias de referência como o **CIS Benchmarks** (Center for Internet Security) para obter diretrizes detalhadas de hardening para cada sistema operacional específico.