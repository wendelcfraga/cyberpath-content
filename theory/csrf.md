# 🌊 CSRF (Cross-Site Request Forgery): O Sequestro de Sessão

O Cross-Site Request Forgery (CSRF), também conhecido como "Sea-Surf", é um ataque que engana o navegador de uma vítima para que ele envie uma requisição indesejada para uma aplicação onde o usuário está autenticado.

## 🕵️ Como o Ataque Explora o Navegador?
O segredo do CSRF está no comportamento padrão dos navegadores: **eles enviam automaticamente os cookies de um site em todas as requisições feitas para aquele site**, mesmo que a requisição tenha partido de um site diferente (terceiro).

## 🧪 Cenários de Ataque

### 1. CSRF via GET (O mais simples)
Se uma aplicação permite ações sensíveis via GET, o ataque é trivial.
- **URL Vulnerável**: `https://banco.com/transferir?conta=123&valor=1000`
- **Payload**: O atacante coloca uma tag de imagem em seu próprio site: `<img src="https://banco.com/transferir?conta=hacker&valor=1000" style="display:none">`.
- **Resultado**: Assim que a vítima visita o site do hacker, o navegador tenta "baixar a imagem", disparando a transferência bancária silenciosamente.

### 2. CSRF via POST (Usando formulários ocultos)
A maioria das aplicações modernas usa POST, mas isso não as protege sozinhas.
- **Payload**: O hacker cria um formulário HTML que se auto-submete:
```html
<form id="csrf-form" action="https://site.com/perfil/update" method="POST">
  <input type="hidden" name="email" value="hacker@evil.com">
</form>
<script>document.getElementById('csrf-form').submit();</script>
```

## 🛡️ Estratégias de Defesa Definitivas

### 1. Tokens Anti-CSRF (Sincronizados)
O servidor gera um token único e aleatório que deve ser enviado em cada requisição de modificação de estado.
- **Como funciona**: O atacante não consegue ler a página da vítima (devido ao SOP), portanto ele não sabe qual é o token atual e não consegue forjar a requisição.

### 2. Atributo Cookies SameSite
Uma das defesas mais eficazes e modernas. Você instrui o navegador sobre quando enviar o cookie:
- **SameSite=Strict**: O cookie só é enviado se a requisição partir do próprio site.
- **SameSite=Lax**: O cookie é enviado em navegações "top-level" (como clicar em um link), mas não em requisições de subrecursos (como `<img>` ou `<iframe>`). **Este é o padrão atual do Chrome.**

### 3. Verificação de Headers (Origin & Referer)
O servidor verifica se a requisição partiu de um domínio confiável. Embora útil, esses headers podem ser omitidos ou, em casos raros, manipulados.

### 4. Interação do Usuário
Para ações críticas (trocar senha, deletar conta, transferir grandes valores), exija uma re-autenticação, senha ou um CAPTCHA.

---
**Tags:** `CSRF`, `Web-Security`, `Session-Management`, `SameSite`, `Tokens`, `Cookies`
