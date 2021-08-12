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