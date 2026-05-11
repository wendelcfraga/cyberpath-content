# CSRF (Cross-Site Request Forgery)

O Cross-Site Request Forgery (CSRF) é um ataque que força um usuário autenticado a executar ações indesejadas em uma aplicação web na qual ele está atualmente autenticado.

## Como funciona?
Com um pouco de ajuda de engenharia social (como enviar um link por e-mail ou chat), um atacante pode induzir os usuários de uma aplicação web a executar ações de sua escolha. Se a vítima for um usuário comum, um ataque CSRF bem-sucedido pode comprometer os dados e as operações do usuário. Se a vítima tiver uma conta administrativa, o ataque CSRF pode comprometer toda a aplicação web.

## Exemplo de Cenário
1. O usuário faz login no `bank.com`.
2. O usuário visita um site malicioso enquanto ainda está logado no banco.
3. O site malicioso envia uma requisição oculta para `bank.com/transfer?amount=1000&to=attacker`.
4. O banco processa a requisição porque o navegador enviou automaticamente os cookies de sessão do usuário.

## Como Prevenir
- **Tokens Anti-CSRF**: Um valor único, secreto e imprevisível gerado pela aplicação do lado do servidor para cada sessão do usuário ou requisição.
- **Atributo SameSite em Cookies**: Define se os cookies devem ser enviados em requisições de sites de terceiros.
- **Verificação de Referer e Origin**: Verificar de onde a requisição está vindo.
- **Autenticação de Dois Fatores (2FA)**: Adiciona uma camada extra que o atacante não pode contornar facilmente via CSRF.