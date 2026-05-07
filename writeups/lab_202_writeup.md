# Write-up: Reflected XSS (Cross-Site Scripting)

**Autor:** @cyberpath_staff  
**Dificuldade:** Fácil  
**Data:** 07/05/2026

## 🎯 Objetivo
O objetivo deste laboratório era demonstrar uma vulnerabilidade de Reflected XSS (XSS Refletido) explorando um campo de pesquisa que não sanitiza a entrada do usuário antes de exibi-la na página.

## 🔍 Reconhecimento
A aplicação possui um recurso de busca. Ao inserir um termo, ele é "refletido" no HTML da página de resultados. O código vulnerável é:

```php
<?php
  $searchTerm = $_GET['q'];
  echo "<p>Resultados para: " . $searchTerm . "</p>";
?>
```

Como o valor de `q` é inserido diretamente no DOM sem codificação, o navegador tentará interpretar qualquer tag HTML ou script JavaScript presente no parâmetro.

## 🚀 Exploração
Para confirmar a vulnerabilidade, inserimos um script simples que gera uma caixa de alerta.

1.  **Payload Utilizado:** `<script>alert('XSS')</script>`
2.  **Como funciona:** 
    *   Ao enviar essa string no campo de busca, o servidor gera o seguinte HTML: `<p>Resultados para: <script>alert('XSS')</script></p>`.
    *   O navegador recebe esse HTML e, ao encontrar a tag `<script>`, executa o JavaScript contido nela, exibindo o alerta.

## 🏁 Conclusão e Flag
O XSS Refletido pode ser usado para roubo de cookies de sessão, redirecionamentos maliciosos ou desfiguração de páginas (defacement).

**Prevenção:** A principal defesa é o **Output Encoding**. Todos os dados dinâmicos devem ser codificados antes de serem inseridos no HTML (ex: converter `<` em `&lt;`). Além disso, implementar uma **Content Security Policy (CSP)** robusta ajuda a mitigar o impacto de scripts não autorizados.
