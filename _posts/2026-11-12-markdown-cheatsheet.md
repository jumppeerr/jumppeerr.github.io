---
layout: post
title: "Markdown 速查：写博客用得上的那些语法"
date: 2026-11-12 09:30:00 +0800
categories: [笔记]
tags: [markdown, 写作]
---

写静态博客绕不开 Markdown。这篇把真正高频的语法整理成一页速查，复制粘贴即可。

## 标题与强调

```markdown
# 一级标题
## 二级标题

**加粗**  *斜体*  ~~删除线~~  `行内代码`
```

## 列表

```markdown
- 无序项
  - 嵌套项
- 无序项

1. 有序项
2. 有序项
```

## 链接与图片

```markdown
[链接文字](https://jekyllrb.com)
![图片说明](/assets/images/pic.png)
```

站内链接建议用 `relative_url`，这样以后换域名也不怕：

```liquid
{% raw %}
[关于页]({{ '/about/' | relative_url }})
{% endraw %}
```

## 引用与代码块

````markdown
> 一段引用

```python
print("hello")
```
````

带语言标记的代码块会有高亮，常用的有 `python`、`js`、`bash`、`yaml`、`sql`。
如果代码块里本身要出现三反引号，就把外层围栏改成四个反引号。

## 表格

```markdown
| 名称 | 说明 |
| --- | --- |
| Jekyll | 静态站点生成器 |
| Minima | 默认主题 |
```

## 分隔线

```markdown
---
```

三个短横线前后要留空行，否则会被当成 front matter。

## 常用 HTML 兜底

Markdown 表达不了的时候，直接写 HTML：

```html
<details>
  <summary>点击展开</summary>
  隐藏的内容
</details>
```

这类折叠块很适合放长命令、长日志。

---

记住常用的 20% 就够覆盖 80% 的写作需求了。
