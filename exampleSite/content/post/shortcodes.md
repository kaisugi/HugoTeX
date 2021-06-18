+++
title = "Shortcodes"
description = "A description of theme-specific shortcodes"
date = "2019-02-28"
author = "Hugo Authors"
+++

## Sidenotes

[LaTeX.css](https://latex.vercel.app/), which HugoTeX is using, defines syntax for sidenotes. However, as it is a little verbose to write, we provide a Hugo shortcode for that:

```md
# The content

A sentence, which deserves a sidenote.{{% sidenote %}}The content of the note.{{% /sidenote %}}.
```

Will render into

---
# The content

A sentence, which deserves a sidenote. {% sidenote %}} The content of the note. {{% /sidenote %}}.

---