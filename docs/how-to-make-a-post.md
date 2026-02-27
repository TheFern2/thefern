# How to Make a Post

## Create the File

Create a new `.md` file in `src/data/blog/`:

```bash
touch src/data/blog/my-new-post.md
```

## Frontmatter

Add this at the top of the file:

```yaml
---
title: "Your Post Title"
description: "A brief description of your post."
pubDatetime: 2024-01-15T00:00:00Z
tags:
  - tag1
  - tag2
featured: false
draft: false
---
```

### Required Fields

| Field | Description |
|-------|-------------|
| `title` | Post title |
| `description` | Short summary (used in cards and SEO) |
| `pubDatetime` | Publication date (ISO format) |
| `tags` | Array of tags |

### Optional Fields

| Field | Default | Description |
|-------|---------|-------------|
| `featured` | `false` | Show in featured section on homepage |
| `draft` | `false` | If `true`, post won't be published |
| `author` | Site author | Override default author |
| `ogImage` | Auto-generated | Custom Open Graph image |
| `modDatetime` | - | Last modified date |

## Content

Write your content below the frontmatter using Markdown:

```markdown
---
title: "My Post"
description: "About something cool"
pubDatetime: 2024-01-15T00:00:00Z
tags:
  - tutorial
---

## Introduction

Your content here...

## Code Examples

```python
print("Hello, world!")
```

## Images

![Alt text](/path/to/image.png)
```

## Preview

Run the dev server to preview:

```bash
npm run dev
```

Visit `http://localhost:4321/posts/my-new-post`
