---
layout: post
title: "Git 日常操作清单：从提交到回滚"
date: 2026-11-08 15:10:00 +0800
categories: [工具]
tags: [git, 效率]
---

把每天真正会用到的 Git 命令按场景整理一遍，比背文档有用。

## 日常三板斧

```bash
git status            # 我改了什么
git add -p            # 逐块挑选要提交的改动
git commit -m "feat: 支持深色模式"
```

`git add -p` 是被严重低估的命令。它让你把一个文件里不相关的改动拆成多个语义清晰的提交。

## 分支操作

```bash
git switch -c feat/login    # 新建并切换分支
git switch main             # 回到 main
git branch -d feat/login    # 删除已合并分支
git fetch --prune           # 清理远端已删除的分支
```

## 撤销的三种场景

### 1. 改错了，还没 add

```bash
git restore path/to/file
```

### 2. 已经 add，还没 commit

```bash
git restore --staged path/to/file
```

### 3. 已经 commit，但还没 push

```bash
git commit --amend          # 改提交信息或补充文件
git reset --soft HEAD~1     # 撤销提交，保留改动
```

> 已经 push 到共享分支的历史不要随便改写，用 `git revert` 更安全。

## 找回丢失的提交

`git reflog` 记录了 HEAD 的每一次移动：

```bash
git reflog
git reset --hard HEAD@{2}
```

误删分支、误 reset 之后，这通常是最快的救命手段。

## 提交信息约定

用 Conventional Commits 风格，一眼就能看出改了什么：

| 前缀 | 含义 |
| --- | --- |
| feat | 新功能 |
| fix | 修 bug |
| docs | 文档 |
| refactor | 重构 |
| chore | 杂项 |

## 配置一次，长期受益

```bash
git config --global user.name "jumppeerr"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
git config --global pull.rebase true
```

---

工具的价值在于让你忘记它的存在。命令练到不用查，注意力才能回到真正的问题上。
