# Criptografia na Prática

A criptografia é o processo de transformar informações legíveis (texto simples) em um formato ilegível (texto cifrado) para proteger a confidencialidade.

## Criptografia Simétrica vs. Assimétrica

### Simétrica (Chave Única)
- Usa a mesma chave para criptografar e descriptografar.
- **Vantagem**: Rápida.
- **Exemplos**: AES, DES, ChaCha20.

### Assimétrica (Chave Pública/Privada)
- Usa um par de chaves relacionadas. A chave pública criptografa e a privada descriptografa (e vice-versa para assinaturas).
- **Exemplos**: RSA, ECC (Curva Elíptica), Diffie-Hellman.

## Hashing
O hashing transforma dados de qualquer tamanho em um valor de tamanho fixo. É uma função de via única (não pode ser revertida).
- **Usos**: Armazenamento de senhas, integridade de arquivos.
- **Algoritmos Seguros**: Argon2, bcrypt, SHA-256.
- **Algoritmos Inseguros**: MD5, SHA-1.

## TLS e SSL
O TLS (Transport Layer Security) é o sucessor do SSL. Ele protege a comunicação web garantindo:
1. **Confidencialidade** (Criptografia).
2. **Integridade** (MAC).
3. **Autenticação** (Certificados Digitais).

## JWT (JSON Web Tokens)
Padrão para representar reivindicações entre duas partes de forma segura. Frequentemente usado para autenticação em APIs.
- Consiste em: `Header.Payload.Signature`.
- **Atenção**: O payload é apenas codificado em Base64, não criptografado por padrão. Não coloque dados sensíveis lá sem criptografia JWE.