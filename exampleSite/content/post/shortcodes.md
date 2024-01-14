+++
title = "Shortcodes"
description = "A description of theme-specific shortcodes"
date = "2021-06-21"
author = "Hugo Authors"
+++

Tips for sidenotes.

<!--more-->

## Sidenotes

[LaTeX.css](https://latex.vercel.app/), which HugoTeX is using, defines syntax for sidenotes. However, as it is a little verbose to write, we provide a Hugo shortcode for that:

```md
A sentence deserving a sidenote.{{%/* sidenote */%}}The note itself.{{%/* /sidenote */%}}.
```

Will render into

---
A sentence deserving a sidenote.{{% sidenote %}}The note itself.{{% /sidenote %}}.

---

## Tables

Another shortcode allows to insert tables with captions:

```md
{{< table title="A sample table with a descriptive caption via [LaTeX.css](https://latex.vercel.app/)." >}}
| Header 1      | Header 2      | Header 3      |
|---------------|---------------|---------------|
| Description 1 | Description 2 | Description 3 |
| Description 1 | Description 2 | Description 3 |
| Description 1 | Description 2 | Description 3 |
|---------------|---------------|---------------|
| Footer 1      | Footer 2      | Footer 3      |
{{< /table >}}
```

Will render into

---

{{< table title="A sample table with a descriptive caption via [LaTeX.css](https://latex.vercel.app/)." >}}
| Header 1      | Header 2      | Header 3      |
|---------------|---------------|---------------|
| Description 1 | Description 2 | Description 3 |
| Description 1 | Description 2 | Description 3 |
| Description 1 | Description 2 | Description 3 |
|---------------|---------------|---------------|
| Footer 1      | Footer 2      | Footer 3      |
{{< /table >}}

---
