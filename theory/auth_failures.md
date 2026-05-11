# 🔑 Falhas de Autenticação: A Porta Mal Fechada

A autenticação é o que impede que qualquer um entre na sua conta. Quando ela falha, o atacante ganha as chaves do reino.

## 🔓 Problemas Comuns (O que procurar?)
- **Senhas Fracas**: Usuários que usam `123456` ou `senha123`.
- **Credential Stuffing**: Atacantes usam listas de e-mails e senhas vazados de *outros* sites para tentar entrar no seu.
- **Força Bruta (Brute Force)**: Tentar milhares de combinações de senha por segundo.
- **Sessões Infinitas**: O site nunca desloga o usuário, permitindo que alguém use o computador dele depois e acesse a conta.

## 🕵️ Cenário de Ataque
Um site não tem limite de tentativas de login. O atacante usa um script para testar as 10.000 senhas mais comuns no usuário `admin`. Em 15 minutos, ele consegue acesso total ao painel de controle.

## 🛡️ Como Blindar o Acesso?
1. **MFA (Multi-Factor Authentication)**: Mesmo que o atacante tenha a senha, ele não tem o código do seu celular. É a defesa nº 1!
2. **Rate Limiting**: Bloquear o IP ou a conta após 5 tentativas erradas.
3. **Bons Hashes**: Nunca salve senhas em texto puro. Use algoritmos modernos como **Argon2** ou **BCrypt**.
4. **Complexidade**: Exigir símbolos, números e letras maiúsculas.

---
**Tags:** `Autenticação`, `MFA`, `Brute-Force`, `Sessões`, `Passwords`, `Identity-Management`