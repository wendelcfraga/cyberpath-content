# SQL Injection Cego (Blind SQLi)

O Blind SQL Injection ocorre quando uma aplicação é vulnerável a injeção SQL, mas suas respostas HTTP não contêm os resultados da consulta SQL relevante ou quaisquer detalhes do erro do banco de dados.

## Tipos de Blind SQLi

### 1. Baseado em Conteúdo (Boolean-based)
O atacante faz perguntas ao banco de dados que têm respostas "Verdadeiro" ou "Falso". Ele observa se o conteúdo da página muda dependendo da resposta.
*Exemplo:* `?id=1 AND (SELECT 1 FROM users WHERE username='admin' AND password LIKE 'A%')=1`

### 2. Baseado em Tempo (Time-based)
O atacante injeta comandos que fazem o banco de dados esperar um determinado tempo antes de responder se uma condição for verdadeira.
*Exemplo:* `?id=1; IF (1=1) WAITFOR DELAY '0:0:5'--`

## Processo de Extração
Como não vemos os dados diretamente, precisamos extrair informação caractere por caractere (ex: testar se a primeira letra da senha é 'a', depois 'b', etc.), muitas vezes usando ferramentas automatizadas como o **SQLMap**.

## Prevenção
As mesmas técnicas do SQLi tradicional: **Prepared Statements** e validação rigorosa de entradas.