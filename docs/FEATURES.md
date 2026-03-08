# Novas Funcionalidades — Branch `feature/numbered-publications-list`

> Resumo das alterações introduzidas nesta branch em relação à `main`.

---

## 1. Lista de Publicações Numerada

- Template customizado `layouts/publication/list.html` que exibe as publicações com numeração sequencial.
- Atualização do layout de seção (`layouts/partials/section/publication.html`) para suportar a nova estrutura visual.

## 2. Suporte Multi-idioma (Português / Inglês)

- Configuração de idiomas em `config/_default/languages.yaml` com suporte a `en` e `pt`.
- Todo o conteúdo do site duplicado e traduzido para português em `content/pt/`, incluindo:
  - Perfil do autor (`authors/admin/`)
  - Publicações científicas (~30 artigos)
  - Posts do blog (5 posts)
  - Materiais de ensino (Python e JavaScript)
  - Projetos e experiência
  - Eventos
- Arquivos de tradução de interface em `i18n/en.yaml` e `i18n/pt.yaml` (278 entradas cada).
- Seletor de idioma customizado via `layouts/partials/hooks/head-end/custom-language-switcher.html`.
- Reorganização do conteúdo inglês para `content/en/` (antes na raiz `content/`).
- Reestruturação dos menus para português em `config/_default/menus.yaml`.

## 3. Sistema de Comentários (Utterances)

- Integração do [Utterances](https://utteranc.es/) para comentários em posts do blog via GitHub Issues.
- Partial `layouts/partials/comments.html` com suporte a tema claro/escuro automático.
- Hook `layouts/partials/hooks/content-end.html` que injeta os comentários ao final dos posts.
- Documentação de configuração em `UTTERANCES_SETUP.md`.

## 4. Seção de Blog

- Adição da seção de blog ao site com posts de exemplo.
- Atualização da navegação para incluir o blog nos menus PT e EN.
- Card de artigo customizado (`layouts/_partials/views/card.html`) com layout aprimorado e melhor hierarquia visual.
- Grid de artigos atualizado (`layouts/_partials/views/article-grid.html`).

## 5. Tipografia Inter

- Integração da fonte [Inter](https://fonts.google.com/specimen/Inter) via partial `layouts/_partials/hooks/head-end/custom-fonts.html`.
- Aplicação da fonte em toda a interface por `assets/main.css`.

## 6. Melhorias Visuais e de Layout

- Suporte aprimorado ao modo escuro nas publicações e demais seções.
- Ajustes de espaçamento e layout na seção de publicações.
- Botão GitHub adicionado via `layouts/partials/hooks/head-end/github-button.html`.

---

## Commits desta Branch

| Hash | Descrição |
|------|-----------|
| `88298bd` | Melhoria no layout e estilo do card de artigo |
| `def53d9` | Integração do sistema de comentários Utterances |
| `fe3d0bc` | Adição da seção de blog e atualização da navegação |
| `bef6bfa` | Atualização de layout e espaçamento na seção de publicações |
| `6f96e95` | Integração da fonte Inter |
| `b23e42e` | Reorganização do menu em português e identificadores de gráficos |
| `6894b33` | Correção de títulos e navegação em português |
| `d8aac16` | Expansão de conteúdo: novas publicações, materiais de ensino e eventos |
| `cc061c9` | Implementação do suporte multi-idioma e reestruturação do site |
| `8833647` | Melhoria no suporte ao modo escuro e layout de publicações |
| `ced45fe` | Simplificação do layout do item de publicação |
| `8f61813` | Atualização do layout e configuração de publicações |
| `2834b0e` | Adição da lista de publicações numerada com template customizado |
| `6b9c6e8` | Setup inicial do projeto |

---

*Gerado em 2026-03-03 a partir da branch `feature/numbered-publications-list`.*
