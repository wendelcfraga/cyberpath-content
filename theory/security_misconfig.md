# Má Configuração de Segurança

A má configuração de segurança é um dos problemas mais comuns, frequentemente resultado de configurações padrão, configurações incompletas ou ad hoc, armazenamento em nuvem aberto, cabeçalhos HTTP mal configurados e mensagens de erro detalhadas contendo informações sensíveis.

## Exemplos Comuns
- **Recursos padrão ativados**: Contas e senhas padrão (ex: admin/admin).
- **Páginas desnecessárias**: Amostras, aplicativos, scripts e páginas de ajuda que não foram removidos.
- **Mensagens de erro detalhadas**: Exibição de stack traces ou outras mensagens de erro informativas para os usuários.
- **Cloud Storage Exposto**: Buckets S3 ou similares com permissões de leitura pública.

## Como Prevenir
- **Processo de Hardening**: Um processo repetível para implantar ambientes seguros.
- **Remover Recursos Desnecessários**: Desinstalar frameworks e componentes que não são usados.
- **Revisar Configurações de Nuvem**: Garantir que as permissões de armazenamento sejam o mais restritas possível.
- **Configurar Cabeçalhos de Segurança**: Implementar HSTS, X-Content-Type-Options, etc.