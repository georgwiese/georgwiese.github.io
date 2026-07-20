# georgwiese.github.io

Personal technical blog built with [Quarto](https://quarto.org/) and hosted on [GitHub Pages](https://georgwiese.github.io/).

## Installing Quarto

Download and install Quarto from <https://quarto.org/docs/get-started/>.

On macOS with Homebrew:

```bash
brew install --cask quarto
```

Verify the installation:

```bash
quarto --version
```

## Previewing the site locally

```bash
quarto preview
```

This starts a local development server with live reload at <http://localhost:4848>.

## Creating a new post

1. Create a new directory under `posts/` with an `index.qmd` file:

```bash
mkdir posts/my-new-post
```

2. Add front matter and content to `posts/my-new-post/index.qmd`:

```markdown
---
title: "My New Post"
date: 2025-06-01
---

Post content here.
```

3. Use `draft: true` in the front matter while the post is in progress. Remove it when ready to publish.

## Deployment

Pushing to the `main` branch automatically triggers the GitHub Actions workflow at `.github/workflows/deploy.yml`.  
The workflow:
1. Installs Quarto.
2. Renders the site with `quarto render`.
3. Deploys the `_site/` output to GitHub Pages using `actions/deploy-pages`.

**Required one-time setup:** In the repository settings, go to **Pages → Source** and select **GitHub Actions**.

## Finishing giscus setup

Post comments are powered by [giscus](https://giscus.app/). To activate them:

1. Enable **GitHub Discussions** on the repository (Settings → Features → Discussions).
2. Visit <https://giscus.app/> and fill in the repository name to obtain the IDs.
3. Edit `_quarto.yml` and replace the four placeholder values under `website.comments.giscus`:

| Placeholder | Replace with |
|---|---|
| `REPLACE-WITH-GITHUB-REPO` | `georgwiese/georgwiese.github.io` |
| `REPLACE-WITH-REPO-ID` | repo ID from giscus |
| `REPLACE-WITH-CATEGORY` | discussion category name |
| `REPLACE-WITH-CATEGORY-ID` | discussion category ID from giscus |
