# 🏆 OWASP Top 10: O Mapa da Mina da Segurança Web

O OWASP Top 10 não é apenas uma lista, é o padrão global para segurança de aplicações. Se você quer ser um Pentester ou um Desenvolvedor seguro, este é o seu guia definitivo.

## 🧐 O que é?
É uma lista atualizada periodicamente que descreve os 10 riscos de segurança mais críticos para aplicações web, baseada em dados de milhares de empresas e especialistas em segurança.

## 🚩 O Top 10 Atual (Aprofundado)

### 1. 🔓 A01:2021-Broken Access Control
O usuário consegue acessar dados ou funções fora de sua permissão.
- **Cenário**: O usuário 'João' acessa `site.com/api/user/123`. Ele muda para `id=124` e vê os dados da 'Maria'.
- **Mitigação**: Implementar verificações de permissão em todas as requisições no lado do servidor, não apenas esconder botões no frontend.

### 2. 🔐 A02:2021-Cryptographic Failures
Falha na proteção de dados sensíveis (senhas, cartões, PII).
- **Problema**: Usar HTTP em vez de HTTPS, ou algoritmos fracos como MD5/SHA1.
- **Mitigação**: Usar TLS 1.2+, Argon2 ou BCrypt para senhas e criptografar dados em repouso.

### 3. 💉 A03:2021-Injection
Dados não confiáveis são enviados para um intérprete como parte de um comando ou consulta.
- **Tipos**: SQL Injection, Command Injection, LDAP Injection.
- **Mitigação**: Usar consultas parametrizadas (Prepared Statements) e validar rigorosamente o input.

### 4. 🏗️ A04:2021-Insecure Design
A falha está na arquitetura do sistema.
- **Exemplo**: Um site de e-commerce que não limita a quantidade de cupons de desconto que podem ser usados em uma única compra.
- **Mitigação**: Ciclo de vida de desenvolvimento seguro (S-SDLC) e modelagem de ameaças.

### 5. ⚙️ A05:2021-Security Misconfiguration
Configurações de segurança mal feitas ou padrão.
- **Cenário**: Deixar o console de administração com `admin/admin` ou mostrar stack traces detalhados em erros 500.
- **Mitigação**: Desabilitar recursos desnecessários e automatizar a verificação de configurações.

### 6. 📦 A06:2021-Vulnerable and Outdated Components
Usar bibliotecas (npm, nuget, maven) com vulnerabilidades conhecidas.
- **Risco**: Se sua aplicação usa uma versão antiga do Log4j, ela pode estar vulnerável a RCE.
- **Mitigação**: Usar ferramentas como `npm audit`, `Snyk` ou `OWASP Dependency-Check`.

### 7. 🆔 A07:2021-Identification and Authentication Failures
Falhas que permitem que atacantes comprometam senhas ou tokens de sessão.
- **Cenário**: Permitir ataques de força bruta ou preenchimento de credenciais (Credential Stuffing).
- **Mitigação**: Implementar MFA (Multi-Factor Authentication) e políticas de senha forte.

### 8. 🛡️ A08:2021-Software and Data Integrity Failures
Código e infraestrutura que não protegem contra violações de integridade.
- **Exemplo**: Atualizações de software baixadas de fontes não assinadas ou deserialização insegura de objetos.
- **Mitigação**: Usar assinaturas digitais e verificar a procedência de todas as bibliotecas.

### 9. 📈 A09:2021-Security Logging and Monitoring Failures
Não registrar ou monitorar eventos de segurança, impedindo a detecção de ataques em curso.
- **Problema**: Um atacante leva meses exfiltrando dados e ninguém percebe porque não há logs.
- **Mitigação**: Registrar falhas de login, acessos de alto privilégio e integrar com sistemas SIEM.

### 10. 🔌 A10:2021-Server-Side Request Forgery (SSRF)
A aplicação web faz uma requisição para um destino arbitrário sem validar a URL.
- **Ataque**: Fazer o servidor acessar seus próprios serviços internos (como metadados de nuvem ou bancos de dados internos).
- **Mitigação**: Usar allow-lists de domínios e protocolos permitidos.

## 💡 Conclusão
Dominar o OWASP Top 10 é o primeiro passo para qualquer profissional de segurança. Ele serve como o checklist base para auditorias e testes de invasão em todo o mundo.

---
**Tags:** `OWASP`, `Web-Security`, `Checklist`, `AppSec`, `Pentest-Basic`, `Risk-Analysis`