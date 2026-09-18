---
title: Hello World:本站的第一篇文章
description: 博客正式开张,记录搭建这个 Hugo 博客的过程与踩坑。
date: 2026-09-18
draft: false
tags:
  - Notes
categories:
  - Programming
---

欢迎来到我的博客!这是本站的第一篇文章。

## 为什么用 Hugo + Stack

这个网站使用 [Hugo](https://gohugo.io/) 静态站点生成器构建,搭配 [Stack](https://github.com/CaiJimmy/hugo-theme-stack) 主题,通过 GitHub Actions 自动部署到 GitHub Pages。

主要优点:

1. **构建速度快**:Hugo 是目前最快的静态站点生成器之一
2. **完全免费**:GitHub Pages 托管,无需服务器
3. **外观现代**:Stack 主题采用卡片式设计,支持深色模式

## 写作体验

```markdown
---
title: 文章标题
date: 2026-09-18
tags: [Notes]
categories: [Programming]
---

正文内容,支持标准 Markdown……
```

## 接下来

- 换上自己的头像(`assets/img/avatar.png`)
- 修改 `hugo.toml` 中的站点标题
- 把仓库推送到 GitHub 并启用 Pages

> "Abstractness is the price of generality."
