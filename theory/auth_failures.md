# Falhas de Identificação e Autenticação

Esta categoria foca na confirmação da identidade do usuário, autenticação e gerenciamento de sessão.

## Problemas Comuns
- **Permitir senhas fracas**: O sistema não exige complexidade mínima.
- **Credential Stuffing**: O atacante usa listas de nomes de usuários e senhas vazados de outros sites.
- **Sessões que não expiram**: IDs de sessão que permanecem válidos por muito tempo após o logout ou inatividade.
- **Exposição de ID de sessão na URL**: Enviar o identificador da sessão como parâmetro GET.

## Como Prevenir
1. **Implementar MFA (Autenticação de Múltiplos Fatores)**: Aumenta significativamente a segurança.
2. **Políticas de Senha Forte**: Exigir comprimento e complexidade.
3. **Gerenciamento de Sessão Seguro**: Usar IDs de sessão complexos e garantir que sejam destruídos no logout.
4. **Limitação de Tentativas (Rate Limiting)**: Bloquear ou atrasar tentativas após sucessivas falhas.