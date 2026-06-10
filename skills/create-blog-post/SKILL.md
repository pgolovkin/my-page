---
name: create-blog-post
description: Create new blog posts for this repository's GitHub Pages Jekyll site. Use when Codex needs to add a dated article, blog entry, note, announcement, or post under docs/_posts/, choose a date and slug, write Jekyll post front matter, add Markdown content, handle optional tags or author metadata, and validate that the post appears through the existing site.posts listing.
---

# Create Blog Post

## Overview

Use this skill to add new dated blog posts to this repository's GitHub Pages site. The site is built from `docs/`, and posts belong in `docs/_posts/` using Jekyll's `YYYY-MM-DD-slug.md` naming convention.

## Post Creation Workflow

1. Read `docs/_layouts/post.html`, `docs/index.md`, `docs/_config.yml`, and at least one existing file in `docs/_posts/`.
2. Determine the post date. Use the date requested by the user; otherwise use the current date from the environment context.
3. Derive a short lowercase slug from the title or topic. Use ASCII letters, digits, and hyphens for the filename unless the user explicitly requests another URL.
4. Check that `docs/_posts/YYYY-MM-DD-slug.md` does not already exist.
5. Create the post with `layout: post`, `title`, and `date` front matter.
6. Add optional `tags` or `author` only when the user asks or the content clearly benefits from them.
7. Write the body in Markdown. Match the current site language unless the user asks otherwise; existing public content is Russian.
8. Validate that the file path, front matter, date, and home page listing behavior are correct.

## File Pattern

Use this baseline:

```markdown
---
layout: post
title: "Post title"
date: YYYY-MM-DD
---

# Post heading

Post body.
```

When using tags, prefer YAML list syntax:

```yaml
tags:
  - tag-one
  - tag-two
```

The active `post` layout displays `page.date`, `page.title`, optional `page.author`, the content, and optional `page.tags`.

## Date And Visibility

- Jekyll treats future-dated posts as unpublished by default on GitHub Pages. If the user requests a future date, explain that the post may not appear until that date unless future posts are enabled.
- The home page lists the latest five posts with `{% for post in site.posts limit:5 %}`. Do not manually edit that list for ordinary posts.
- If the user asks for a draft, use `docs/_drafts/` only after confirming or creating a draft workflow; this repo does not currently have `_drafts/`.

## Post Versus Page

Create a blog post when the user asks for a dated article, blog entry, note, announcement, or post. Blog posts belong in `docs/_posts/` and use `layout: post`.

Create a standalone page instead when the user asks for persistent sections such as "About", "Projects", "Contacts", "Resume", "Portfolio", or "Services". Standalone pages belong directly under `docs/` and use `layout: default`.

## Validation

At minimum, verify:

- The filename matches `docs/_posts/YYYY-MM-DD-slug.md`.
- The front matter is valid YAML and includes `layout: post`, `title`, and `date`.
- The body has useful Markdown content and does not duplicate the title awkwardly unless that matches the site style.
- The date is not unintentionally in the future.
- `docs/index.md` can discover the post through `site.posts`; no manual index edit is needed for normal posts.

If Ruby/Jekyll dependencies are available, run:

```bash
bundle exec jekyll build -s docs
```

If the local Jekyll environment is not installed, report that and rely on structural checks.
