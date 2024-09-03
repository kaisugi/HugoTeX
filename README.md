# HugoTeX

A hugo theme which looks like a LaTeX document.

![screenshot](https://user-images.githubusercontent.com/36184621/154785719-a9ef69da-7672-4e13-bf0d-5565cf0c99e2.png)

**Live Demo: https://hugotex.vercel.app/**

This theme is heavily inspired by [latex-css](https://latex.now.sh/).

## Quick Start

```bash
git clone https://github.com/kaisugi/HugoTeX
cd HugoTeX/exampleSite
hugo server -t ../..
# open http://localhost:1313/
```

Hugo (>= **0.128.0**) is required.

## Config settings

example

```toml
baseURL = "https://hugotex.vercel.app/"
title = "HugoTeX"
languageCode = "en"
DefaultContentLanguage = "en"
enableInlineShortcodes = true
footnoteReturnLinkContents = "^"

[pagination]
  pagerSize = 3

[Params.Author]
  name = "Kaito Sugimoto"
  abstract = """
  I'm a software engineer and a coffee enthusiast in Japan.
  My primary interest lies in the area of natural language processing.
  """

[taxonomies]
  category = "categories"
  tag = "tags"
  series = "series"

[markup]
  [markup.goldmark]
    [markup.goldmark.renderer]
      unsafe = true
  [markup.highlight]
    style = "paraiso-dark" # syntax highlighting style

[Params]
  darkmode = true # set true if you want to enforce dark mode
  # lightmode = true # set true if you want to enforce light mode
```

**By default, dark mode is automatically enabled based on `prefers-color-scheme` media query. If you want to enforce or deactivate this setting, set `darkmode=true` or `lightmode=true` in [Params]** 

### Social media

If you want to enable the generation of Twitter Card or Opengraph `meta` tags so you get nice embeds on Twitter, Facebook and other social media sites, add the following:

```toml
[Params]
  twittercard = true
  opengraph = true
```

See the [Internal Templates](https://gohugo.io/templates/internal/) in Hugo for how to configure this behaviour further.

## Shortcodes

### Sidenotes

[LaTeX.css](https://latex.vercel.app/), which HugoTeX is using, defines syntax for sidenotes. However, as it is a little verbose to write, we provide a Hugo shortcode for that:

```
A sentence deserving a sidenote.{{% sidenote %}}The note itself.{{% /sidenote %}}.
```

The note will be displayed on the right margin on larger screens. On smaller screns the note will be hidden by default and will open when clicking on the superscript number marking the existence of the note.

## For contributors

Any issues or pull requests are welcome.

## LICENSE

MIT

## Similar Projects

- [queensferryme / hugo-theme-texify](https://github.com/queensferryme/hugo-theme-texify/)
