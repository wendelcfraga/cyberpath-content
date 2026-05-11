# Exposição de Dados Sensíveis

Esta vulnerabilidade ocorre quando uma aplicação não protege adequadamente informações confidenciais, permitindo que atacantes as acessem ou modifiquem.

## O que são Dados Sensíveis?
- Senhas e hashes.
- Números de cartão de crédito.
- Dados de saúde (PHI).
- Informações Pessoais Identificáveis (PII).
- Chaves de API e segredos de criptografia.

## Causas Comuns
- Transmissão de dados em texto simples (sem HTTPS).
- Armazenamento de segredos em repositórios de código (Hardcoding).
- Uso de algoritmos de criptografia fracos ou obsoletos (ex: MD5, SHA1).
- Falta de cabeçalhos de segurança (HSTS).

## Como Prevenir
- **Criptografar dados em repouso e em trânsito**.
- **Não armazenar dados sensíveis desnecessariamente**.
- **Desativar o cache** para respostas que contenham dados sensíveis.
- **Usar funções de derivação de chave fortes** (Argon2, bcrypt) para senhas.