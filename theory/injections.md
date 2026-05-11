# 💉 Injeções: Onde o Código vira Arma

A injeção ocorre quando você consegue "enganar" um sistema para executar comandos que ele não deveria. É como convencer o segurança de um prédio que você é o dono, apenas mudando a forma como você fala.

## 🗄️ SQL Injection (SQLi): Dominando o Banco de Dados
A aplicação espera um nome, mas você envia um comando.

### 🚩 Tipos de SQLi Detalhados:
1. **In-Band (Classic)**: A forma mais fácil. Os resultados são exibidos diretamente na página ou em erros.
   - **Union-Based**: Usa o operador `UNION` para combinar resultados de tabelas diferentes. Ex: `' UNION SELECT username, password FROM users --`
   - **Error-Based**: Força o banco a gerar um erro que contém a informação desejada.
2. **Inferential (Blind)**: O site não mostra o erro.
   - **Boolean-Based**: Você faz perguntas de Sim/Não. Ex: `' AND (SELECT SUBSTR(user,1,1) FROM users)='a`
   - **Time-Based**: Você faz o banco "dormir" se a condição for verdadeira. Ex: `' AND IF(1=1, SLEEP(5), 0) --`
3. **Out-of-Band**: Os dados são enviados para um servidor externo (DNS loggers) quando as outras técnicas falham.

### 🧪 Exemplo Prático de Bypass de Login:
- **Cenário**: `SELECT * FROM usuarios WHERE user = '$user' AND pass = '$pass'`
- **Payload**: `admin' #` (O `#` ou `--` anula a verificação da senha no MySQL).

## 💻 Command Injection: Assumindo o Servidor
Ocorre quando o site chama o sistema operacional de forma insegura, geralmente usando funções como `exec()`, `system()` ou `shell_exec()`.

### 🚩 Como identificar:
Procure por campos que pareçam interagir com o sistema: geradores de PDF, ferramentas de rede (ping/traceroute), redimensionadores de imagem.

### 🧪 Operadores de Encadeamento:
- `;` ou `\n`: Executa o segundo comando após o primeiro.
- `&&`: Executa o segundo apenas se o primeiro tiver sucesso.
- `||`: Executa o segundo apenas se o primeiro falhar.
- `|` (Pipe): Passa a saída do primeiro para o segundo.

**Ataque Real**: `8.8.8.8 && whoami && hostname && ip a` (Revela usuário, nome da máquina e endereços IP).

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