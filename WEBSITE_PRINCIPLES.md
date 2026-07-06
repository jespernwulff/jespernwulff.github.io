# Website architecture & principles

Playbook for future (AI-assisted) maintenance of this site. Built to the spec at
<https://gking.harvard.edu/mysite/files/ACADEMIC_SITE_PROMPT.md>. Read this before making structural changes.

## Stack

| Layer | Choice |
|-------|--------|
| Static site generator | **Hugo extended** (built/tested on 0.163.3) |
| Theme | **Hugo Blox** `blox-tailwind` (Go module, vendored in `_vendor/`) |
| CSS | Tailwind v4 (via the theme) + `assets/css/custom.css` for all project styling |
| Search | **Pagefind** (WASM, built in CI, indexed from the HTML) |
| Hosting | **GitHub Pages** user site at https://jespernwulff.github.io/ (repo `jespernwulff.github.io`) |
| CI | GitHub Actions (`.github/workflows/deploy.yml`) |

The Hugo site **is the repository root** (not a `hugo-site/` subfolder), which is why the deploy
workflow runs `hugo` with no `working-directory`.

## Build toolchain gotchas (learned the hard way)

- **Tailwind needs Node.** As of Hugo 0.161, `css.TailwindCSS` requires the npm package
  `@tailwindcss/cli` (a Node script) — the standalone Tailwind binary is rejected. So the CI
  workflow **must** `setup-node` + `npm ci` before `hugo`. `package.json` pins `@tailwindcss/cli`,
  `@tailwindcss/typography`, `tailwindcss`, and `pagefind`. (The original spec's `deploy.yml`
  omitted Node/Tailwind — this repo's version adds them.)
- `blox-tailwind` requires **Hugo ≥ 0.148.2 extended**. `hugo.yaml`'s CI `HUGO_VERSION` must match.
- `build.buildStats.enable: true` in `hugo.yaml` emits `hugo_stats.json` so Tailwind sees the
  classes used in templates.
- `_vendor/` is committed, so CI does **not** need Go. `go.sum` is committed alongside `go.mod`.
- Windows dev only: the Go module cache and `node_modules` must live at a **short path**
  (Windows `MAX_PATH` 260-char limit), and `git config core.longpaths true` is needed.

## Layout override strategy

We keep Blox's `site_head` (it runs the deferred Tailwind compile, SEO, favicon from
`assets/media/icon.png`, and auto-loads `assets/css/custom.css`) and override only what we control:

- `layouts/baseof.html` — thin shell: keeps `site_head`, adds a skip-link and `<main>`.
- `layouts/index.html` — homepage (photo-left hero + research-area accordions). **Do not** set
  `type: landing` on `content/_index.md` — that makes Hugo pick the theme's landing template instead.
- `layouts/publication/{list,single}.html` — the filterable Writings page and paper pages.
- `layouts/software/{list,single}.html`, `layouts/authors/list.html` (People), `layouts/_default/{list,single}.html`.
- `layouts/_partials/`: `components/headers/navbar.html`, `components/search-modal.html` (Pagefind,
  `relURL`-fixed import), `site_footer.html`, `related_finder.html`, `authors.html`, `breadcrumbs.html`,
  `bibtex_entry.html`, `social-icon.html`, `initials.html`, and `hooks/head-end/mysite.html`
  (discovery metadata + homepage Person JSON-LD).
- `layouts/shortcodes/staticrel.html` — sub-path-safe URLs (`{{< staticrel "files/x.pdf" >}}`).

## Content model

- Sections: `publication/`, `software/`, `bio/`, `teaching/`, `contact/`, `authors/`. Each item is a
  leaf bundle whose **folder name is its permanent slug** (`permalinks` use `:contentbasename`).
- `content/publication/` is generated from a single source list — see the generator note below.
- Research areas live in `data/research_areas.json`; each publication tags itself with `areas:`.
  The homepage accordions and the Writings research-area filter both read this.

## Automatic "See also" (`related_finder.html`)

Runs at build time on every publication/software page. Priority: explicit `related_*`/`see_also`/
`dataverse_url` overrides → shared research `area` → scored backfill (title-token +2, shared
non-owner author +1, shared tag +2; threshold 4, relaxed to 2 when there are <3 explicit picks).
Caps at 8, dedupes by normalized title, labels each `[Paper]`/`[Book]`/`[Software]`/`[Dataset]`.
No script, no stale data file — it recomputes on every build.

## Sub-path safety (the #1 source of 404s)

The site now lives at the domain root, but keep sub-path discipline anyway (it costs nothing
and survives any future move). Never hard-code `/foo`. In templates use
`relURL "foo"` (no leading slash); in Markdown use the `staticrel` shortcode or `url_pdf: files/...`
(no leading slash). The Pagefind import in the search modal is `relURL`-wrapped.

## Co-author links

Citation author names link to each person's external page via `data/coauthors.json`. The links
were auto-resolved by web search and **must be reviewed** — see `UPDATING.md`.

## Homepage research areas

`data/research_areas.json` defines two groups (Methods / Applications), each with subareas that
carry an explicit, ordered `papers` slug list. The homepage renders exactly those lists (Gary
King-style entries: title, award ribbon, authors, italic venue + year, and small
Abstract/Article/Full text/PDF/Code buttons from front matter). The Writings-page area filter
uses the same subarea ids via each paper's `areas:` front matter.

## Deliberate deviations from the base spec

- Repo root is the Hugo site (not `hugo-site/`), matching the provided deploy workflow.
- **No People page** — removed at the owner's request (the spec's default includes one).
  Co-author names still link out from citations via `data/coauthors.json`.
- No `talk/` section — the owner's talks are workshops/short courses, listed on the Teaching page.
- The Writings page orders working papers / under review / R&R first, then published work by
  year (matching gking.harvard.edu/publication); the "Newest first" sort preserves that grouping.
- CI installs Node + the Tailwind npm CLI (the spec's deploy.yml predates Hugo's Tailwind change).

## Local preview

```bash
npm install
hugo server            # or, to mirror production exactly:
hugo --gc --minify && npx pagefind --site public && (cd public && python -m http.server 8787)
```
Search only works against a Pagefind-indexed `public/` build, not `hugo server`.
