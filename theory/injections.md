# 💉 Injeções: Onde o Código vira Arma

A injeção ocorre quando você consegue "enganar" um sistema para executar comandos que ele não deveria. É como convencer o segurança de um prédio que você é o dono, apenas mudando a forma como você fala.

## 🗄️ SQL Injection (SQLi): Dominando o Banco de Dados
A aplicação espera um nome, mas você envia um comando.
- **Cenário de Login**: 
  - O que o site faz: `SELECT * FROM usuarios WHERE user = 'admin' AND pass = '123'`
  - O seu truque: No campo de senha, você digita `' OR 1=1 --`
  - O resultado final: `SELECT * FROM usuarios WHERE user = 'admin' AND pass = '' OR 1=1 --'`
  - **O que aconteceu?** O `--` comenta o resto da query, e `1=1` é sempre verdade. Você logou sem senha!

## 💻 Command Injection: Assumindo o Servidor
Ocorre quando o site chama o sistema operacional.
- **Exemplo**: Um site que testa se um IP está online usando `ping`.
- **Ataque**: No campo de IP, você digita `8.8.8.8 ; cat /etc/passwd`
- **O desastre**: O servidor executa o ping e logo em seguida mostra todos os usuários do sistema para você.

## 🛡️ Como se Proteger?
1. **Prepared Statements**: O comando e os dados viajam separados. O banco sabe que o que vem do usuário é *apenas* um texto, nunca um comando.
2. **Never Trust, Always Verify**: Valide tudo. Se espera um número, não aceite letras ou símbolos.
3. **WAF (Web Application Firewall)**: Um filtro que bloqueia tentativas óbvias de injeção antes de chegarem ao servidor.

---
**Tags:** `SQLi`, `RCE`, `Database`, `Sanitização`, `Backend`, `Payloads`