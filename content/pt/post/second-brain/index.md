---
title: 🧠 Aprimore seu pensamento com um segundo cérebro
summary: Crie uma base de conhecimento pessoal e compartilhe seu conhecimento com seus colegas.
date: 2023-10-26
authors:
  - admin
tags:
  - Second Brain
  - Markdown
image:
  caption: 'Crédito da imagem: [**Unsplash**](https://unsplash.com)'
---

Crie uma base de conhecimento pessoal e compartilhe seu conhecimento com seus colegas.

O framework web Hugo Blox capacita você com uma das capacidades de anotações mais flexíveis que existem.

Crie uma poderosa base de conhecimento que funciona em cima de uma pasta local de arquivos Markdown de texto simples.

Use-a como seu segundo cérebro, compartilhando publicamente seu conhecimento com seus colegas através do seu site, ou através de um repositório GitHub privado e site protegido por senha apenas para você.

## Mapas Mentais

Hugo Blox suporta uma extensão Markdown para mapas mentais.

Com este formato aberto, você pode até editar seus mapas mentais em outras ferramentas populares como Obsidian.

Simplesmente insira um bloco de código Markdown rotulado como `markmap` e opcionalmente defina a altura do mapa mental conforme mostrado no exemplo abaixo.

Mapas mentais podem ser criados simplesmente escrevendo os itens como uma lista Markdown dentro do bloco de código `markmap`, indentando cada item para criar quantos subníveis você precisar:

<div class="highlight">
<pre class="chroma">
<code>
```markmap {height="200px"}
- Módulos Hugo
  - Hugo Blox
  - blox-plugins-netlify
  - blox-plugins-netlify-cms
  - blox-plugins-reveal
```
</code>
</pre>
</div>

renderiza como

```markmap {height="200px"}
- Módulos Hugo
  - Hugo Blox
  - blox-plugins-netlify
  - blox-plugins-netlify-cms
  - blox-plugins-reveal
```

E aqui está um mapa mental mais avançado com formatação, blocos de código e matemática:

<div class="highlight">
<pre class="chroma">
<code>
```markmap
- Mapas Mentais
  - Links
    - [Documentação Hugo Blox](https://docs.hugoblox.com/)
    - [Comunidade Discord](https://discord.gg/z8wNYzb)
    - [GitHub](https://github.com/HugoBlox/hugo-blox-builder)
  - Recursos
    - Formatação Markdown
    - **inline** ~~text~~ *styles*
    - texto
      multilinha
    - `código inline`
    -
      ```js
      console.log('olá');
      console.log('bloco de código');
      ```
    - Matemática: $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$
```
</code>
</pre>
</div>

renderiza como

```markmap
- Mapas Mentais
  - Links
    - [Documentação Hugo Blox](https://docs.hugoblox.com/)
    - [Comunidade Discord](https://discord.gg/z8wNYzb)
    - [GitHub](https://github.com/HugoBlox/hugo-blox-builder)
  - Recursos
    - Formatação Markdown
    - **inline** ~~text~~ *styles*
    - texto
      multilinha
    - `código inline`
    -
      ```js
      console.log('olá');
      console.log('bloco de código');
      ```
    - Matemática: $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$
```

## Destaque

<mark>Destaque</mark> texto importante com `mark`:

```html
<mark>Texto destacado</mark>
```

## Callouts

Use [callouts](https://docs.hugoblox.com/reference/markdown/#callouts) (também conhecidos como _asides_, _hints_ ou _alerts_) para chamar atenção para notas, dicas e avisos.

Ao envolver um parágrafo em `{{%/* callout note */%}} ... {{%/* /callout */%}}`, ele será renderizado como um aside.

```markdown
{{%/* callout note */%}}
Um aside Markdown é útil para exibir avisos, dicas ou definições para seus leitores.
{{%/* /callout */%}}
```

renderiza como

{{% callout note %}}
Um aside Markdown é útil para exibir avisos, dicas ou definições para seus leitores.
{{% /callout %}}

Ou use o tipo de callout `warning` para que seus leitores não percam detalhes críticos:

{{% callout warning %}}
Um aside Markdown é útil para exibir avisos, dicas ou definições para seus leitores.
{{% /callout %}}

## Você achou esta página útil? Considere compartilhá-la 🙌

