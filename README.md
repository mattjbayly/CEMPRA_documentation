# CEMPRA Documentation

Cumulative Effects Model for Prioritizing Recovery Actions (CEMPRA) Guidance Documentation.

**Live site**: https://mattjbayly.github.io/CEMPRA_documentation/

This repository holds the source for the CEMPRA guidance website, authored as a
[Quarto book](https://quarto.org/docs/books/) and published with GitHub Pages.

## How this project is set up

- **Source**: Quarto book. Chapters and appendices are `.qmd` files in the repo
  root (`index.qmd`, `01_intro.qmd`, … `references.qmd`, `appendix_*.qmd`). The
  chapter order and site config live in `_quarto.yml`.
- **Bibliography**: `references.bib`, formatted with `apa.csl`.
- **Rendered output**: Quarto renders the whole site into the `docs/` folder
  (`output-dir: docs` in `_quarto.yml`). The `docs/` folder is **committed to the
  repo** — it is not a build artifact you can ignore.
- **Hosting**: GitHub Pages serves the site directly from the **`/docs` folder on
  the `main` branch**. There is no build step on GitHub's side and no GitHub
  Actions workflow — GitHub just serves the committed HTML.

Everything happens on `main`. There is **one source of truth**: you render
locally and commit both the `.qmd` sources and the rendered `docs/` output
together.

### Repository layout

```
CEMPRA_documentation/
├── _quarto.yml           # site config: title, chapter order, output-dir: docs
├── index.qmd             # home page (includes the bibliography list)
├── 01_intro.qmd … 12_conclusions.qmd, references.qmd, appendix_*.qmd
├── references.bib        # bibliography database
├── apa.csl               # citation style
├── images/ , assets/     # figures and supporting files
└── docs/                 # RENDERED SITE — committed; this is what Pages serves
```

## Deploying an update (the only workflow you need)

From the repository root, with [Quarto](https://quarto.org/docs/get-started/)
installed (and R, since some chapters run R code):

```bash
# 1. Edit the .qmd source files (and references.bib if adding citations)

# 2. Re-render the whole site into docs/
quarto render --to html

# 3. Commit BOTH the source changes and the rendered docs/ output
git add .
git commit -m "Describe the change"

# 4. Publish
git push origin main
```

GitHub Pages redeploys automatically within ~1–3 minutes of the push.

> **Important:** always run `quarto render` before committing. Editing a `.qmd`
> file alone does **not** change the live site — Pages serves the pre-rendered
> HTML in `docs/`. If you commit source edits without re-rendering, the website
> will not reflect your changes.

## Verifying a deployment

After the push, confirm the live site actually updated:

1. Wait 1–3 minutes for the Pages build.
2. Hard-refresh the page (**Ctrl+F5**) or open it in a private window — browsers
   and GitHub's CDN cache aggressively, so a normal refresh may show the old
   version for several minutes.

To check past the CDN cache from the command line (PowerShell):

```powershell
$url = "https://mattjbayly.github.io/CEMPRA_documentation/index.html?cb=" + [guid]::NewGuid()
(Invoke-WebRequest $url -Headers @{ 'Cache-Control'='no-cache' } -UseBasicParsing).Content -match "some new text you added"
```

If the raw source on GitHub
(`raw.githubusercontent.com/mattjbayly/CEMPRA_documentation/main/docs/index.html`)
shows your change but the live `github.io` site does not, it is a caching/build
delay — give it a few minutes.

## GitHub Pages configuration (one-time, already done)

This is set under **Settings → Pages** on GitHub and does not normally need to
change:

- **Source**: Deploy from a branch
- **Branch**: `main`
- **Folder**: `/docs`

> **Note:** An old `gh-pages` branch was previously used as the publishing source.
> It is **deprecated and no longer served** — do not push to it. The single
> `main` + `/docs` setup above is the current, canonical workflow.

## Links

- **R Package**: https://github.com/essatech/CEMPRA
- **Shiny App**: https://github.com/essatech/CEMPRAShiny
- **Shiny App (Live)**: https://essa.shinyapps.io/CEMPRAShiny/
