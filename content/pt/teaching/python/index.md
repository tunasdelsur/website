---
title: Aprenda Python
summary: Aprenda Python facilmente em 10 minutos!
date: 2023-10-24
type: docs
math: false
tags:
  - Python
image:
  caption: 'Incorpore mídia rica como vídeos e matemática LaTeX'
---

[Hugo Blox Builder](https://hugoblox.com) é projetado para dar aos criadores de conteúdo técnico uma experiência perfeita. Você pode se concentrar no conteúdo e o Hugo Blox Builder, no qual este modelo é construído, cuida do resto.

**Incorpore vídeos, podcasts, código, matemática LaTeX e até teste alunos!**

Nesta página, você encontrará alguns exemplos dos tipos de conteúdo técnico que podem ser renderizados com Hugo Blox.

## Vídeo

Ensine seu curso compartilhando vídeos com seus alunos. Escolha uma das seguintes abordagens:

{{< youtube D2vj0WcvH5c >}}

**Youtube**:

    {{</* youtube w7Ft2ymGmfc */>}}

**Bilibili**:

    {{</* bilibili id="BV1WV4y1r7DF" */>}}

**Arquivo de vídeo**

Vídeos podem ser adicionados a uma página colocando-os em sua biblioteca de mídia `assets/media/` ou na [pasta da página](https://gohugo.io/content-management/page-bundles/), e então incorporando-os com o shortcode _video_:

    {{</* video src="my_video.mp4" controls="yes" */>}}

## Podcast

Você pode adicionar um podcast ou música a uma página colocando o arquivo MP3 na pasta da página ou na pasta da biblioteca de mídia e então incorporando o áudio em sua página com o shortcode _audio_:

    {{</* audio src="ambient-piano.mp3" */>}}

Experimente:

{{< audio src="ambient-piano.mp3" >}}

## Teste alunos

Forneça uma autoavaliação simples, mas divertida, revelando as soluções para desafios com o shortcode `spoiler`:

```markdown
{{</* spoiler text="👉 Clique para ver a solução" */>}}
Você me encontrou!
{{</* /spoiler */>}}
```

renderiza como

{{< spoiler text="👉 Clique para ver a solução" >}} Você me encontrou 🎉 {{< /spoiler >}}

## Matemática

Hugo Blox Builder suporta uma extensão Markdown para matemática $\LaTeX$. Você pode ativar este recurso alternando a opção `math` em seu arquivo `config/_default/params.yaml`.

Para renderizar matemática _inline_ ou _em bloco_, envolva sua matemática LaTeX com `{{</* math */>}}$...${{</* /math */>}}` ou `{{</* math */>}}$$...$${{</* /math */>}}`, respectivamente.

{{% callout note %}}
Envolvemos a matemática LaTeX no shortcode _math_ do Hugo Blox para evitar que o Hugo renderize nossa matemática como Markdown.
{{% /callout %}}

Exemplo de **bloco matemático**:

```latex
{{</* math */>}}
$$
\gamma_{n} = \frac{ \left | \left (\mathbf x_{n} - \mathbf x_{n-1} \right )^T \left [\nabla F (\mathbf x_{n}) - \nabla F (\mathbf x_{n-1}) \right ] \right |}{\left \|\nabla F(\mathbf{x}_{n}) - \nabla F(\mathbf{x}_{n-1}) \right \|^2}
$$
{{</* /math */>}}
```

renderiza como

{{< math >}}
$$\gamma_{n} = \frac{ \left | \left (\mathbf x_{n} - \mathbf x_{n-1} \right )^T \left [\nabla F (\mathbf x_{n}) - \nabla F (\mathbf x_{n-1}) \right ] \right |}{\left \|\nabla F(\mathbf{x}_{n}) - \nabla F(\mathbf{x}_{n-1}) \right \|^2}$$
{{< /math >}}

Exemplo de **matemática inline** `{{</* math */>}}$\nabla F(\mathbf{x}_{n})${{</* /math */>}}` renderiza como {{< math >}}$\nabla F(\mathbf{x}_{n})${{< /math >}}.

Exemplo de **matemática multilinha** usando a quebra de linha matemática (`\\`):

```latex
{{</* math */>}}
$$f(k;p_{0}^{*}) = \begin{cases}p_{0}^{*} & \text{if }k=1, \\
1-p_{0}^{*} & \text{if }k=0.\end{cases}$$
{{</* /math */>}}
```

renderiza como

{{< math >}}

$$
f(k;p_{0}^{*}) = \begin{cases}p_{0}^{*} & \text{if }k=1, \\
1-p_{0}^{*} & \text{if }k=0.\end{cases}
$$

{{< /math >}}

## Código

Hugo Blox Builder utiliza a extensão Markdown do Hugo para destacar sintaxe de código. O tema do código pode ser selecionado no arquivo `config/_default/params.yaml`.


    ```python
    import pandas as pd
    data = pd.read_csv("data.csv")
    data.head()
    ```

renderiza como

```python
import pandas as pd
data = pd.read_csv("data.csv")
data.head()
```

## Imagens Inline

```go
{{</* icon name="python" */>}} Python
```

renderiza como

{{< icon name="python" >}} Python

## Você achou esta página útil? Considere compartilhá-la 🙌

