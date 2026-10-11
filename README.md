# timelessslatehen.org

This repository contains the source for [timelessslatehen.org](https://timelessslatehen.org), a static site built with [Quartz](https://quartz.jzhao.xyz/) and published with GitHub Pages.

## Repository layout

- [`quartz/content/`](./quartz/content/) — Markdown notes and other source content for the site. The home page is `index.md`.
- [`quartz/quartz.config.yaml`](./quartz/quartz.config.yaml) — site identity, URL, theme, plugins, and layout settings.
- [`quartz/`](./quartz/) — Quartz source, dependencies, and build configuration.
- [`.github/workflows/deploy-quartz.yml`](./.github/workflows/deploy-quartz.yml) — builds and deploys the site to GitHub Pages.

## Writing content

Add or edit Markdown files under `quartz/content/`. Quartz supports standard Markdown, GitHub Flavored Markdown, and Obsidian-style links and formatting. A note can include frontmatter such as:

```md
---
title: Example title
description: A short summary for previews
tags:
  - example
---

Write your note here.
```

Use `draft: true` in frontmatter to keep a draft out of the generated site. Content in this repository is part of its Git history, so do not add passwords, credentials, or material that must remain confidential.

## Local development

Requirements: Node.js 22 or newer and npm 10.9.2 or newer.

```sh
cd quartz
npm ci
npm run quartz -- build --serve
```

Open the local URL printed by Quartz (port 8080 by default). The development server watches for changes and rebuilds the site. Stop it with `Ctrl+C`.

To create a production build without starting the server:

```sh
npm run quartz -- build --output public
```

The generated `quartz/public/` directory is build output; make content and configuration changes in the source files instead.

## Deployment

Push changes to `main` to publish them. The GitHub Actions workflow runs when files under `quartz/` or the deployment workflow itself change, and can also be started manually from the repository's **Actions** tab. It installs the locked npm dependencies, builds Quartz, and deploys the generated site to GitHub Pages.

GitHub Pages should be configured to use **GitHub Actions** as its build and deployment source. The site domain is set in `quartz/quartz.config.yaml`; update it there if the domain changes.
