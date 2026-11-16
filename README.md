# Jumppeerr 的博客

基于 **Jekyll + Minima 主题**的静态博客，托管在 GitHub Pages，推送到 `main` 分支后由 GitHub Actions 自动构建并发布。

线上地址：<https://jumppeerr.github.io>

## 目录结构

```text
.
├── _config.yml              # 站点配置（标题、描述、主题、插件）
├── index.md                 # 首页，自动列出 _posts 里的文章
├── about.md                 # 「关于」页面
├── 404.html                 # 404 页面
├── _posts/                  # 所有文章
│   ├── 2026-11-08-git-cheatsheet.md
│   ├── 2026-11-12-markdown-cheatsheet.md
│   └── 2026-11-16-hello-world.md
├── _includes/
│   └── custom-head.html     # 往 <head> 里追加内容（引入自定义样式）
├── assets/css/custom.css    # 自定义样式，叠加在 Minima 之上
└── .github/workflows/pages.yml  # 构建 + 部署工作流
```

## 写一篇新文章

1. 在 `_posts/` 下新建文件，文件名必须是 `YYYY-MM-DD-英文标题.md`，例如 `2026-11-20-my-first-post.md`。
2. 文件开头写 front matter：

```yaml
---
layout: post
title: "文章标题"
date: 2026-11-20 10:00:00 +0800
categories: [随笔]
tags: [标签一, 标签二]
---
```

3. 下面正常写 Markdown。
4. 提交并推送，Actions 构建完成后几十秒内上线。

> 注意：文章正文里的 `{{ }}` 和 `{% %}` 会被 Jekyll 当作 Liquid 模板执行。
> 要展示这类代码，请用 `{% raw %}` 与 `{% endraw %}` 把示例包起来。

## 本地预览（可选）

需要 Ruby 3.x：

```bash
gem install bundler
bundle install
bundle exec jekyll serve
# 打开 http://127.0.0.1:4000
```

如果本地没有 Ruby，也可以只推送，让 GitHub Actions 构建（本项目默认走这条路径）。

## 修改站点信息

编辑 `_config.yml`：

| 字段 | 说明 |
| --- | --- |
| `title` | 顶部显示的博客名 |
| `description` | 站点描述（SEO / 页脚） |
| `author` | 作者名 |
| `url` / `baseurl` | 站点地址；用户站点 `baseurl` 留空 |
| `minima.skin` | 换肤：`classic`、`dark`、`solarized`、`solarized-dark` |
| `header_pages` | 顶部导航要显示的页面 |

颜色、卡片、代码块等视觉细节在 `assets/css/custom.css` 里。

## 部署配置说明（已完成）

- 仓库：`jumppeerr.github.io`（用户站点，必须与用户名同名）
- Pages 源：**GitHub Actions**（`build_type: workflow`）
- 工作流：`.github/workflows/pages.yml`，push 到 `main` 即触发
- 如果以后换成项目站点（仓库名不是 `用户名.github.io`），把 `_config.yml` 里的 `baseurl` 改成 `"/仓库名"`，并把 `url` 改成 `https://用户名.github.io`

## 绑定自定义域名

1. 在仓库根目录新建 `CNAME` 文件，内容为你的域名，例如 `blog.example.com`。
2. 在域名服务商添加 CNAME 记录，指向 `jumppeerr.github.io`。
3. 在仓库 Settings → Pages 里勾选 Enforce HTTPS。

## 许可

文章内容版权归作者所有，站点模板代码可自由使用。
