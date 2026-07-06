# jespernwulff.github.io

Academic website for **Jesper N. Wulff**, Professor of Business Economics, Aarhus University.

Built with [Hugo](https://gohugo.io/) (extended) + [Hugo Blox](https://hugoblox.com/) (Tailwind) + [Pagefind](https://pagefind.app/), deployed to GitHub Pages via GitHub Actions.

- **Live site:** https://jespernwulff.github.io/
- **Editing guide:** see [`UPDATING.md`](UPDATING.md) — how to add a paper, a person, or edit the bio without touching the build system.
- **Architecture notes:** see [`WEBSITE_PRINCIPLES.md`](WEBSITE_PRINCIPLES.md).

## How it deploys

Every push to `main` triggers `.github/workflows/deploy.yml`, which installs Hugo + Node, runs `npm ci` (Tailwind CLI + Pagefind), builds the site, generates the search index, and publishes to GitHub Pages. You never build locally to publish — just edit Markdown and push (or edit on github.com).

## Local development (optional)

Requires Hugo extended and Node. From the repo root:

```bash
npm install
hugo server
```
