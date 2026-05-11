# 💉 Injeções: Onde o Código vira Arma

A injeção ocorre quando você consegue "enganar" um sistema para executar comandos que ele não deveria. É como convencer o segurança de um prédio que você é o dono, apenas mudando a forma como você fala.

## 🗄️ SQL Injection (SQLi): Dominando o Banco de Dados
A aplicação espera um nome, mas você envia um comando.

### 🚩 Tipos de SQLi:
1. **In-Band (Classic)**: Os resultados são exibidos diretamente na página.
2. **Inferential (Blind)**: O site não mostra o erro, mas você percebe mudanças no tempo de resposta ou no conteúdo da página (Verdadeiro vs Falso).
3. **Out-of-Band**: Os dados são enviados para um servidor externo controlado pelo atacante (ex: via DNS ou HTTP).

### 🧪 Exemplo Prático:
- **Cenário de Login**: 
  - O que o site faz: `SELECT * FROM usuarios WHERE user = 'admin' AND pass = '123'`
  - O seu truque: No campo de senha, você digita `' OR 1=1 --`
  - O resultado final: `SELECT * FROM usuarios WHERE user = 'admin' AND pass = '' OR 1=1 --'`
  - **O que aconteceu?** O `--` comenta o resto da query, e `1=1` é sempre verdade. Você logou sem senha!

## 💻 Command Injection: Assumindo o Servidor
Ocorre quando o site chama o sistema operacional de forma insegura.
- **Exemplo**: Um site que testa se um IP está online usando `ping`.
- **Ataque**: No campo de IP, você digita `8.8.8.8 ; cat /etc/passwd`
- **O desastre**: O servidor executa o ping e logo em seguida mostra todos os usuários do sistema para você.

## 🛠️ Outras Variantes:
- **NoSQL Injection**: Ataques similares contra bancos como MongoDB usando operadores `$gt`, `$ne`.
- **LDAP Injection**: Manipulação de consultas de diretório (comum em redes corporativas).
- **Template Injection (SSTI)**: Injetar código em motores de template como Jinja2 ou Thymeleaf para obter RCE.

## 🛡️ Como se Proteger? (Defesa em Profundidade)
1. **Consultas Parametrizadas (Prepared Statements)**: Essencial. O comando e os dados viajam separados.
2. **Princípio do Menor Privilégio**: O banco de dados da aplicação não deve ter permissões de `root` ou `sysadmin`.
3. **Escaping/Sanitização**: Limpar caracteres especiais (como `'`, `;`, `--`) de todo input.
4. **WAF (Web Application Firewall)**: Uma camada extra para filtrar payloads conhecidos.

---
**Tags:** `SQLi`, `RCE`, `SSTI`, `Database-Security`, `Backend`, `Payloads`, `Sanitization`