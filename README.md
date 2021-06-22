# HugoTeX

A hugo theme which looks like a LaTeX document.

![screenshot](images/tn.png)

**Live Demo: https://hugotex.netlify.app/**

This theme is heavily inspired by [latex-css](https://latex.now.sh/).

## Quick Start

```bash
git clone https://github.com/HelloRusk/HugoTeX
cd HugoTeX/exampleSite
hugo server -t ../..
# open http://localhost:1313/
```

Hugo (>= **0.77.0**) is required.

## Config settings

example

```toml
baseURL = "https://hugotex.netlify.app/"
title = "HugoTeX"
paginate = 3
languageCode = "en"
DefaultContentLanguage = "en"
enableInlineShortcodes = true
footnoteReturnLinkContents = "^"

[author]
  name = "Kaito Sugimoto"
  abstract = "I'm a software engineer and a coffee enthusiast in Japan. My primary interest lies in the area of natural language processing."

[taxonomies]
category = "categories"
tag = "tags"
series = "series"
```

## Shortcodes

### Sidenotes

[LaTeX.css](https://latex.vercel.app/), which HugoTeX is using, defines syntax for sidenotes. However, as it is a little verbose to write, we provide a Hugo shortcode for that:

```
A sentence deserving a sidenote.{{% sidenote %}}The note itself.{{% /sidenote %}}.
```

The note will be displaied on the right margin on larger screens. On smaller screns the note will be hidden by default and will open when clicking on the superscript number marking the existence of the note.

## For contributors

Any issues or pull requests are welcome.

## LICENSE

MIT

## Similar Projects

- [queensferryme / hugo-theme-texify](https://github.com/queensferryme/hugo-theme-texify/)
