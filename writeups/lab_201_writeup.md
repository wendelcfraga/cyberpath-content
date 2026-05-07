# Write-up: SQL Injection Básico (Bypass de Autenticação)

**Autor:** @cyberpath_staff  
**Dificuldade:** Média  
**Data:** 07/05/2026

## 🎯 Objetivo
O objetivo deste laboratório era obter acesso à área administrativa de um blog fictício sem possuir as credenciais válidas (usuário e senha), explorando uma vulnerabilidade de SQL Injection no formulário de login.

## 🔍 Reconhecimento
Ao analisar o cenário proposto, identificamos que a aplicação utiliza uma consulta SQL insegura para validar o acesso. O código no backend concatena as entradas diretamente:

```sql
SELECT * FROM users WHERE username = '$username' AND password = '$password';
```

Esta estrutura permite que um atacante manipule a lógica da query se os campos não forem devidamente sanitizados.

## 🚀 Exploração
Para contornar a autenticação, precisamos fazer com que a cláusula `WHERE` retorne sempre `true`, independentemente da senha.

1.  **Payload Utilizado:** `' OR '1'='1' --`
2.  **Como funciona:**
    *   O primeiro `'` fecha a aspa simples da string do `username`.
    *   O operador `OR '1'='1'` adiciona uma condição que é matematicamente impossível de ser falsa.
    *   O `--` (espaço no final opcional em alguns DBs) comenta o restante da query original (a parte que verifica o password).

A query final executada no banco de dados torna-se:
```sql
SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = '...';
```

Como `'1'='1'` é verdadeiro, o banco de dados retorna o primeiro usuário da tabela (geralmente o admin), concedendo o acesso.

## 🏁 Conclusão e Flag
Explorar falhas de injeção é um dos métodos mais comuns para comprometimento de dados. A lição aprendida é que nunca devemos confiar em entradas de usuários para montar queries.

**Prevenção:** A melhor defesa é o uso de **Prepared Statements** (Consultas Parametrizadas), onde os dados são tratados separadamente do comando SQL.
