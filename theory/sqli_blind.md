# SQL Injection Cego (Blind SQLi): A Arte da Inferência

O Blind SQL Injection é o nível avançado da injeção SQL. Ele ocorre quando o atacante consegue injetar comandos no banco de dados, mas a aplicação **não exibe os resultados** da consulta nem mensagens de erro detalhadas. É como tentar ler um livro em uma sala totalmente escura, onde você só pode fazer perguntas que resultem em "sim" ou "não".

## Tipos de Blind SQLi

### 1. Baseado em Conteúdo (Boolean-based)
Neste cenário, você observa mudanças sutis na resposta da página.
- **A Lógica**: Você injeta uma condição. Se a condição for verdadeira, a página carrega um elemento (ex: "Bem-vindo, usuário"). Se for falsa, o elemento some ou aparece uma mensagem de erro genérica.
- **Exemplo de Raciocínio**: "Se o primeiro caractere da senha do admin for 'A', mostre a página normalmente. Caso contrário, mostre erro."

### 2. Baseado em Tempo (Time-based)
Usado quando a página é idêntica para respostas verdadeiras ou falsas.
- **A Lógica**: Você ordena que o banco de dados "tire uma soneca" (ex: `SLEEP(5)`) se a sua condição for verdadeira.
- **A Medição**: Se o servidor demorar 5 segundos para responder, você sabe que a sua pergunta foi respondida com um "Sim".

## O Processo de Exfiltração
Como você só recebe 1 bit de informação por vez (Sim/Não), extrair uma senha inteira manualmente é exaustivo. 
1. **Descobrir o tamanho**: "A senha tem mais de 5 caracteres? Sim. Mais de 10? Não..."
2. **Descobrir caractere por caractere**: "O primeiro caractere é 'a'? Não. É 'b'? Sim."

Ferramentas como o **SQLMap** automatizam esse processo realizando milhares de perguntas binárias por segundo.

## Estratégias de Prevenção
Não existe "Blind SQLi" se você usar **Prepared Statements**. O banco de dados tratará sua tentativa de "pergunta" apenas como uma string de texto inofensiva.

---
**Tags:** `Blind-SQLi`, `Exfiltration`, `Boolean-Based`, `Time-Based`, `Database-Security`