# 💉 Injeções: Onde o Código vira Arma

A injeção ocorre quando uma aplicação falha ao filtrar a entrada do usuário, permitindo que caracteres de controle (como `'`, `;`, `--`) mudem a lógica do comando original que o servidor pretendia executar.

## 🗄️ SQL Injection (SQLi): Manipulando a Lógica do Banco
A aplicação espera um dado (ex: um nome), mas você envia um fragmento de código SQL.

### 🚩 Tipos de SQLi e sua Lógica:
1. **In-Band (Classic)**: A forma direta.
   - **Union-Based**: Explora o comando `UNION` para anexar resultados de tabelas que não deveriam estar expostas. Requer que você descubra o número de colunas primeiro.
   - **Error-Based**: Força o banco a exibir mensagens de erro técnicas. Essas mensagens muitas vezes revelam versões do banco ou nomes de tabelas.
2. **Inferential (Blind)**: O site não mostra dados nem erros.
   - **Boolean-Based**: Você testa condições. Se a página carrega normalmente, a resposta é "Sim"; se der erro ou mudar o conteúdo, é "Não".
   - **Time-Based**: Você pede ao banco para pausar (delay) se uma condição for verdade. Se a resposta demorar, você confirmou a informação.

### 🧪 A Lógica do Bypass de Login
Imagine a consulta: `SELECT * FROM users WHERE username = '$user' AND password = '$pass'`
Se você conseguir fechar a aspa do `$user` precocemente e inserir uma condição lógica que resulte sempre em **VERDADEIRO** (ex: `1=1`), o banco pode ignorar o restante da verificação.

## 💻 Command Injection: Execução no Sistema Operacional
Ocorre quando o servidor passa dados do usuário diretamente para uma shell do sistema (bash, cmd).

### 🚩 Como Identificar Vetores:
Procure por funcionalidades que pareçam fazer tarefas de sistema:
- Ferramentas de diagnóstico de rede (ping, nslookup).
- Conversores de arquivos ou redimensionadores de imagem.
- Visualizadores de logs.

### 🧪 Operadores de Encadeamento
Para injetar comandos, você precisa usar operadores que o sistema operacional entenda para separar instruções:
- `;` ou `\n`: Executa o próximo comando independente do anterior.
- `&&`: Executa o próximo apenas se o primeiro funcionar.
- `||`: Executa o próximo apenas se o primeiro falhar.

## 🛡️ Como se Proteger?
1. **Queries Parametrizadas (Prepared Statements)**: A defesa definitiva. O motor do banco de dados é avisado: "Isto é o comando, e isto são APENAS dados". Mesmo que os dados contenham `'`, eles nunca serão executados.
2. **Princípio do Menor Privilégio**: O usuário do banco de dados nunca deve ser o 'root'.
3. **Allow-listing**: Em vez de tentar bloquear caracteres ruins, permita apenas o que é conhecido como bom (ex: apenas números em um campo de ID).

---
**Tags:** `SQLi`, `RCE`, `Injection-Theory`, `Backend-Security`, `Prepared-Statements`