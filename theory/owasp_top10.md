# 🏆 OWASP Top 10: O Mapa da Mina da Segurança Web

O OWASP Top 10 não é apenas uma lista, é o padrão global para segurança de aplicações. Se você quer ser um Pentester ou um Desenvolvedor seguro, este é o seu guia definitivo.

## 🧐 O que é?
É uma lista atualizada periodicamente que descreve os 10 riscos de segurança mais críticos para aplicações web, baseada em dados de milhares de empresas e especialistas em segurança.

## 🚩 O Top 10 Atual (Aprofundado)

## 🚩 O Top 10 Atual (Aprofundado e Prático)

### 1. 🔓 A01:2021-Broken Access Control
O usuário consegue acessar dados ou funções fora de sua permissão.
- **Cenário**: O usuário 'João' acessa `site.com/api/user/123`. Ele muda para `id=124` e vê os dados da 'Maria'. Isso é chamado de **IDOR** (Insecure Direct Object Reference).
- **Ataque Avançado**: Tentar acessar rotas administrativas como `/admin/export_users` mesmo estando logado como usuário comum.
- **Mitigação**: Use identificadores não previsíveis (UUIDs) e verifique a propriedade do recurso em cada acesso ao banco de dados.

### 2. 🔐 A02:2021-Cryptographic Failures
Falha na proteção de dados sensíveis em trânsito ou em repouso.
- **Problema**: Armazenar senhas em Plaintext ou usar Base64 (que não é criptografia, é apenas codificação).
- **Curiosidade**: O termo mudou de "Sensitive Data Exposure" para "Cryptographic Failures" para focar na causa raiz (falha na cripto) e não no sintoma (exposição).
- **Mitigação**: Use Hashing adaptativo (Argon2, BCrypt) e nunca invente seu próprio algoritmo de criptografia.

### 3. 💉 A03:2021-Injection
Dados não confiáveis são inseridos em comandos, forçando a execução de instruções não planejadas.
- **Tipos**: Além de SQL, temos **Log Injection** (escrever entradas falsas em logs para enganar administradores) e **Email Injection**.
- **Regra de Ouro**: Nunca confie em NADA que venha do usuário (Headers, Cookies, URL, Form).
- **Mitigação**: Use ORMs modernos que fazem parametrização automática, mas cuidado com funções de "Raw Query".

### 4. 🏗️ A04:2021-Insecure Design
A vulnerabilidade nasce na prancheta, antes de uma linha de código ser escrita.
- **Exemplo**: Um sistema de recuperação de senha que faz perguntas óbvias como "Qual seu animal de estimação?", cujas respostas estão no Facebook do usuário.
- **Diferença**: Enquanto "Insecure Implementation" é um erro ao codificar, "Insecure Design" é uma falha na lógica de negócio.

### 5. ⚙️ A05:2021-Security Misconfiguration
Portas abertas por esquecimento ou falta de conhecimento.
- **Exemplo Real**: Buckets S3 da Amazon configurados como "Public" contendo backups de banco de dados.
- **Checklist**: Remova páginas de exemplo, desabilite o diretório `/server-status` e mude as senhas padrão de serviços como Redis ou MongoDB.

### 6. 📦 A06:2021-Vulnerable and Outdated Components
O seu código é seguro, mas o do vizinho (biblioteca) não é.
- **Caso Famoso**: O ataque à Equifax ocorreu devido a uma vulnerabilidade conhecida no Apache Struts que não foi corrigida a tempo.
- **Ação**: Implemente um pipeline de CI/CD que bloqueie o build se houver dependências com CVEs de nível Crítico ou Alto.

### 7. 🆔 A07:2021-Identification and Authentication Failures
- **Sessões Inseguras**: O ID de sessão não muda após o login (Session Fixation).
- **Ataque**: Preenchimento de Credenciais (usar senhas vazadas em outros sites para tentar entrar no seu).
- **Mitigação**: Invalide sessões após logout, implemente MFA e use bibliotecas de gerenciamento de identidade testadas (como Keycloak ou Auth0).

### 8. 🛡️ A08:2021-Software and Data Integrity Failures
Confiança cega em atualizações ou dados serializados.
- **Ataque**: Injetar um objeto malicioso em um campo que o Java ou PHP vai "deserializar", levando à execução de comandos (RCE).
- **Ação**: Verifique a integridade de arquivos usando hashes (SHA-256) e evite formatos de serialização nativos perigosos.

### 9. 📈 A09:2021-Security Logging and Monitoring Failures
- **O Problema**: O tempo médio para detectar uma invasão é de mais de 200 dias. Sem logs, você é um "cego em um tiroteio".
- **O que logar**: Tentativas de login, acessos a dados sensíveis, mudanças de privilégio e erros de validação de input.

### 10. 🔌 A10:2021-Server-Side Request Forgery (SSRF)
O servidor vira o seu "proxy" para atacar a rede interna dele.
- **Exemplo**: Pedir para o servidor baixar uma imagem de `http://169.254.169.254/latest/meta-data/` (IP de metadados da AWS) para roubar chaves de acesso.
- **Defesa**: Negue por padrão acessos a IPs internos (127.0.0.1, 10.x.x.x, 192.168.x.x).

## 💡 Conclusão
Dominar o OWASP Top 10 é o primeiro passo para qualquer profissional de segurança. Ele serve como o checklist base para auditorias e testes de invasão em todo o mundo.

---
**Tags:** `OWASP`, `Web-Security`, `Checklist`, `AppSec`, `Pentest-Basic`, `Risk-Analysis`