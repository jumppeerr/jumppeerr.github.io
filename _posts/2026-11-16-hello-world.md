---
layout: post
title: "博客开张：用 Jekyll + GitHub Pages 搭一个自己的站点"
date: 2026-11-16 20:00:00 +0800
categories: [教程]
tags: [jekyll, github-pages, 博客]
---

折腾博客这件事，大概是每个程序员的周期性冲动。这次不再折腾动态博客、不再买服务器，直接用一个静态站把内容写起来。

## 为什么选 Jekyll + GitHub Pages

| 方案 | 成本 | 维护 | 适合 |
| --- | --- | --- | --- |
| WordPress | 服务器 + 域名 | 要升级、要备份 | 内容多、要后台 |
| 静态站 + GitHub Pages | 0 元 | 几乎没有 | 写笔记、做作品集 |
| 自建 VPS | 每年几百 | 要运维 | 想完全掌控 |

对我的需求来说，答案很明确：**写文章比搭系统重要**。

## 整体结构

整个站点只有几个核心文件：

```text
github-blog/
├── _config.yml          # 站点配置（标题、主题、插件）
├── index.md             # 首页：自动列出所有文章
├── about.md             # 「关于」页
├── _posts/              # 所有文章，文件名必须是 日期-标题.md
├── _includes/           # 可复用的 HTML 片段
├── assets/css/          # 自定义样式
└── .github/workflows/   # 自动构建并部署
```

## 写一篇新文章

新建 `_posts/2026-11-20-my-post.md`，开头写 front matter：

```yaml
---
layout: post
title: "文章标题"
date: 2026-11-20 10:00:00 +0800
categories: [随笔]
tags: [tag1, tag2]
---
```

然后下面正常写 Markdown 就行。提交、推送，几十秒后线上就能看到。

## 一个重要的细节

Jekyll 会解析文章里的 Liquid 模板语法，所以如果你想在文章里展示双大括号的示例代码，需要用 Liquid 的 raw 标签把示例包起来，否则那段模板会被当成真实代码执行、渲染结果为空。

> 先把站点跑起来，再慢慢打磨。完美主义是博客最好的敌人。

下一篇见。
