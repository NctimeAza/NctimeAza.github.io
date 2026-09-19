# My Blog (Hugo + Theme Stack)

一个从零搭建、外观仿照 [sdl.moe](https://sdl.moe/) 的个人博客:使用 **Hugo** 静态站点生成器 + **Theme Stack** 卡片式主题(与 sdl.moe 同款主题),托管在 **GitHub Pages** 上,由 GitHub Actions 自动构建部署。

## 目录结构

```
├── .github/workflows/hugo.yml   # GitHub Actions 自动部署 workflow
├── hugo.toml                    # 站点主配置(菜单、widgets、侧边栏、配色)
├── assets/img/avatar.jpg        # 头像(替换成你自己的)
├── archetypes/                  # 新文章模板
├── content/
│   ├── _index.md                # 首页(菜单:首页)
│   ├── post/                     # 博文(卡片列表展示)
│   │   └── hello-world.md       # 示例文章
│   └── page/                     # 独立页面
│       ├── about/index.md       # 关于(菜单:关于)
│       ├── archives/index.md    # 归档(菜单:归档)
│       ├── search/index.md      # 搜索(菜单:搜索)
│       └── links/index.md      # 友链(菜单:友链)
└── themes/stack/                 # Stack 主题(已内置,无需再下载)
```

## 本地预览

需要安装 [Hugo (extended 版, ≥ 0.157)](https://github.com/gohugoio/hugo/releases):

```bash
hugo server -D
# 打开 http://localhost:1313/
```

## 写新文章

```bash
hugo new content post/my-first-post.md
```

编辑生成的 Markdown 文件(front matter 含标题/日期/标签/分类),保存后本地服务会自动热刷新。

## 部署到 GitHub Pages

1. 在 GitHub 新建仓库(例如 `blog`),把本项目推上去:

   ```bash
   git remote add origin https://github.com/<你的用户名>/<仓库名>.git
   git push -u origin main
   ```

2. 仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**。
3. 推送到 `main` 分支即可自动构建并发布;Actions 里可查看部署进度。

发布地址为 `https://<你的用户名>.github.io/<仓库名>/`。若要用 `username.github.io` 根路径,新建名为 `<你的用户名>.github.io` 的仓库再推送即可,无需改配置(workflow 会自动获取正确的 baseURL)。

## 个性化(仿 sdl.moe 的配置已就位)

| 想改什么 | 改哪里 |
|---|---|
| 站点标题 | `hugo.toml` 的 `title` |
| 副标题(现同 sdl.moe: "Abstractness is the price of generality") | `hugo.toml` 的 `[params.sidebar].subtitle` |
| 头像 | 覆盖 `assets/img/avatar.jpg` |
| 侧边栏菜单(首页/关于/归档/搜索/友链) | 各页面 front matter 的 `menu.main` |
| 右侧栏小工具(搜索/归档/标签云) | `hugo.toml` 的 `[params.widgets]` |
| 默认配色(当前 auto,首访跟随系统;可在左下角切换明暗) | `hugo.toml` 的 `[params.colorScheme].default` |
| 社交图标(现占位 GitHub) | `hugo.toml` 的 `[[menu.social]]` |
| 页脚起始年份 | `hugo.toml` 的 `[params.footer].since` |

已同步 sdl.moe 的布局:三栏结构(左侧菜单栏 / 中间文章卡片流 / 右侧 widgets)、卡片 10px 圆角、暗色背景 `rgb(48,48,48)`、文章列表含分类标签与阅读时长、归档页按年分组、搜索页(含 JSON 索引)。

## 常用命令

```bash
hugo new content post/xxx.md   # 新文章
hugo server -D                 # 本地预览(含草稿)
hugo --gc --minify -d public   # 手动构建(部署由 CI 完成,一般用不到)
```

> 备注:评论系统(Stack 支持 giscus/waline 等)当前关闭,需要时在 `hugo.toml` 的 `[params.comments]` 里开启并填入 provider 参数。
