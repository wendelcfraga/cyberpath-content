# Repositório de Conteúdo do CyberPath

![Content](https://img.shields.io/badge/Conteúdo-JSON-brightgreen)

> Hackeie o conhecimento, defenda o futuro.

Este repositório serve como a fonte de conteúdo dinâmica para o aplicativo Android **CyberPath**. Todo o material de aprendizado, incluindo roadmaps, quizzes e laboratórios práticos, é armazenado aqui em formato JSON.

## 🚀 Propósito

O objetivo deste repositório é desacoplar o conteúdo da lógica da aplicação. Isso nos permite atualizar, corrigir e adicionar novos módulos de aprendizado de forma ágil, sem a necessidade de lançar uma nova versão do aplicativo na Google Play Store.

## 📁 Estrutura do Conteúdo

O conteúdo é organizado em diferentes tipos de arquivos JSON, cada um com um propósito específico:

### 1. Roadmaps (`*_roadmap.json`)

* **Exemplo:** `web_hacking_roadmap.json`
* **Função:** Define a estrutura e a ordem dos módulos de aprendizado para uma trilha de conhecimento. Cada objeto no array "roadmap" representa um passo e contém:
    * `id`: Identificador único.
    * `title`: Título do módulo.
    * `description`: Breve descrição.
    * `contentFile`: O nome do arquivo JSON (quiz ou laboratório) associado a este passo.
    * `status`: O estado inicial (geralmente `UNLOCKED` para o primeiro e `LOCKED` para os demais).

### 2. Quizzes (`*_quiz.json`)

* **Exemplo:** `owasp_quiz.json`
* **Função:** Contém uma lista de perguntas de múltipla escolha sobre um tópico específico. A estrutura principal é um array "quiz", onde cada objeto representa uma pergunta com:
    * `id`: Identificador único.
    * `question`: O texto da pergunta.
    * `options`: Um array com as opções de resposta.
    * `correctAnswer`: A resposta correta.
    * `explanation`: Uma explicação detalhada sobre a resposta.

### 3. Laboratórios (`*_lab.json`)

* **Exemplo:** `lab_sqli_01.json`
* **Função:** Descreve um laboratório prático e interativo. A estrutura principal contém os metadados do laboratório e um array "steps" com os passos do desafio. Cada passo pode ter:
    * `id`, `type` (`INFO`, `INPUT_CHALLENGE`, `MULTIPLE_CHOICE`), `title`, `description`.
    * Campos de desafio como `correctAnswer`, `successMessage`, `options`, etc.

## 🤝 Como Contribuir

Novas ideias para quizzes e laboratórios são sempre bem-vindas! Se você deseja contribuir:

1.  Crie um **Fork** deste repositório.
2.  Crie um novo arquivo JSON seguindo a estrutura dos arquivos existentes para o seu novo quiz ou laboratório.
3.  (Opcional) Adicione uma entrada para o seu novo conteúdo em um dos arquivos de roadmap.
4.  Abra um **Pull Request** com uma descrição clara das suas alterações.

## 📄 Licença

Este conteúdo é distribuído sob a licença MIT. Sinta-se à vontade para usar e adaptar para os seus próprios projetos educacionais.
