# 🛡️ CyberPath Content Repository

[![Content](https://img.shields.io/badge/Content-JSON-brightgreen)](https://github.com/wendelcfraga/cyberpath-content)
[![Status](https://img.shields.io/badge/Status-Active-blue)](https://github.com/wendelcfraga/cyberpath-content)
[![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-orange)](https://github.com/wendelcfraga/cyberpath-content/pulls)
[![License](https://img.shields.io/badge/License-MIT-lightgrey)](LICENSE)

> **O cérebro dinâmico do app CyberPath.**  
> Este repositório armazena todos os Roadmaps, Quizzes, Laboratórios, Resumos e Conquistas exibidos no aplicativo Android. O conteúdo é servido em formato JSON e carregado remotamente, permitindo atualizações em tempo real sem necessidade de publicar uma nova versão na Play Store.

---

## 📋 Índice

- [Visão Geral](#-visão-geral)
- [Como o App Consome Este Repositório](#-como-o-app-consome-este-repositório)
- [Estrutura de Pastas](#-estrutura-de-pastas)
- [Pré-requisitos para Contribuir](#️-pré-requisitos-para-contribuir)
- [Fluxo de Contribuição (Passo a Passo)](#-fluxo-de-contribuição-passo-a-passo)
- [Guia Detalhado por Tipo de Conteúdo](#-guia-detalhado-por-tipo-de-conteúdo)
  - [1. Índices Globais (index/)](#1-índices-globais-index)
  - [2. Roadmaps (roadmaps/)](#2-roadmaps-roadmaps)
  - [3. Quizzes (quizzes/)](#3-quizzes-quizzes)
  - [4. Laboratórios (labs/)](#4-laboratórios-labs)
  - [5. Resumos (summaries/)](#5-resumos-summaries)
  - [6. Conquistas (index/achievements.json)](#6-conquistas-indexachievementsjson)
- [Regras de Qualidade e Boas Práticas](#-regras-de-qualidade-e-boas-práticas)
- [Convenções de Nomenclatura](#-convenções-de-nomenclatura)
- [Validação de JSON](#-validação-de-json)
- [Checklist Antes de Abrir um PR](#checklist-pr)
- [Reportando Bugs de Conteúdo](#-reportando-bugs-de-conteúdo)
- [Código de Conduta](#-código-de-conduta)

---

## 🔭 Visão Geral

O **CyberPath** é um aplicativo Android voltado ao aprendizado de **hacking ético e cibersegurança**. Este repositório é a fonte de dados que alimenta o app. Todo o conteúdo educacional — trilhas de aprendizado, quizzes, laboratórios práticos, resumos teóricos e conquistas — vive aqui na forma de arquivos JSON.

Qualquer pessoa pode contribuir adicionando novo conteúdo, corrigindo erros, melhorando explicações ou criando novos laboratórios e trilhas.

---

## 📡 Como o App Consome Este Repositório

O aplicativo faz requisições HTTP diretamente para os arquivos deste repositório (via raw GitHub ou CDN). Por isso:

- **Não quebre a estrutura de chaves JSON existente** — o app parseia campos por nome exato.
- **Não renomeie nem mova arquivos sem atualizar os índices** — links quebrados resultam em conteúdo invisível no app.
- **Toda alteração mergeada na branch `main` entra em produção imediatamente.**

---

## 📂 Estrutura de Pastas

```
cyberpath-content/
├── index/
│   ├── roadmaps_index.json       # Lista todas as trilhas disponíveis no app
│   ├── labs_index.json           # Lista todos os laboratórios disponíveis
│   └── achievements.json         # Definição de todas as conquistas/badges
│
├── roadmaps/
│   └── web_hacking.json          # Exemplo: trilha de Web Hacking
│
├── quizzes/
│   └── intro_web_quiz.json       # Exemplo: quiz de introdução a web
│
├── labs/
│   └── lab_sqli.json             # Exemplo: laboratório de SQL Injection
│
├── summaries/
│   └── owasp_top10.json          # Exemplo: resumo do OWASP Top 10
│
└── README.md
```

**Regra de ouro:** cada novo arquivo deve ser referenciado em pelo menos um índice (`index/`) para que o app o encontre.

---

## 🛠️ Pré-requisitos para Contribuir

Você só precisa de:

1. Uma conta no [GitHub](https://github.com)
2. Familiaridade básica com JSON (veja [json.org](https://www.json.org/json-pt.html))
3. Um editor de texto — recomendamos [VS Code](https://code.visualstudio.com/) com a extensão **Prettier** para formatar JSON automaticamente
4. (Opcional) [Node.js](https://nodejs.org/) para rodar validações locais de JSON

---

## 🔀 Fluxo de Contribuição (Passo a Passo)

### 1. Faça um Fork do repositório

Clique em **Fork** no canto superior direito da página do repositório no GitHub.

### 2. Clone o seu fork localmente

```bash
git clone https://github.com/<seu-usuario>/cyberpath-content.git
cd cyberpath-content
```

### 3. Crie uma branch descritiva

Use o padrão `tipo/descricao-curta`:

```bash
# Para novo conteúdo:
git checkout -b feat/lab-buffer-overflow

# Para correção:
git checkout -b fix/quiz-owasp-resposta-errada

# Para melhoria de conteúdo existente:
git checkout -b improve/resumo-criptografia
```

### 4. Crie ou edite os arquivos JSON

Siga os schemas detalhados nas seções abaixo.

### 5. Valide o JSON antes de commitar

```bash
# Usando Node.js (valida todos os arquivos JSON do projeto):
node -e "
  const fs = require('fs');
  const path = require('path');
  const glob = require('glob');

  glob.sync('**/*.json').forEach(file => {
    try {
      JSON.parse(fs.readFileSync(file, 'utf8'));
      console.log('✅ OK:', file);
    } catch(e) {
      console.error('❌ ERRO:', file, e.message);
      process.exit(1);
    }
  });
"
```

Ou use ferramentas online como [jsonlint.com](https://jsonlint.com/).

### 6. Commit com mensagem clara

```bash
git add .
git commit -m "feat: adiciona laboratório de buffer overflow para Linux"
```

**Formato de mensagem de commit:**

| Prefixo | Uso |
|---|---|
| `feat:` | Novo conteúdo (lab, quiz, roadmap, resumo) |
| `fix:` | Correção de resposta errada, typo, link quebrado |
| `improve:` | Melhoria de explicação, reescrita de conteúdo |
| `chore:` | Ajustes de formatação, indentação, sem mudança de conteúdo |

### 7. Faça o Push e abra um Pull Request

```bash
git push origin feat/lab-buffer-overflow
```

Em seguida, acesse o GitHub e abra um **Pull Request** para a branch `main` do repositório original. Descreva no PR:

- O que foi adicionado/modificado
- Por que esse conteúdo é relevante
- Se há alguma dependência (ex: requer atualização no índice)

---

## 📖 Guia Detalhado por Tipo de Conteúdo

---

### 1. Índices Globais (`index/`)

Os arquivos de índice são a **porta de entrada** para todo o conteúdo no app. Sempre que criar um novo Roadmap ou Lab, registre-o aqui.

---

#### `roadmaps_index.json`

Lista as trilhas exibidas na aba principal.

```json
[
  {
    "id": "web_hacking",
    "title": "Web Hacking",
    "description": "Aprenda a identificar e explorar vulnerabilidades em aplicações web.",
    "file": "roadmaps/web_hacking.json",
    "icon": "ic_web",
    "totalNodes": 12,
    "estimatedHours": 8,
    "difficulty": "Intermediário",
    "tags": ["OWASP", "XSS", "SQLi", "BurpSuite"]
  }
]
```

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | `string` | ✅ | Identificador único da trilha (snake_case) |
| `title` | `string` | ✅ | Nome exibido no card |
| `description` | `string` | ✅ | Resumo de até 150 caracteres |
| `file` | `string` | ✅ | Caminho relativo para o JSON da trilha |
| `icon` | `string` | ✅ | Nome do drawable no app ou URL de imagem PNG |
| `totalNodes` | `number` | ⚠️ | Quantidade de nós/módulos na trilha |
| `estimatedHours` | `number` | ⚠️ | Estimativa de horas para concluir |
| `difficulty` | `string` | ⚠️ | `"Iniciante"`, `"Intermediário"` ou `"Avançado"` |
| `tags` | `string[]` | ❌ | Palavras-chave para busca futura |

---

#### `labs_index.json`

Lista os laboratórios exibidos na aba Labs.

```json
[
  {
    "id": 1,
    "title": "SQL Injection Básico",
    "category": "Web",
    "difficulty": "Fácil",
    "xp": 150,
    "contentFile": "labs/lab_sqli.json",
    "description": "Aprenda a explorar falhas de SQL Injection em um ambiente controlado.",
    "tags": ["SQLi", "Web", "OWASP"]
  }
]
```

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | `number` | ✅ | ID numérico único e sequencial |
| `title` | `string` | ✅ | Nome do laboratório |
| `category` | `string` | ✅ | Uma das categorias válidas (veja abaixo) |
| `difficulty` | `string` | ✅ | `"Fácil"`, `"Médio"` ou `"Difícil"` |
| `xp` | `number` | ✅ | XP concedido ao concluir (sugestão: Fácil=100, Médio=200, Difícil=350) |
| `contentFile` | `string` | ✅ | Caminho para o JSON do lab |
| `description` | `string` | ⚠️ | Descrição de até 200 caracteres |
| `tags` | `string[]` | ❌ | Palavras-chave |

**Categorias válidas:** `Web`, `Mobile`, `Network`, `Cloud`, `OS`, `Cryptography`, `Forensics`, `Reverse Engineering`

---

### 2. Roadmaps (`roadmaps/`)

Um roadmap organiza o aprendizado em uma sequência lógica de **nós** (módulos). O app exibe os nós como uma trilha interativa, desbloqueando-os progressivamente.

#### Schema completo

```json
{
  "title": "Web Hacking",
  "description": "Trilha completa de hacking em aplicações web.",
  "version": "1.0.0",
  "roadmap": [
    {
      "id": 1,
      "title": "Introdução ao HTTP",
      "description": "Entenda como funciona o protocolo base da web: métodos, headers, status codes e cookies.",
      "iconName": "ic_http",
      "contentFile": "quizzes/http_basics_quiz.json",
      "status": "UNLOCKED",
      "xp": 50,
      "prerequisites": []
    },
    {
      "id": 2,
      "title": "OWASP Top 10",
      "description": "Conheça as 10 vulnerabilidades mais críticas em aplicações web segundo a OWASP.",
      "iconName": "ic_owasp",
      "contentFile": "summaries/owasp_top10.json",
      "status": "LOCKED",
      "xp": 80,
      "prerequisites": [1]
    },
    {
      "id": 3,
      "title": "SQL Injection na Prática",
      "description": "Explore uma aplicação vulnerável e extraia dados do banco de dados.",
      "iconName": "ic_database",
      "contentFile": "labs/lab_sqli.json",
      "status": "LOCKED",
      "xp": 200,
      "prerequisites": [2]
    }
  ]
}
```

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `title` | `string` | ✅ | Nome da trilha |
| `description` | `string` | ⚠️ | Descrição geral |
| `version` | `string` | ⚠️ | Versão semântica (ex: `"1.0.0"`) |
| `roadmap[]` | `array` | ✅ | Lista de nós da trilha |
| `roadmap[].id` | `number` | ✅ | ID único e sequencial dentro da trilha |
| `roadmap[].title` | `string` | ✅ | Título do nó |
| `roadmap[].description` | `string` | ✅ | Descrição do conteúdo |
| `roadmap[].iconName` | `string` | ✅ | Nome do drawable ou URL de ícone |
| `roadmap[].contentFile` | `string` | ✅ | Caminho para quiz, lab ou summary |
| `roadmap[].status` | `string` | ✅ | `"UNLOCKED"` (primeiro nó) ou `"LOCKED"` (demais) |
| `roadmap[].xp` | `number` | ✅ | XP ganho ao concluir o nó |
| `roadmap[].prerequisites` | `number[]` | ⚠️ | IDs dos nós que devem ser concluídos antes |

> ⚠️ **Atenção:** apenas o primeiro nó da trilha deve ter `"status": "UNLOCKED"`. Todos os demais devem começar como `"LOCKED"`.

---

### 3. Quizzes (`quizzes/`)

Quizzes testam conhecimento teórico com perguntas de múltipla escolha. Podem ser vinculados a nós de roadmaps ou existir de forma avulsa.

#### Schema completo

```json
{
  "quizTitle": "Quiz: Fundamentos de HTTP",
  "description": "Teste seus conhecimentos sobre o protocolo HTTP.",
  "passingScore": 70,
  "quiz": [
    {
      "id": 101,
      "question": "Qual método HTTP é utilizado para enviar dados sensíveis em um formulário de login?",
      "options": [
        "GET",
        "POST",
        "PUT",
        "DELETE"
      ],
      "correctAnswer": "POST",
      "explanation": "O método POST envia os dados no corpo da requisição, não na URL, sendo mais adequado para dados sensíveis como senhas. O GET expõe os dados na URL e nos logs do servidor."
    },
    {
      "id": 102,
      "question": "O que significa um status code HTTP 403?",
      "options": [
        "Recurso não encontrado",
        "Requisição inválida",
        "Acesso proibido",
        "Erro interno do servidor"
      ],
      "correctAnswer": "Acesso proibido",
      "explanation": "O código 403 Forbidden indica que o servidor entendeu a requisição, mas se recusa a autorizá-la. Diferente do 401, autenticar-se não resolve o problema."
    }
  ]
}
```

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `quizTitle` | `string` | ⚠️ | Título exibido no cabeçalho do quiz |
| `description` | `string` | ⚠️ | Breve descrição |
| `passingScore` | `number` | ⚠️ | Porcentagem mínima de acertos para "passar" (0–100) |
| `quiz[]` | `array` | ✅ | Lista de perguntas |
| `quiz[].id` | `number` | ✅ | ID único da pergunta |
| `quiz[].question` | `string` | ✅ | Texto da pergunta (termine com `?`) |
| `quiz[].options` | `string[]` | ✅ | Exatamente 4 opções de resposta |
| `quiz[].correctAnswer` | `string` | ✅ | Deve ser **idêntico** a uma das opções |
| `quiz[].explanation` | `string` | ✅ | Explicação detalhada da resposta correta (mín. 30 chars) |

> ✅ **Dica de qualidade:** a `explanation` é um dos campos mais importantes. Explique **por que** a resposta é correta **e** por que as outras estão erradas quando relevante.

---

### 4. Laboratórios (`labs/`)

Labs são experiências interativas que guiam o usuário por um cenário de ataque ou defesa, passo a passo.

#### Schema completo

```json
{
  "labTitle": "SQL Injection Básico",
  "objective": "Explorar uma falha de SQL Injection para extrair credenciais de um banco de dados vulnerável.",
  "scenario": "Você encontrou um portal de login de uma aplicação web. Ao analisar as requisições, percebe que os inputs não são sanitizados...",
  "steps": [
    {
      "id": 1,
      "type": "INFO",
      "title": "Entendendo SQL Injection",
      "content": "SQL Injection ocorre quando dados controlados pelo usuário são inseridos diretamente em queries SQL sem sanitização adequada.\n\nExemplo vulnerável:\n```sql\nSELECT * FROM users WHERE username='$user' AND password='$pass'\n```\n\nSe `$user` for `' OR '1'='1`, a query se torna sempre verdadeira."
    },
    {
      "id": 2,
      "type": "MULTIPLE_CHOICE",
      "title": "Verificação Rápida",
      "question": "Qual dos payloads abaixo é um clássico de SQL Injection para bypass de autenticação?",
      "options": [
        "<script>alert(1)</script>",
        "' OR '1'='1' --",
        "../../../etc/passwd",
        "%00admin"
      ],
      "correctAnswer": "' OR '1'='1' --",
      "explanation": "O payload força a condição WHERE a ser sempre verdadeira (1=1) e o '--' comenta o restante da query, ignorando a verificação de senha."
    },
    {
      "id": 3,
      "type": "INPUT_CHALLENGE",
      "title": "Execute o Ataque",
      "content": "No campo de usuário do formulário de login abaixo, insira o payload correto para fazer bypass da autenticação:",
      "placeholder": "Digite o payload aqui...",
      "correctAnswer": "' OR '1'='1' --",
      "successMessage": "🎉 Perfeito! Você autenticou sem credenciais válidas. A flag é: FLAG{sqli_bypass_success}",
      "failureMessage": "❌ Incorreto. Lembre-se: a condição precisa ser sempre verdadeira e o restante da query deve ser comentado."
    },
    {
      "id": 4,
      "type": "INFO",
      "title": "Como se Defender",
      "content": "Para prevenir SQL Injection:\n\n1. **Prepared Statements**: Use queries parametrizadas.\n2. **ORM**: Use frameworks que abstraem queries SQL.\n3. **Validação de Input**: Rejeite caracteres especiais inesperados.\n4. **Princípio do Menor Privilégio**: O usuário do banco deve ter apenas as permissões necessárias."
    },
    {
      "id": 5,
      "type": "COMPLETION",
      "title": "Laboratório Concluído!",
      "content": "Você aprendeu como identificar e explorar SQL Injection, e também como se defender. Este é um dos ataques mais comuns e devastadores da web — agora você sabe como funciona dos dois lados."
    }
  ]
}
```

#### Tipos de passo (`type`)

| Tipo | Descrição | Campos Extras Obrigatórios |
|---|---|---|
| `INFO` | Texto informativo, pode incluir blocos de código Markdown | — |
| `MULTIPLE_CHOICE` | Pergunta de múltipla escolha integrada ao fluxo | `question`, `options`, `correctAnswer`, `explanation` |
| `INPUT_CHALLENGE` | O usuário digita uma resposta/flag/payload | `placeholder`, `correctAnswer`, `successMessage`, `failureMessage` |
| `COMPLETION` | Passo final que encerra o lab e libera XP | — |

> ⚠️ Todo laboratório **deve** terminar com um passo do tipo `COMPLETION`.

---

### 5. Resumos (`summaries/`)

Resumos fornecem conteúdo teórico denso, geralmente acompanhado de perguntas de fixação ao final.

```json
{
  "summaryTitle": "OWASP Top 10 — 2021",
  "readingTimeMinutes": 10,
  "sections": [
    {
      "id": 1,
      "heading": "O que é OWASP?",
      "body": "A OWASP (Open Web Application Security Project) é uma fundação sem fins lucrativos dedicada a melhorar a segurança de software. O OWASP Top 10 é uma lista das vulnerabilidades mais críticas em aplicações web, atualizada periodicamente com base em dados reais de incidentes."
    },
    {
      "id": 2,
      "heading": "A01:2021 — Broken Access Control",
      "body": "Falhas de controle de acesso permitem que usuários ajam fora de suas permissões pretendidas. Isso pode levar ao acesso não autorizado a dados de outros usuários, modificação ou exclusão de dados, e execução de funções privilegiadas."
    }
  ],
  "reinforcementQuiz": {
    "passingScore": 60,
    "quiz": [
      {
        "id": 201,
        "question": "Qual vulnerabilidade lidera o OWASP Top 10 de 2021?",
        "options": [
          "Injection",
          "Broken Access Control",
          "Cryptographic Failures",
          "Security Misconfiguration"
        ],
        "correctAnswer": "Broken Access Control",
        "explanation": "Em 2021, Broken Access Control subiu para a primeira posição, aparecendo em 94% das aplicações testadas. Em edições anteriores, Injection liderava a lista."
      }
    ]
  }
}
```

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `summaryTitle` | `string` | ✅ | Título do resumo |
| `readingTimeMinutes` | `number` | ⚠️ | Tempo estimado de leitura |
| `sections[]` | `array` | ✅ | Seções do conteúdo |
| `sections[].heading` | `string` | ✅ | Título da seção |
| `sections[].body` | `string` | ✅ | Corpo do texto (suporta Markdown básico) |
| `reinforcementQuiz` | `object` | ⚠️ | Quiz de fixação ao final do resumo |

---

### 6. Conquistas (`index/achievements.json`)

As conquistas são desbloqueadas automaticamente pelo app baseadas em **gatilhos (triggers)** que monitoram o progresso do usuário.

```json
[
  {
    "id": "first_steps",
    "title": "Primeiros Passos",
    "description": "Conclua seu primeiro módulo de qualquer trilha.",
    "icon": "ic_trophy_bronze",
    "xpReward": 50,
    "type": "SINGLE_UNLOCK",
    "category": "ROADMAP",
    "triggerType": "ROADMAP_NODE_COUNT",
    "triggerValue": 1,
    "triggerTarget": null
  },
  {
    "id": "web_hacker",
    "title": "Web Hacker",
    "description": "Complete a trilha de Web Hacking.",
    "icon": "ic_trophy_gold",
    "xpReward": 500,
    "type": "SINGLE_UNLOCK",
    "category": "ROADMAP",
    "triggerType": "ROADMAP_COMPLETED",
    "triggerValue": 1,
    "triggerTarget": "web_hacking"
  },
  {
    "id": "quiz_master",
    "title": "Quiz Master",
    "description": "Acerte 100 perguntas no total.",
    "icon": "ic_trophy_silver",
    "xpReward": 200,
    "type": "INCREMENTAL",
    "category": "QUIZ",
    "triggerType": "TOTAL_CORRECT_ANSWERS",
    "triggerValue": 100,
    "triggerTarget": null
  }
]
```

#### Campos

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | `string` | ✅ | ID único (snake_case) |
| `title` | `string` | ✅ | Nome da conquista |
| `description` | `string` | ✅ | O que o usuário precisa fazer |
| `icon` | `string` | ✅ | Nome do drawable |
| `xpReward` | `number` | ✅ | XP bonus ao desbloquear |
| `type` | `string` | ✅ | `SINGLE_UNLOCK` ou `INCREMENTAL` |
| `category` | `string` | ✅ | Categoria (veja tabela abaixo) |
| `triggerType` | `string` | ✅ | Lógica do gatilho (veja tabela abaixo) |
| `triggerValue` | `number` | ✅ | Valor numérico necessário para ativar |
| `triggerTarget` | `string\|null` | ⚠️ | ID do roadmap ou lab alvo (quando aplicável) |

#### Tipos de conquista (`type`)

| Valor | Comportamento |
|---|---|
| `SINGLE_UNLOCK` | Desbloqueada uma única vez ao atingir o gatilho |
| `INCREMENTAL` | Possui barra de progresso — desbloqueada ao atingir `triggerValue` |

#### Categorias (`category`)

`ROADMAP` · `LAB` · `QUIZ` · `STREAK` · `LEVEL`

#### Gatilhos disponíveis (`triggerType`)

| Gatilho | Descrição | `triggerTarget` |
|---|---|---|
| `ROADMAP_NODE_COUNT` | Nós de roadmap concluídos (total) | `null` |
| `ROADMAP_PERCENT` | % de um roadmap específico concluído | ID do roadmap |
| `ROADMAP_COMPLETED` | Trilha específica 100% concluída | ID do roadmap |
| `TOTAL_LABS` | Total de labs concluídos | `null` |
| `TOTAL_CORRECT_ANSWERS` | Total de respostas corretas em quizzes | `null` |
| `STREAK_DAYS` | Dias consecutivos com atividade | `null` |
| `PERFECT_QUIZZES` | Quizzes concluídos com 100% de acerto | `null` |
| `LEVEL_REACHED` | Nível de XP atingido | `null` |
| `LAB_ID` | Lab específico concluído | ID do lab |

---

## ✅ Regras de Qualidade e Boas Práticas

### JSON

- **Valide sempre** o JSON antes de commitar. Uma vírgula faltando ou aspas extras quebram o parsing no app.
- Use **indentação de 2 espaços** (não tabs).
- Strings com caracteres especiais ou acentos devem estar em **UTF-8** (padrão do Git).

### Conteúdo

- **Precisão técnica:** Não publique conteúdo que não foi verificado. Se não tem certeza, adicione uma nota ou abra uma issue antes.
- **Linguagem:** O conteúdo deve estar em **Português Brasileiro** (pt-BR) por padrão.
- **Explicações:** Prefira exemplos concretos a definições abstratas.
- **Ética:** Todo conteúdo ofensivo deve ser contextualizado em ambientes controlados e legais (CTFs, labs próprios, bug bounty com autorização). Nunca instrua ataques a sistemas reais sem permissão.
- **IDs:** Verifique que o ID que está usando não existe em outro arquivo. IDs duplicados causam comportamentos inesperados no app.

### Imagens e Ícones

- Use drawables existentes no app sempre que possível (prefixo `ic_`).
- Para novos ícones, forneça um PNG com fundo transparente, proporção **1:1**, mínimo **96x96px**.
- Evite ícones com muito texto embutido — perdem qualidade em telas pequenas.

### Caminhos

- Use sempre **caminhos relativos** à raiz do repositório.
  - ✅ `quizzes/http_basics_quiz.json`
  - ❌ `/home/user/cyberpath-content/quizzes/http_basics_quiz.json`
  - ❌ `./quizzes/http_basics_quiz.json`

---

## 📝 Convenções de Nomenclatura

| Tipo de arquivo | Padrão | Exemplo |
|---|---|---|
| Roadmap | `snake_case.json` | `web_hacking.json` |
| Quiz | `snake_case_quiz.json` | `http_basics_quiz.json` |
| Lab | `lab_snake_case.json` | `lab_sqli.json` |
| Resumo | `snake_case.json` | `owasp_top10.json` |
| ID de roadmap (string) | `snake_case` | `web_hacking` |
| ID de lab (numérico) | número inteiro único | `7` |
| ID de conquista (string) | `snake_case` | `web_hacker` |

---

## 🔍 Validação de JSON

Antes de abrir um PR, valide seus arquivos:

**Opção 1 — Online:**  
[jsonlint.com](https://jsonlint.com/) ou [jsonformatter.curiousconcept.com](https://jsonformatter.curiousconcept.com/)

**Opção 2 — Terminal (Node.js):**

```bash
node -e "JSON.parse(require('fs').readFileSync('quizzes/meu_quiz.json', 'utf8')); console.log('✅ JSON válido')"
```

**Opção 3 — Python:**

```bash
python3 -m json.tool quizzes/meu_quiz.json && echo "✅ JSON válido"
```

**Opção 4 — VS Code:**  
Instale a extensão **Prettier** e use `Ctrl+Shift+P > Format Document`.

---
<a name="checklist-pr"></a>
## ☑️ Checklist Antes de Abrir um PR

Antes de submeter seu Pull Request, verifique:

- [ ] O JSON de todos os arquivos criados/editados é válido (sem erros de sintaxe)
- [ ] Novos roadmaps foram adicionados ao `index/roadmaps_index.json`
- [ ] Novos labs foram adicionados ao `index/labs_index.json`
- [ ] Todos os `contentFile` apontam para arquivos que realmente existem no repositório
- [ ] IDs de quizzes, labs e conquistas são únicos no escopo do arquivo
- [ ] Nenhuma pergunta de quiz possui `correctAnswer` diferente das `options`
- [ ] Labs possuem um passo do tipo `COMPLETION` ao final
- [ ] O conteúdo está em Português Brasileiro
- [ ] Explicações de quizzes e labs são claras e tecnicamente corretas
- [ ] A branch segue o padrão `feat/`, `fix/` ou `improve/`
- [ ] A mensagem de commit segue o padrão descrito neste guia

---

## 🐛 Reportando Bugs de Conteúdo

Encontrou uma resposta errada, explicação confusa, link quebrado ou conteúdo desatualizado?

1. Acesse a aba [Issues](https://github.com/wendelcfraga/cyberpath-content/issues)
2. Clique em **New Issue**
3. Use o título no formato: `[BUG] Arquivo: descrição do problema`
   - Exemplo: `[BUG] quizzes/http_basics_quiz.json: resposta correta incorreta na questão 3`
4. Inclua no corpo da issue:
   - Arquivo e ID da questão/passo afetado
   - O que está errado
   - O que deveria estar correto (se souber)

---

## 🤝 Código de Conduta

Este projeto segue o [Contributor Covenant v2.1](https://www.contributor-covenant.org/version/2/1/code_of_conduct/).

Em resumo:

- Seja respeitoso com outros colaboradores
- Críticas construtivas são bem-vindas; ataques pessoais, não
- Conteúdo de hacking é para fins educacionais — nunca instrua atividades ilegais
- Dúvidas? Abra uma issue com a tag `question`

---

<div align="center">

**Hackeie o conhecimento, defenda o futuro.** 💻🛡️

*CyberPath — Seu caminho para a cibersegurança*

</div>
