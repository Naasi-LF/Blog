# Naasi 博客

基于 Hugo 和 PaperMod 主题构建的个人博客。

[English](README.md) | 简体中文

## 创建新文章

### 自动生成

1. 创建中文文章：
```bash
hugo new content/zh/posts/your-post-name.md
```

2. 创建英文文章：
```bash
hugo new content/en/posts/your-post-name.md
```

该命令会自动生成一个包含以下前置参数的 markdown 文件：
```yaml
---
title: "Your Post Name"
date: 2025-02-04T17:23:51+08:00  # 当前时间
draft: true
---
```

### 编辑前置参数

文件生成后，更新前置参数添加更多细节：
```yaml
---
title: "文章标题"
date: 2025-02-04T16:24:04+08:00
draft: false
description: "文章描述"
summary: "文章摘要，将显示在列表页面"
tags: ["标签1", "标签2"]
categories: ["分类1"]
---
```

## 示例文章

这是一个完整的文章示例：

```markdown
---
title: "我的第一篇博客"
date: 2025-02-04T17:00:00+08:00
draft: false
description: "这是我的第一篇博客文章"
summary: "在这篇文章中，我将介绍如何使用 Markdown 写作，以及如何在 Hugo 中创建漂亮的博客文章。"
tags: ["教程", "Markdown"]
categories: ["写作"]
---

## 介绍

欢迎来到我的博客！这是一篇示例文章，展示了 Markdown 的基本用法。

### 文本格式

你可以使用 **粗体**、*斜体* 或 ~~删除线~~ 来格式化文本。

### 代码块

```python
def hello_world():
    print("你好，世界！")
```

### 列表

1. 第一项
2. 第二项
   - 子项 1
   - 子项 2


## 本地预览

运行以下命令启动本地预览：
```bash
hugo server -D
```

访问 http://localhost:1313/naasiBlog/ 查看你的博客。

## 注意事项

1. 确保文章的 `draft: false` 才会被发布
2. 图片请放在 `static/images` 目录下
3. 可以使用 `<!--more-->` 来控制文章预览的截断位置
4. 中英文文章分别放在 `content/zh/posts` 和 `content/en/posts` 目录下
