# HugoTeX

[![Hugo](https://img.shields.io/badge/Hugo-%5E0.158.0-blue.svg)](https://gohugo.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stars](https://img.shields.io/github/stars/kaisugi/HugoTeX?style=social)](https://github.com/kaisugi/HugoTeX/stargazers)

> A LaTeX-inspired Hugo theme for elegant technical writing and academic content

Transform your Hugo site into a beautifully typeset document with the classic aesthetics of LaTeX. Perfect for researchers, mathematicians, and anyone who appreciates excellent typography.

![screenshot](https://user-images.githubusercontent.com/36184621/154785719-a9ef69da-7672-4e13-bf0d-5565cf0c99e2.png)

**[Live Demo →](https://hugotex.vercel.app/)**

## ✨ Features

- 📐 **LaTeX-style Typography** - Classic, elegant document styling inspired by LaTeX
- ⚡ **Server-Side Math Rendering** - KaTeX with zero JavaScript overhead, instant page loads
- 🌓 **Automatic Dark Mode** - Respects system preferences with seamless theme switching
- 📱 **Mobile Optimized** - Fast and responsive on all devices
- 🚀 **Lightning Fast** - No client-side JavaScript required for math rendering
- 🔍 **SEO-Friendly** - Built-in OpenGraph and Twitter Card support
- 📝 **Sidenotes Support** - Elegant margin notes for supplementary content
- 📄 **Article Abstracts** - Automatically displays content before `<!--more-->` as an academic-style abstract
- 🎨 **Customizable** - Easy theming with simple configuration
- ♿ **Accessible** - Works perfectly even with JavaScript disabled

## 🎯 Perfect For

- **Researchers & Academics** - Write papers and notes with LaTeX-quality output
- **Technical Bloggers** - Share tutorials and documentation with beautiful code and math
- **Mathematics Content** - Display complex equations with proper typesetting
- **Science Communicators** - Present technical content in an elegant, readable format
- **Anyone** - Who appreciates clean, professional typography

## 🚀 Quick Start

### Prerequisites

- Hugo >= **0.158.0** ([Download Hugo](https://gohugo.io/installation/))
- Git

### Try It Out

```bash
# Clone the repository
git clone https://github.com/kaisugi/HugoTeX
cd HugoTeX/exampleSite

# Start the development server
hugo server -t ../..

# Open http://localhost:1313/ in your browser
```

## 📦 Installation

### Method 1: Git Submodule (Recommended)

```bash
# Add the theme as a submodule to your Hugo site
cd your-hugo-site
git submodule add https://github.com/kaisugi/HugoTeX.git themes/HugoTeX

# Update your config
echo 'theme = "HugoTeX"' >> hugo.toml
```

### Method 2: Hugo Modules

```bash
# Initialize your site as a Hugo module
hugo mod init github.com/yourusername/yoursite

# Add to your hugo.toml
cat >> hugo.toml << EOF
[module]
  [[module.imports]]
    path = "github.com/kaisugi/HugoTeX"
EOF

# Get the theme
hugo mod get
```

### Method 3: Direct Clone

```bash
# Clone directly into themes directory
cd your-hugo-site/themes
git clone https://github.com/kaisugi/HugoTeX.git
```

## ⚙️ Configuration

### Basic Setup

Create or update your `hugo.toml`:

```toml
baseURL = "https://example.com/"
title = "My Hugo Site"
theme = "HugoTeX"
languageCode = "en"
DefaultContentLanguage = "en"
enableInlineShortcodes = true
footnoteReturnLinkContents = "^"

[pagination]
  pagerSize = 10

[Params]
  darkmode = true  # Set to true to enforce dark mode
  # lightmode = true  # Set to true to enforce light mode
  [Params.Favicon]
    ico = "/favicon.ico"
    svg = "/favicon.svg"
    png = "/favicon.png"

[Params.Author]
  name = "Your Name"
  abstract = """
  Your bio goes here. This appears on the homepage.
  """

[taxonomies]
  category = "categories"
  tag = "tags"
  series = "series"

[markup]
  [markup.goldmark]
    [markup.goldmark.renderer]
      unsafe = true
    [markup.goldmark.extensions]
      [markup.goldmark.extensions.passthrough]
        enable = true
        [markup.goldmark.extensions.passthrough.delimiters]
          inline = [['$', '$']]
          block = [['$$', '$$']]
  [markup.highlight]
    style = "paraiso-dark"  # Syntax highlighting style
```

### Theme Options

**Dark Mode Control**

By default, dark mode automatically activates based on the user's system `prefers-color-scheme` setting.

- Set `darkmode = true` to enforce dark mode
- Set `lightmode = true` to enforce light mode
- Omit both for automatic switching

### Favicon Support

Define icon paths once under `[Params.Favicon]`. Every field is optional; only provided values are rendered.
The recommended setup uses `/favicon.ico`, `/favicon.svg`, and `/favicon.png`.
`ico` should point to a multi-size `.ico` file, at minimum 16, 32, and 48 px, for legacy browser support.
`png` is rendered as both a 180x180 PNG favicon fallback and the Apple touch icon.

```toml
[Params.Favicon]
  ico = "/favicon.ico"                     # Legacy multi-size .ico fallback
  svg = "/favicon.svg"                     # SVG icon for modern browsers
  png = "/favicon.png"                     # 180x180 PNG fallback and Apple touch icon
```

Place these files in the site's `static` directory:
`static/favicon.ico`, `static/favicon.svg`, and `static/favicon.png`.
For an SVG with shadows, filters, or transparent padding, render a large
PNG first, trim the transparent canvas, then resize and re-center the
result:

```sh
rsvg-convert -f png -w 2048 -h 2048 -o /tmp/favicon-2048.png static/favicon.svg

convert /tmp/favicon-2048.png -alpha set -trim +repage -resize 180x180 -background none -gravity center -extent 180x180 static/favicon.png

convert /tmp/favicon-2048.png -alpha set -trim +repage -resize 16x16 -background none -gravity center -extent 16x16 /tmp/favicon-16.png
convert /tmp/favicon-2048.png -alpha set -trim +repage -resize 32x32 -background none -gravity center -extent 32x32 /tmp/favicon-32.png
convert /tmp/favicon-2048.png -alpha set -trim +repage -resize 48x48 -background none -gravity center -extent 48x48 /tmp/favicon-48.png

convert /tmp/favicon-16.png /tmp/favicon-32.png /tmp/favicon-48.png static/favicon.ico

rm -f /tmp/favicon-2048.png /tmp/favicon-16.png /tmp/favicon-32.png /tmp/favicon-48.png
```

### Canonical URLs

HugoTeX renders a canonical link in the document head for every page. By
default it uses Hugo's `.Permalink`, derived from `baseURL` and the page
URL.

Set `relcanonical` in page front matter only when the page should declare
a different canonical URL, for example when the same content also exists
at another permanent address. The value is rendered without conversion,
so it must be a full absolute URL with scheme and host; do not use
relative paths.

```toml
+++
title = "A duplicated page"
relcanonical = "https://example.com/original-page/"
+++
```

### Social Media Integration

Enable rich previews on social platforms:

```toml
[Params]
  twittercard = true
  opengraph = true
```

See [Hugo's Internal Templates](https://gohugo.io/templates/internal/) for advanced configuration.

## 📐 Math Typesetting

HugoTeX uses [KaTeX](https://katex.org/) with **server-side rendering** for mathematical notation.

### Why Server-Side?

- ⚡ **Zero JavaScript overhead** - Math renders instantly, no client-side processing
- 📱 **Better mobile performance** - Especially on slower devices
- ♿ **Works without JavaScript** - Accessible by default
- 🚀 **Faster page loads** - No render blocking

### Usage

Simply write math expressions in your Markdown:

**Inline math:** `$E = mc^2$` → $E = mc^2$

**Display math:**
```markdown
$$
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
$$
```

Math is automatically processed using Hugo's built-in `transform.ToMath` function. The passthrough extension (shown in config above) enables this functionality.

**Reference:** [Hugo Math in Markdown](https://gohugo.io/content-management/mathematics/) | [KaTeX Supported Functions](https://katex.org/docs/supported.html)

## 🎨 Shortcodes

### Sidenotes

Create elegant margin notes with the sidenote shortcode:

```markdown
Here's some text with a sidenote.{{%/* sidenote */%}}This appears in the margin.{{%/* /sidenote */%}}
```

**Behavior:**
- **Desktop:** Displays in the right margin
- **Mobile:** Hidden by default, revealed by clicking the reference number

This feature is powered by [LaTeX.css](https://latex.vercel.app/).

## 🎨 Customization

### Syntax Highlighting

Change the code highlighting theme in your config:

```toml
[markup.highlight]
  style = "monokai"  # Try: github, dracula, nord, etc.
```

Browse available styles: [Chroma Style Gallery](https://xyproto.github.io/splash/docs/)

### Custom CSS

Add custom styles by creating `assets/css/custom.css` in your site directory.

## 🌟 Showcase

Using HugoTeX? We'd love to feature your site! Open an issue or PR to add it here.

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

- 🐛 **Report bugs** - Open an issue describing the problem
- ✨ **Suggest features** - Share your ideas for improvements
- 📝 **Improve documentation** - Help make the docs clearer
- 🔧 **Submit pull requests** - Fix bugs or add features

Before contributing:
1. Check existing issues and PRs
2. Test your changes thoroughly
3. Follow the existing code style
4. Update documentation as needed

## 📄 License

MIT License - see [LICENSE](LICENSE) for details

## 🙏 Credits

This theme is heavily inspired by:
- [LaTeX.css](https://latex.vercel.app/) - CSS library mimicking LaTeX style
- [latex-css](https://latex.now.sh/) - Original inspiration

## 📚 Similar Projects

Looking for alternatives? Check out:
- [hugo-theme-texify](https://github.com/queensferryme/hugo-theme-texify/) - Another excellent LaTeX-inspired theme

---

**Made with ❤️ by [Kaito Sugimoto](https://github.com/kaisugi)**

If you find HugoTeX useful, please consider giving it a ⭐ on GitHub!
