# Manual do Site — Matias Köhler

> Guia completo para editar conteúdo, traduções, publicações e posts do site.
> Não é necessário saber programar — basta seguir os passos!

---

## Índice

1. [Introdução](#1-introdução)
2. [Estrutura de Pastas](#2-estrutura-de-pastas)
3. [Como Editar Traduções da Interface](#3-como-editar-traduções-da-interface)
4. [Como Adicionar um Novo Idioma](#4-como-adicionar-um-novo-idioma)
5. [Como Editar ou Adicionar uma Publicação](#5-como-editar-ou-adicionar-uma-publicação)
6. [Como Ativar, Adicionar ou Editar um Post no Blog](#6-como-ativar-adicionar-ou-editar-um-post-no-blog)
7. [Como Configurar o Utterances (Comentários)](#7-como-configurar-o-utterances-comentários)
8. [Como Ver o Site Localmente (Prévia)](#8-como-ver-o-site-localmente-prévia)
9. [Glossário](#9-glossário)

---

## 1. Introdução

Este site foi criado com o **Hugo**, um programa que transforma arquivos de texto simples em páginas de internet. Você não precisa escrever código HTML: basta editar arquivos de texto no formato **Markdown** (`.md`) e o Hugo gera o site automaticamente.

### Conceitos básicos

| Termo | O que é |
|-------|---------|
| **Markdown** | Um formato de texto simples que usa símbolos como `#` para títulos e `**texto**` para negrito. Os arquivos terminam em `.md`. |
| **Frontmatter** | O bloco de informações no início de cada arquivo `.md`, delimitado por `---`. É onde ficam título, data, autores, etc. |
| **YAML** | O formato usado nos arquivos de configuração (`.yaml`). Usa recuos (espaços) para organizar informações hierarquicamente. |

### Como funciona na prática

1. Você edita um arquivo de texto (`.md` ou `.yaml`)
2. O Hugo lê esse arquivo e gera a página correspondente
3. Ao fazer push para o GitHub, o site é publicado automaticamente via Netlify

---

## 2. Estrutura de Pastas

Abaixo está um mapa simplificado das pastas mais importantes do projeto:

```
website/
├── config/                  ← Configurações do site
│   └── _default/
│       ├── languages.yaml   ← Idiomas disponíveis (EN, PT)
│       ├── menus.yaml       ← Links do menu de navegação
│       └── params.yaml      ← Configurações gerais (comentários, aparência, etc.)
│
├── content/                 ← Todo o conteúdo do site
│   ├── en/                  ← Conteúdo em inglês
│   │   ├── authors/         ← Perfil do autor
│   │   ├── publication/     ← Publicações científicas
│   │   └── post/            ← Posts do blog
│   └── pt/                  ← Conteúdo em português (mesma estrutura)
│       ├── authors/
│       ├── publication/
│       └── post/
│
├── i18n/                    ← Traduções de textos da interface
│   ├── en.yaml              ← Textos em inglês ("Back to top", "PDF", etc.)
│   └── pt.yaml              ← Textos em português ("Voltar para o topo", "PDF", etc.)
│
├── layouts/                 ← Templates visuais customizados
├── static/                  ← Imagens e arquivos estáticos
└── docs/                    ← Documentação (você está aqui!)
```

**Regra de ouro:** para cada arquivo em `content/en/`, deve existir um correspondente em `content/pt/` (e vice-versa) para que o conteúdo apareça em ambos os idiomas.

---

## 3. Como Editar Traduções da Interface

Os textos fixos da interface do site (botões, rótulos, mensagens) ficam nos arquivos de tradução dentro da pasta `i18n/`.

### O que são esses arquivos?

- `i18n/en.yaml` — textos em inglês
- `i18n/pt.yaml` — textos em português

Cada arquivo contém uma lista de pares `id` + `translation`. O `id` é um identificador interno (não mude!) e o `translation` é o texto que aparece no site.

### Formato do arquivo

```yaml
- id: back_to_top
  translation: Voltar para o topo

- id: btn_pdf
  translation: PDF
```

### Passo a passo: alterar uma tradução existente

**Exemplo:** mudar o texto "Voltar para o topo" para "Voltar ao topo".

1. Abra o arquivo `i18n/pt.yaml`
2. Procure pelo texto que deseja alterar. Neste caso, procure por `back_to_top`:
   ```yaml
   - id: back_to_top
     translation: Voltar para o topo
   ```
3. Altere apenas o valor de `translation`:
   ```yaml
   - id: back_to_top
     translation: Voltar ao topo
   ```
4. Salve o arquivo

**Cuidados importantes:**
- **Nunca altere o valor de `id`** — ele é usado internamente pelo site
- Mantenha o recuo (espaços) exatamente como está — YAML é sensível a espaços
- Se o texto contiver caracteres especiais como `:` ou `#`, coloque-o entre aspas: `translation: "Texto: especial"`

---

## 4. Como Adicionar um Novo Idioma

Atualmente o site possui dois idiomas: inglês (EN) e português (PT). Veja como adicionar um terceiro — usaremos **espanhol (ES)** como exemplo.

### Passo 1: Criar entrada no arquivo de idiomas

Abra `config/_default/languages.yaml` e adicione um bloco para o novo idioma no final do arquivo:

```yaml
# Español
es:
  languageCode: es
  languageName: Español
  contentDir: content/es
  title: "Matias Köhler | Botanizando en todas partes"
  weight: 3
  params:
    description: "Sitio personal del botánico Prof. Matias Köhler"
    header:
      navbar:
        logo:
          text: "🌳🌴🌿 Botanizando en todas partes"
  menu:
    main:
      - name: Bio
        url: /es/
        weight: 10
      - name: Publicaciones
        url: /es/publication/
        weight: 11
```

O campo `weight` define a ordem do idioma no seletor (1 = primeiro, 2 = segundo, etc.).

### Passo 2: Criar a pasta de conteúdo

Crie a pasta `content/es/` e copie a estrutura de outro idioma como base:

```
content/es/
├── authors/
│   └── admin/
│       └── _index.md
├── publication/
│   └── (copiar as publicações de content/en/publication/)
├── post/
│   └── (copiar os posts de content/en/post/)
└── _index.md
```

A maneira mais fácil é copiar toda a pasta `content/en/` para `content/es/` e depois traduzir os textos.

### Passo 3: Criar o arquivo de traduções da interface

Copie o arquivo `i18n/en.yaml` para `i18n/es.yaml` e traduza os textos:

```yaml
- id: back_to_top
  translation: Volver arriba

- id: btn_pdf
  translation: PDF

- id: abstract
  translation: Resumen
```

### Passo 4: Traduzir o conteúdo

Abra cada arquivo `index.md` dentro de `content/es/` e traduza:
- O título (`title`)
- O resumo (`summary` ou `abstract`)
- O texto do corpo (tudo que vem depois do segundo `---`)

**Não altere** campos técnicos como `date`, `doi`, `url_pdf` — eles permanecem iguais em todos os idiomas.

### Passo 5: Verificar

Rode o site localmente (veja [Seção 8](#8-como-ver-o-site-localmente-prévia)) e clique no seletor de idioma para conferir se o espanhol aparece corretamente.

---

## 5. Como Editar ou Adicionar uma Publicação

### Onde ficam as publicações?

Cada publicação é uma **pasta** dentro de `content/{idioma}/publication/`. Por exemplo:

```
content/en/publication/kohler-tuna-2025/
├── index.md        ← Informações da publicação
├── cite.bib        ← Referência bibliográfica (opcional)
└── featured.jpg    ← Imagem de capa (opcional)
```

### Campos do frontmatter explicados

O frontmatter fica no início do arquivo `index.md`, entre dois `---`. Cada campo tem uma função:

| Campo | O que é | Exemplo |
|-------|---------|---------|
| `title` | Título da publicação | `"Proposal to reject the name..."` |
| `authors` | Lista de autores. Use `admin` para o dono do site | `- admin` / `- Lucas C. Majure` |
| `date` | Data de publicação (formato: ANO-MÊS-DIA) | `2025-06-23` |
| `publishDate` | Data em que aparece no site (geralmente igual a `date`) | `'2025-06-23'` |
| `publication_types` | Tipo: `article-journal`, `paper-conference`, `thesis`, `book` | `- article-journal` |
| `publication` | Nome da revista/conferência (use `*` para itálico) | `'*TAXON*'` |
| `doi` | DOI do artigo | `10.1002/tax.13365` |
| `abstract` | Resumo do artigo | Texto livre |
| `tags` | Palavras-chave (lista) | `- Cactaceae` / `- Plant Taxonomy` |
| `url_pdf` | Link direto para o PDF | `https://...` |
| `image.caption` | Legenda da imagem de capa | `'Taxon 74(3), 2025'` |
| `links` | Links adicionais (nome + URL) | Ver exemplo abaixo |

### Passo a passo: editar uma publicação existente

1. Navegue até a pasta da publicação. Exemplo: `content/en/publication/kohler-tuna-2025/`
2. Abra o arquivo `index.md`
3. Altere os campos desejados no frontmatter (entre os `---`)
4. Salve o arquivo
5. **Lembre-se:** repita a edição no outro idioma (`content/pt/publication/kohler-tuna-2025/index.md`)

### Passo a passo: criar uma nova publicação

1. Crie uma nova pasta em `content/en/publication/` com um nome descritivo (use letras minúsculas, sem espaços, separando palavras com `-`). Exemplo: `silva-orchids-2026`
2. Dentro dessa pasta, crie o arquivo `index.md` usando o modelo abaixo
3. Preencha todos os campos
4. (Opcional) Adicione um arquivo `cite.bib` com a referência BibTeX
5. (Opcional) Adicione uma imagem `featured.jpg` ou `featured.png`
6. **Repita os passos 1–5 em `content/pt/publication/`** com o título e resumo traduzidos

### Modelo pronto para copiar (publicação)

Copie o bloco abaixo, cole em um novo arquivo `index.md` e preencha:

```yaml
---
title: "Título da publicação aqui"
authors:
- admin
- Nome do Segundo Autor
- Nome do Terceiro Autor
date: 2026-01-15
publishDate: '2026-01-15'
publication_types:
- article-journal
publication: '*Nome da Revista*'
doi: "10.xxxx/xxxxx"
abstract: "Escreva o resumo da publicação aqui."
tags:
- Palavra-chave 1
- Palavra-chave 2
url_pdf: "https://link-para-o-pdf.com"
links:
- name: URL
  url: "https://link-do-artigo.com"
image:
  caption: 'Legenda da imagem'
  focal_point: ""
---
```

---

## 6. Como Ativar, Adicionar ou Editar um Post no Blog

### O Blog está desativado?

Sim! Atualmente o Blog existe no site mas **não aparece no menu de navegação** porque as linhas correspondentes estão comentadas (desativadas) nos arquivos de configuração.

### Como ativar o Blog no menu

Você precisa descomentar (remover o `#`) as linhas do Blog em **dois** arquivos:

**Arquivo 1: `config/_default/menus.yaml`** (menu em inglês)

Antes (desativado):
```yaml
  #- name: Blog
  #  url: /post/
  #  weight: 12
```

Depois (ativado):
```yaml
  - name: Blog
    url: /post/
    weight: 12
```

**Arquivo 2: `config/_default/languages.yaml`** (menu em português)

Antes (desativado):
```yaml
      #- name: Blog
      #  url: /pt/post/
      #  weight: 12
```

Depois (ativado):
```yaml
      - name: Blog
        url: /pt/post/
        weight: 12
```

**Atenção ao recuo (espaços)!** Em YAML, os espaços no início da linha definem a hierarquia. Mantenha o mesmo alinhamento dos itens vizinhos.

### Estrutura de um post

Cada post é uma pasta dentro de `content/{idioma}/post/`:

```
content/en/post/data-visualization/
├── index.md        ← Conteúdo do post
├── featured.jpg    ← Imagem de destaque (opcional)
└── line-chart.json ← Dados extras, se houver (opcional)
```

### Campos do frontmatter de um post

| Campo | O que é | Exemplo |
|-------|---------|---------|
| `title` | Título do post | `"Meu primeiro post"` |
| `summary` | Resumo curto (aparece na listagem) | `"Um resumo sobre o tema."` |
| `date` | Data de publicação (ANO-MÊS-DIA) | `2026-03-08` |
| `authors` | Lista de autores | `- admin` |
| `tags` | Palavras-chave | `- Botânica` / `- Pesquisa` |
| `image.caption` | Crédito/legenda da imagem | `'Foto: Unsplash'` |
| `comments` | Ativar/desativar comentários neste post | `true` ou `false` |

### Passo a passo: criar um novo post

1. Crie uma nova pasta em `content/en/post/`. Exemplo: `meu-novo-post`
2. Dentro dela, crie o arquivo `index.md` usando o modelo abaixo
3. Preencha o frontmatter e escreva o conteúdo do post após o segundo `---`
4. (Opcional) Adicione uma imagem `featured.jpg` na mesma pasta
5. Repita em `content/pt/post/` com o conteúdo traduzido

### Passo a passo: editar um post existente

1. Navegue até a pasta do post. Exemplo: `content/en/post/data-visualization/`
2. Abra o `index.md`
3. Edite o frontmatter ou o conteúdo de texto
4. Salve e repita no outro idioma

### Modelo pronto para copiar (post)

```yaml
---
title: "Título do post"
summary: "Um breve resumo do que trata este post."
date: 2026-03-08
authors:
  - admin
tags:
  - Palavra-chave 1
  - Palavra-chave 2
image:
  caption: 'Crédito da imagem'
---

Escreva o conteúdo do post aqui usando Markdown.

## Subtítulo

Texto normal, **negrito**, *itálico*.

- Item de lista
- Outro item
```

### Como adicionar imagens ao post

Para usar uma imagem dentro do texto do post, coloque o arquivo de imagem na mesma pasta do `index.md` e referencie assim no Markdown:

```markdown
![Descrição da imagem](nome-do-arquivo.jpg)
```

Para a imagem de destaque (que aparece no topo e na listagem), basta nomeá-la como `featured.jpg` ou `featured.png` e colocá-la na pasta do post.

---

## 7. Como Configurar o Utterances (Comentários)

### O que é o Utterances?

O **Utterances** é um sistema de comentários que usa as Issues do GitHub. Quando alguém comenta em um post do blog, o comentário é salvo como uma Issue no repositório do GitHub. É gratuito e não exige cadastro além de uma conta no GitHub.

### Configuração atual

O Utterances já está configurado neste site. As configurações ficam em `config/_default/params.yaml`:

```yaml
comments:
  provider: utterances
  utterances:
    repo: "tunasdelsur/website"
    issue_term: pathname
    theme: preferred-color-scheme
    label: "💬 comments"
    crossorigin: anonymous
```

### O que cada campo faz

| Campo | O que é | Valor atual |
|-------|---------|-------------|
| `provider` | Sistema de comentários usado | `utterances` |
| `repo` | Repositório GitHub onde as Issues são criadas | `"tunasdelsur/website"` |
| `issue_term` | Como os comentários são organizados: por URL da página | `pathname` |
| `theme` | Aparência dos comentários (acompanha o tema do site) | `preferred-color-scheme` |
| `label` | Rótulo aplicado às Issues no GitHub | `"💬 comments"` |

### Passo a passo: configurar em um novo repositório

Se você migrar o site para outro repositório GitHub:

1. Acesse [github.com/apps/utterances](https://github.com/apps/utterances) e instale o app no novo repositório
2. Abra `config/_default/params.yaml`
3. Altere o campo `repo` para o novo repositório:
   ```yaml
   repo: "seu-usuario/novo-repositorio"
   ```
4. Certifique-se de que as **Issues estão habilitadas** no repositório (Settings → Features → Issues)

### Como alterar o tema dos comentários

No campo `theme`, você pode usar:
- `preferred-color-scheme` — acompanha o tema claro/escuro do site (recomendado)
- `github-light` — sempre claro
- `github-dark` — sempre escuro

### Como alterar o rótulo (label)

Mude o campo `label` em `config/_default/params.yaml`:
```yaml
label: "comentários"
```

### Como desativar comentários em um post específico

Adicione `comments: false` no frontmatter do post:

```yaml
---
title: "Meu post sem comentários"
date: 2026-03-08
comments: false
---
```

### Como desativar comentários globalmente

Em `config/_default/params.yaml`, altere o provider para vazio:

```yaml
comments:
  provider: ""
```

Ou remova/comente todo o bloco `comments`.

---

## 8. Como Ver o Site Localmente (Prévia)

Antes de publicar, é possível ver o site no seu computador para conferir se as alterações ficaram corretas.

### Pré-requisitos

Você precisa ter instalados:
- **Hugo Extended** (versão 0.136.5 ou superior) — [instruções de instalação](https://gohugo.io/installation/)
- **Node.js** (versão 18 ou superior) — [download](https://nodejs.org/)
- **Go** (versão 1.19 ou superior) — [download](https://go.dev/dl/)

### Passo a passo

1. Abra o terminal na pasta do projeto (`website/`)
2. Na primeira vez, instale as dependências:
   ```bash
   npm install
   hugo mod download
   ```
3. Inicie o servidor local:
   ```bash
   hugo server
   ```
4. Abra o navegador e acesse: **http://localhost:1313**
5. O site será atualizado automaticamente sempre que você salvar um arquivo
6. Para parar o servidor, pressione `Ctrl + C` no terminal

**Dica:** para ver posts marcados como rascunho ou com data futura, use:

```bash
hugo server --buildDrafts --buildFuture
```

---

## 9. Glossário

| Termo | Explicação |
|-------|------------|
| **Frontmatter** | Bloco de metadados no início de um arquivo `.md`, delimitado por `---`. Contém informações como título, data, autores. |
| **Hugo** | Programa que gera sites estáticos a partir de arquivos de texto. Não precisa de banco de dados. |
| **Markdown** | Formato de texto simples que usa símbolos para formatação. `# Título`, `**negrito**`, `*itálico*`, `[link](url)`. |
| **YAML** | Formato de arquivo de configuração que usa recuos (espaços) para organizar dados. Usado em `.yaml` e no frontmatter. |
| **Repositório (repo)** | Pasta do projeto no GitHub, onde o código e os arquivos ficam armazenados e versionados. |
| **Push** | Enviar suas alterações locais para o GitHub. Ao fazer push, o site é publicado automaticamente. |
| **Branch** | Uma "ramificação" do projeto. A branch principal (`main`) é a que está publicada no site. |
| **Issue** | Uma discussão/chamado no GitHub. O Utterances usa Issues para armazenar comentários do blog. |
| **Deploy** | O processo de publicar o site na internet. Neste projeto, é feito automaticamente pelo Netlify. |
| **Netlify** | Serviço que hospeda o site e faz o deploy automático sempre que há mudanças no GitHub. |
| **DOI** | Digital Object Identifier — código único que identifica uma publicação científica. Exemplo: `10.1002/tax.13365`. |
| **BibTeX** | Formato de arquivo (`.bib`) usado para referências bibliográficas em trabalhos acadêmicos. |
| **Shortcode** | Atalho especial do Hugo para inserir elementos dinâmicos no texto, como gráficos ou tabelas. |
| **Terminal** | Programa onde você digita comandos de texto (também chamado de "prompt de comando" ou "console"). |
| **i18n** | Abreviação de "internationalization" (internacionalização). Pasta onde ficam as traduções dos textos da interface. |
| **Comentar/Descomentar** | Adicionar ou remover o símbolo `#` no início de uma linha em YAML. Linhas com `#` são ignoradas (desativadas). |

---

**Precisa de ajuda?** Consulte também os documentos técnicos em `docs/`:
- [FEATURES.md](FEATURES.md) — funcionalidades implementadas
- [UTTERANCES_SETUP.md](UTTERANCES_SETUP.md) — detalhes técnicos do Utterances
- [MULTILANGUAGE_IMPLEMENTATION.md](MULTILANGUAGE_IMPLEMENTATION.md) — implementação multilíngue
