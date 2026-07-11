# AGENTS.md

Guidance for AI agents working in this repository.

## Project overview

Personal site for Ryan Shaffer ([ryanshaffer.net](https://www.ryanshaffer.net)), deployed via **GitHub Pages** from the `main` branch. The site is a **Jekyll** static blog built on the **Minimal Mistakes** remote theme.

Primary content types:

- Static pages in `_pages/` (About, Publications, Teaching, archives)
- Blog posts in `_posts/`
- Site-wide settings in `_config.yml`
- Navigation in `_data/navigation.yml`

## Tech stack

| Component | Details |
|-----------|---------|
| Generator | Jekyll via `github-pages` gem |
| Theme | `mmistakes/minimal-mistakes` (remote theme) |
| Skin | `air` |
| Markdown | Kramdown |
| Custom domain | `www.ryanshaffer.net` (`CNAME`) |

Do not vendor or fork the theme into this repo. Override theme files only when necessary, using Jekyll's override paths (`_includes/`, `_layouts/`, etc.).

## Local development

```bash
bundle install
bundle exec jekyll serve
```

- Restart the server after changing `_config.yml`.
- Built output goes to `_site/` (gitignored). Do not edit `_site/` directly.
- On Windows, the Gemfile includes `wdm` for file-watcher support.

Verify changes in the browser at `http://localhost:4000` before pushing.

## Repository layout

```
_config.yml              # Site settings, author, post defaults
_data/navigation.yml     # Top navigation links
_pages/                  # Static pages (included via _config.yml)
_posts/                  # Blog posts (YYYY-MM-DD-slug.md)
_includes/               # Theme overrides (head, favicons)
images/                  # Site images (portrait, headers, post figures)
papers/                  # PDF copies of select publications
index.html               # Home page front matter
CNAME                    # Custom domain for GitHub Pages
```

## Content conventions

### Blog posts (`_posts/`)

- Filename format: `YYYY-MM-DD-slug.md`
- Use YAML front matter. Common fields:

```yaml
---
title: "Post title"
date: 2019-07-07T18:38:30-05:00   # include for original posts; link posts may omit
categories:
  - Blog
tags:
  - quantum computing
link: https://example.com/external-article   # optional; for link/summary posts
---
```

- **Original posts**: Long-form markdown with images, headings, and inline HTML as needed. Reference images as `/images/filename.jpg`.
- **Link posts**: Short summary with a `link:` field pointing to the external source (paper, AWS blog, etc.). Minimal Mistakes renders these as link posts.
- Posts default to `layout: single` with author profile, date, share, and related posts (see `_config.yml` defaults).

### Static pages (`_pages/`)

- Each page needs `permalink:` and `title:` in front matter.
- Use `layout: single` unless a different layout is intentional.
- Keep tables and formatting consistent with existing pages (see `_pages/about.md`).

### Navigation (`_data/navigation.yml`)

- Only add nav items that have corresponding pages.
- Teaching, Categories, Tags, and CV links are intentionally commented out; uncomment only when those pages are ready.

### Publications (`_pages/publications.md`)

- Curated list with title, description, authors, and publication venue.
- Link to arXiv/journal pages and optional local PDFs in `papers/`.
- Google Scholar is the canonical full list; this page is a selected subset.

## Configuration notes

- `url` in `_config.yml` is `https://ryanshaffer.net`; `CNAME` is `www.ryanshaffer.net`. Do not change these without coordinating DNS.
- `search: false` — site search is disabled. Do not enable without configuring a search provider.
- `comments: true` in post defaults, but no comment provider (Disqus, Giscus, etc.) is configured. Comments will not render until a provider is added.
- Google Analytics is in `_includes/head.html` (`G-GP9ZQ8V3GL`). Preserve it unless explicitly asked to remove.

## Theme customization

Existing overrides:

- `_includes/head.html` — page title format, Google Analytics, main CSS
- `_includes/head/custom.html` — favicon and web manifest links
- `index.html` — home layout with header image (`/images/talk-header.jpg`)

When customizing:

1. Prefer `_config.yml` and front matter over template overrides.
2. Override theme files in `_includes/` or `_layouts/` only when the theme does not expose a config option.
3. Match existing style: minimal diffs, no unrelated refactors.

## Images and assets

- Store images in `images/`.
- Reference with absolute site paths: `/images/filename.jpg` (not relative paths).
- Favicon files live at repo root (`favicon.svg`, `favicon.ico`, etc.).
- Add new post images to `images/` and commit them with the post.

## Deployment

- No CI/CD workflow. Pushing to `main` triggers GitHub Pages build.
- GitHub Pages uses the `github-pages` gem dependency set; avoid adding Jekyll plugins not supported by GitHub Pages.
- Do not commit `_site/`, `.sass-cache/`, or `.jekyll-metadata/`.

## Agent workflow

1. **Read before editing** — Check neighboring posts/pages for front matter and formatting patterns.
2. **Minimize scope** — One post, one page, or one config change per task unless asked otherwise.
3. **Do not commit unless asked** — The repo owner controls git operations.
4. **Do not push** unless explicitly requested.
5. **Test locally** when possible: `bundle exec jekyll build` or `bundle exec jekyll serve`.
6. **Preserve voice** — Blog content is technical but accessible, focused on quantum computing, verification, and industry perspective.

## Common tasks

| Task | Where to edit |
|------|---------------|
| New blog post | `_posts/YYYY-MM-DD-slug.md` |
| Update bio/CV | `_pages/about.md`, `_config.yml` (`author:`) |
| Add publication | `_pages/publications.md`, optionally `papers/` |
| Change nav | `_data/navigation.yml` |
| Site title/description | `_config.yml` |
| Home page header | `index.html` front matter |
| Favicon/meta | `_includes/head/custom.html`, root favicon files |

## Avoid

- Editing generated `_site/` output
- Adding heavy JS frameworks or build pipelines
- Enabling unsupported Jekyll plugins
- Large unrelated theme refactors
- Committing secrets, analytics changes, or domain config without confirmation
- Creating empty placeholder pages and enabling them in navigation
