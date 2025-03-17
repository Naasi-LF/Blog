# Naasi Blog

A personal blog built with Hugo and PaperMod theme.

English | [简体中文](README_zh.md)

## Create New Post

### Automatic Creation

1. For English posts:
```bash
hugo new content/en/posts/your-post-name.md
```

2. For Chinese posts:
```bash
hugo new content/zh/posts/your-post-name.md
```

The command will automatically generate a markdown file with the following front matter:
```yaml
---
title: "Your Post Name"
date: 2025-02-04T17:23:51+08:00  # Current time
draft: true
---
```

### Edit the Front Matter

After the file is generated, update the front matter with more details:
```yaml
---
title: "Post Title"
date: 2025-02-04T16:24:04+08:00
draft: false
description: "Post description"
summary: "Post summary that will be shown in the list view"
tags: ["tag1", "tag2"]
categories: ["category1"]
---
```

## Example Post

Here's a complete example post:

```markdown
---
title: "My First Blog Post"
date: 2025-02-04T17:00:00+08:00
draft: false
description: "This is my first blog post"
summary: "In this post, I'll introduce how to write with Markdown and create beautiful blog posts in Hugo."
tags: ["Tutorial", "Markdown"]
categories: ["Writing"]
---

## Introduction

Welcome to my blog! This is an example post showing basic Markdown usage.

### Text Formatting

You can format text using **bold**, *italic*, or ~~strikethrough~~.

### Code Blocks

```python
def hello_world():
    print("Hello, World!")
```

### Lists

1. First item
2. Second item
   - Sub-item 1
   - Sub-item 2


## Local Preview

Run the following command to start local preview:
```bash
hugo server -D
```

Visit http://localhost:1313/naasiBlog/ to view your blog.

## Notes

1. Make sure `draft: false` for posts to be published
2. Place images in the `static/images` directory
3. Use `<!--more-->` to control where the post preview cuts off
4. Put English posts in `content/en/posts` and Chinese posts in `content/zh/posts`
