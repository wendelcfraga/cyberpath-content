# Injeções (Injections)

Injeção é uma das vulnerabilidades mais comuns e perigosas na web. Ocorre quando dados não confiáveis são enviados para um intérprete como parte de um comando ou consulta.

## SQL Injection (SQLi)
Ocorre quando um atacante insere comandos SQL em campos de entrada, manipulando a consulta original ao banco de dados.

### Exemplo:
Consulta original: `SELECT * FROM users WHERE id = '` + id + `'`
Entrada maliciosa: `1' OR '1'='1`
Resultado: `SELECT * FROM users WHERE id = '1' OR '1'='1'`

## Command Injection
Ocorre quando o aplicativo executa comandos do sistema operacional com entrada fornecida pelo usuário sem a devida validação.

## Como Prevenir
1. **Prepared Statements (Parametrização)**: A melhor forma de prevenir SQLi.
2. **Validação de Entrada**: Usar "allow-lists".
3. **Escaping**: Sanitizar caracteres especiais.
4. **Princípio do Menor Privilégio**: O banco de dados deve ter permissões limitadas.