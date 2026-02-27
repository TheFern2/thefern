# How to Make a Project

## Create the File

Create a new `.md` file in `src/data/projects/`:

```bash
touch src/data/projects/my-project.md
```

## Frontmatter

Add this at the top of the file:

```yaml
---
title: "Project Name"
description: "What this project does in one sentence."
tech:
  - TypeScript
  - React
  - Node.js
github: "https://github.com/username/repo"
demo: "https://myproject.com"
image: "https://example.com/screenshot.png"
featured: true
pubDatetime: 2024-01-15T00:00:00Z
---
```

### Required Fields

| Field | Description |
|-------|-------------|
| `title` | Project name |
| `description` | One-line summary |
| `tech` | Array of technologies used |
| `pubDatetime` | Date (used for sorting) |

### Optional Fields

| Field | Description |
|-------|-------------|
| `github` | GitHub repository URL |
| `demo` | Live demo URL |
| `image` | Screenshot/preview image URL |
| `featured` | Show on homepage (default: `false`) |
| `draft` | Hide from site (default: `false`) |

## Content

Write project details below the frontmatter:

```markdown
---
title: "My Awesome Project"
description: "A CLI tool for automating deployments."
tech:
  - Rust
  - CLI
github: "https://github.com/me/project"
featured: true
pubDatetime: 2024-06-01T00:00:00Z
---

## Overview

Explain what the project does and why you built it.

## Features

- Feature one
- Feature two
- Feature three

## Technical Details

Describe architecture, challenges, or interesting decisions.

## What I Learned

Share insights from building this project.
```

## Images

For project images, you can:

1. **Use external URLs** - Hosted images (e.g., from your repo, Imgur, etc.)
2. **Use local images** - Place in `public/projects/` and reference as `/projects/image.png`

## Preview

```bash
npm run dev
```

- Project list: `http://localhost:4321/projects`
- Project detail: `http://localhost:4321/projects/my-project`
