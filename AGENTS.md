# AGENTS.md

This file describes the repository layout and provides guidance for AI coding agents working in this repo.

## Repository overview

This is a personal technical blog built with [Quarto](https://quarto.org/) and deployed to [GitHub Pages](https://georgwiese.github.io/).

## Directory layout

```
_quarto.yml          # Site configuration
index.qmd            # Homepage (blog listing)
about.qmd            # About page
posts/               # Blog posts — one subdirectory per post
  _metadata.yml      # Defaults applied to all posts
  test-post/
    index.qmd        # Example draft post
.github/
  workflows/
    deploy.yml       # CI: render and deploy to GitHub Pages
README.md            # Human-readable setup instructions
AGENTS.md            # This file
CLAUDE.md            # Symlink → AGENTS.md
.gitignore           # Ignores Quarto build artifacts
```

## Adding a new post

Create a new directory under `posts/` with an `index.qmd` file:

```bash
mkdir posts/my-new-post
cat > posts/my-new-post/index.qmd << 'EOF'
---
title: "My New Post"
date: 2025-06-01
categories: [category]
---

Post content here.
EOF
```

## Build commands

- **Preview locally:** `quarto preview`
- **Render site:** `quarto render`
- **Render single post:** `quarto render posts/my-new-post/index.qmd`

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which renders the site
and deploys it to GitHub Pages via the `actions/deploy-pages` action.
GitHub Pages must be configured to use the "GitHub Actions" source in the repository settings.

## giscus comments

Comments are powered by [giscus](https://giscus.app/). To finish setup:

1. Enable GitHub Discussions on the repository.
2. Go to <https://giscus.app/> and configure it for this repo.
3. Replace the four placeholder values in `_quarto.yml` under `website.comments.giscus`:
   - `REPLACE-WITH-GITHUB-REPO` → e.g., `georgwiese/georgwiese.github.io`
   - `REPLACE-WITH-REPO-ID` → the repo ID from giscus
   - `REPLACE-WITH-CATEGORY` → e.g., `Announcements`
   - `REPLACE-WITH-CATEGORY-ID` → the category ID from giscus

## Conventions

- Posts are Quarto Markdown (`.qmd`) files.
- Each post lives in its own subdirectory under `posts/` and is named `index.qmd`.
- Draft posts use `draft: true` in the front matter and are not rendered in production.
- Math is rendered with MathJax; use standard LaTeX syntax.
- Code blocks use triple backticks with language tags (e.g., ` ```rust `).
