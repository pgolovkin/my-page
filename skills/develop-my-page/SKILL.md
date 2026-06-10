---
name: develop-my-page
description: Develop and maintain this repository's GitHub Pages site built with Jekyll from the docs/ folder. Use when Codex needs to edit the personal site, add or update blog posts, change Jekyll layouts or Liquid templates, adjust _config.yml, preserve the custom domain setup, validate pages locally, or prepare GitHub Pages-compatible changes for this repo.
---

# Develop My Page

## Overview

Use this skill to make focused changes to this repository's personal GitHub Pages site. Treat `docs/` as the published site source and keep changes compatible with GitHub Pages' built-in Jekyll build.

## Repository Map

- `docs/_config.yml`: Jekyll site metadata. Current site title and description are in Russian.
- `docs/index.md`: home page using the `default` layout and listing the five latest posts.
- `docs/_layouts/default.html`: base layout, SEO include, theme stylesheet, header, and content wrapper.
- `docs/_layouts/post.html`: post layout with date, title, author fallback, content, and tags.
- `docs/_posts/`: blog posts named `YYYY-MM-DD-slug.md`.
- `docs/CNAME` and root `CNAME`: custom domain files. Keep both unless the user explicitly changes domain handling.

## Workflow

1. Read the relevant existing file before editing. For visual or layout changes, read both the Markdown page and the active layout.
2. Keep edits scoped to the requested page, post, layout, or config key. Do not refactor the theme unless it is required for the request.
3. Preserve Jekyll front matter exactly where needed: pages and posts must start with `---`.
4. Prefer Markdown content for posts and pages; use Liquid only for site data or post loops.
5. Validate with the lightest useful check available, then report what ran and any gaps.

## Content Conventions

- Match the existing site's language unless the user asks otherwise. The current site content is Russian.
- For a new post, create `docs/_posts/YYYY-MM-DD-short-slug.md` with:

```markdown
---
layout: post
title: "Post title"
date: YYYY-MM-DD
---

Post body.
```

- Add optional `tags:` only when useful. The post layout already renders tags when present.
- Avoid committing generated `_site/` output unless the repository already starts tracking it.
- Keep links GitHub Pages-safe. Prefer relative links or Liquid URL filters when editing layouts.

## Layout And Styling

- The site currently uses `jekyll-theme-minimal` and the theme stylesheet through `assets/css/style.css` with `relative_url`.
- When changing layout HTML, preserve `{% seo %}`, `{% include head-custom.html %}`, and existing URL filters unless there is a concrete reason to change them.
- Keep Liquid syntax valid. Watch for nested quotes in expressions such as `{{ "/" | absolute_url }}`.
- If custom CSS is needed, prefer adding a small `docs/assets/css/style.scss` or theme-compatible asset only after checking whether GitHub Pages will build it.

## Validation

Use what is available in the repo or environment:

- If Ruby/Jekyll dependencies exist locally, run a local Jekyll build or serve command from the repo root, such as `bundle exec jekyll build -s docs`.
- If no Ruby setup exists, run structural checks instead: verify file paths, front matter, Liquid syntax by inspection, and links touched by the change.
- For frontend-visible changes, preview locally when practical and inspect the page in the browser.

## GitHub Pages Constraints

- Keep dependencies and plugins compatible with GitHub Pages. Do not introduce unsupported Jekyll plugins without explaining the deployment impact.
- Keep the published source under `docs/`, matching the current repository structure.
- Preserve custom domain files unless the user requests a domain change.
