# MK - Website

My personal website built with [Hugo](https://gohugo.io/) and [Hugo Academic CV (Hugo Blox)](https://hugoblox.com/templates/) theme. It has Portuguese and English versionn, hosted in GitHub Pages.

---

## Tecnologias

- **[Hugo](https://gohugo.io/)** `v0.136.5` — gerador de site estático
- **[Hugo Blox Builder](https://hugoblox.com/)** — tema Academic CV
- **[Tailwind CSS](https://tailwindcss.com/)** `v4` — estilização
- **[Pagefind](https://pagefind.app/)** — busca estática no lado do cliente
- **[Netlify](https://www.netlify.com/)** — hospedagem e deploy contínuo

---

## Estrutura do projeto

```
.
├── assets/         # CSS, JS e outros assets processados
├── config/         # Configurações do Hugo (hugo.yaml, menus, idiomas, etc.)
├── content/
│   ├── en/         # Conteúdo em inglês
│   └── pt/         # Conteúdo em português
├── i18n/           # Strings de tradução
├── layouts/        # Templates e shortcodes customizados
├── static/         # Arquivos estáticos (imagens, fonts, etc.)
├── publications.bib # Referências bibliográficas (BibTeX)
├── hugoblox.yaml   # Configuração do Hugo Blox Builder
├── netlify.toml    # Configuração de build e deploy no Netlify
└── package.json    # Dependências Node (Tailwind CSS)
```

---

## Manual do Site

Para instruções detalhadas sobre como editar conteúdo, traduções, publicações e posts, consulte o **[Manual do Site](docs/MANUAL_DO_SITE.md)**.

---

## Pré-requisitos

- [Hugo Extended](https://gohugo.io/installation/) `v0.136.5` ou superior
- [Go](https://go.dev/dl/) `v1.19` ou superior (necessário para os módulos Hugo)
- [Node.js](https://nodejs.org/) `v18` ou superior (necessário para o Tailwind CSS)

---

## Executando localmente

**1. Clone o repositório**

```bash
git clone <url-do-repositorio>
cd <pasta-do-projeto>
```

**2. Instale as dependências Node**

```bash
npm install
```

**3. Baixe os módulos Hugo**

```bash
hugo mod download
```

**4. Inicie o servidor de desenvolvimento**

```bash
hugo server
```

O site estará disponível em `http://localhost:1313`.

Para incluir conteúdo marcado como futuro (rascunhos e posts agendados):

```bash
hugo server --buildDrafts --buildFuture
```

---

## Build para produção

```bash
hugo --gc --minify
```

O site gerado ficará na pasta `public/`. Para também gerar o índice de busca:

```bash
hugo --gc --minify && npx pagefind --source 'public'
```

---

## Idiomas

O site está disponível em dois idiomas configurados em `config/_default/`:

| Idioma     | Caminho do conteúdo |
|------------|---------------------|
| Inglês     | `content/en/`       |
| Português  | `content/pt/`       |

Consulte [`MULTILANGUAGE_IMPLEMENTATION.md`](./MULTILANGUAGE_IMPLEMENTATION.md) para mais detalhes sobre a implementação multilíngue.

---

## Deploy

O deploy é feito automaticamente pelo Netlify a cada push na branch principal. As configurações de build estão em [`netlify.toml`](./netlify.toml).
