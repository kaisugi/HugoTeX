---
author: Hugo Authors
title: Math Typesetting
date: 2019-03-08
description: A brief guide to setup KaTeX
math: true
---

Mathematical notation in a Hugo project can be enabled by using third party JavaScript libraries.
<!--more-->

In this example we will be using [MathJax](https://www.mathjax.org/)

- To enable MathJax globally set the parameter `math` to `true` in a project's configuration
- To enable MathJax on a per page basis include the parameter `math: true` in content files

**Note:** Use the online reference of [Supported TeX Functions](https://docs.mathjax.org/en/v4.0/input/tex/macros/index.html#supported-tex-latex-commands)

### Examples

Inline math: $\varphi = \dfrac{1+\sqrt5}{2}= 1.6180339887...$

Block math:
$$
 \varphi = 1+\frac{1} {1+\frac{1} {1+\frac{1} {1+\cdots} } }
$$
