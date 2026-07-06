# Updating your website

This site is plain Markdown + a little configuration. You never have to run anything: **edit a file on GitHub, commit, and the site rebuilds and redeploys itself in ~2 minutes** (via GitHub Actions). If you prefer, you can edit locally and `git push`.

The live site is: **https://jespernwulff.github.io/**

---

## The 30-second mental model

- Every **publication** is a folder in `content/publication/`, containing one file called `index.md`.
- The **folder name is the permanent web address** (e.g. `content/publication/itcv-control-variable-correlations/` → `/publication/itcv-control-variable-correlations/`). Don't rename folders once the site is live — it breaks links other people have saved. To fix a title, edit `title:` inside the file and keep the folder.
- Talks, software, and people work the same way, or are pulled from small data files.
- "See also" cross-links, the research-area accordions on the homepage, and the tabs/filters on the Writings page are all **computed automatically**. Add a paper and it slots itself in.

---

## Add a new paper

1. In `content/publication/`, create a new folder with a short, lowercase, hyphenated name (the future URL), e.g. `content/publication/new-paper-slug/`.
2. Inside it, create `index.md`. Copy an existing paper's file as a template. The fields:

   ```yaml
   ---
   title: "The Exact Title of the Paper"
   date: 2026-01-01
   authors: ["Jesper N. Wulff", "Co Author"]
   publication_types: ["journal_article"]   # see list below
   publication: "Journal Name, 12(3), 45-67"
   journal: "Journal Name"
   volume: "12"
   issue: "3"
   pages: "45-67"
   doi: "10.xxxx/xxxxx"                       # optional
   tab: "articles"                            # which Writings tab it appears under
   areas: ["inference"]                       # research areas (see data/research_areas.json)
   tags: ["significance testing"]             # free-text keywords, used for search + See also
   abstract: "Optional abstract text."
   ---
   ```

3. Commit. Done — it appears on the Writings page, in the right tab, and cross-links itself.

**`publication_types` / `tab` values**

| `tab` | typical `publication_types` |
|-------|------------------------------|
| `articles` | `journal_article` |
| `book` | `book`, `book_chapter` |
| `proceedings` | `paper_conference` |
| `under-review` | `article` (also set `status: under_review`) |
| `working-papers` | `report` (also set `status: in_preparation`) |

Optional status flags that add a small badge: `status: under_review`, `status: in_preparation`, `status: in_press`, `status: revise_resubmit`.

**Awards:** add an `award:` line and a gold ribbon appears on the homepage, the Writings list, and the paper's page:
```yaml
award: "Best Paper, Research Methods Division, Academy of Management 2026"
```

**Homepage research areas:** the Methods/Applications accordions on the homepage are driven by
`data/research_areas.json` — each subarea has an explicit, ordered `papers` list of folder names.
A new paper only appears on the **homepage** after you add its slug to the right subarea there
(it appears on the Writings page automatically either way). The `areas:` field in a paper's
front matter controls the research-area *filter* on the Writings page; use the same ids
(`glm`, `inference`, `sensitivity`, `metascience`, `imputation`, `deeplearning`, `finance`, `pubadmin`, `epi`).

To attach a PDF: put the file in `static/files/`, then add
```yaml
url_pdf: "files/your-file.pdf"
```
(no leading slash — keeps the link portable if the site ever moves to a sub-path).

**Other link buttons** (all optional; they appear on the paper's page and in the homepage research areas):
```yaml
url_preprint: "https://ssrn.com/abstract=..."     # Preprint
url_source: "https://..."                          # Full text (open-access page)
url_code: "https://github.com/... or https://osf.io/..."  # Code / repository
url_app: "https://...shinyapps.io/..."            # Web app
url_video: "https://www.youtube.com/watch?v=..."  # Video abstract
```

---

## Add / edit software, teaching, contact, bio

- **Software:** a folder in `content/software/` with `index.md` (`title`, `pkg_kind`, `summary`, `links:` list, `related_paper:`).
- **Bio / CV:** edit `content/bio/_index.md` (plain Markdown). The short blurb on the **homepage** lives separately in `content/_index.md` (`intro:`) — keep the two different.
- **Teaching / Contact:** edit `content/teaching/_index.md` and `content/contact/_index.md`.
- **To replace the CV PDF:** overwrite `static/files/jesper-wulff-cv.pdf` (keep the name).

---

## Co-author links — please review them

Co-author names in citations link to each person's external page via `data/coauthors.json`
(a simple name → URL map). Those links were **found by web search**, so they can be wrong —
please skim the file once and fix or delete any entry. Two identity calls were made
automatically and are worth confirming:

- "Lonati, S." on the ITCV papers was resolved to **Sirio Lonati** (NEOMA), not "Stefano".
- The advisee **Maximiliano Cubillos** is treated as the same person as paper-author "Cubillos, M." (Cubillos Alvarez).

To stop linking a person, delete their line from `data/coauthors.json`; to add one, add a line
with their exact name as it appears in `authors:` lists.

---

## Things you may want to add later

- **Google Scholar** currently points to a name search. If you want your exact profile, replace the URL in `hugo.yaml` (under `profiles`) and `content/contact/_index.md`.
- **DOIs / abstracts** are filled in for most articles but not the conference proceedings, the two Danish articles, or the book chapter — add them to those `index.md` files if you like.
- **Cover images:** drop a `featured.jpg` next to any paper's `index.md` to show a thumbnail on its page.
- **The Bayesian-frequentist web app:** if it has a public URL, add it to `content/software/alphan/index.md`.

---

## Turning off the footer credit / directory listing

Both are on by default. In `hugo.yaml`:
```yaml
params:
  mysite:
    credit: false      # removes the "Created using GaryKing.org/mysite" footer line
    discovery: false    # removes the invisible directory-listing metadata
```
