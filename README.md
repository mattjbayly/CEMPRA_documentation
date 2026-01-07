# CEMPRA Documentation

Cumulative Effects Model for Prioritizing Recovery Actions (CEMPRA) Guidance Documentation.

**Live Site**: [https://mattjbayly.github.io/CEMPRA_documentation/](https://mattjbayly.github.io/CEMPRA_documentation/)

## Quick Start

### Prerequisites
- [Quarto](https://quarto.org/docs/get-started/) installed
- Git

## Publishing Workflow

### Step 1: Edit on main branch

```bash
git checkout main
git pull origin main

# Edit your .qmd files, images, etc.

git add .
git commit -m "Your changes"
git push origin main
```

### Step 2: Publish to gh-pages

```bash
git checkout gh-pages
git merge main
quarto render
git add docs/
git commit -m "Publish updates"
git push origin gh-pages
git checkout main
```

**Important**: You must run `quarto render` *after* merging main into gh-pages. The render must happen on the gh-pages branch.

### One-Command Publish

After committing and pushing changes on main:

```bash
git checkout gh-pages && git merge main && quarto render && git add docs/ && git commit -m "Publish updates" && git push origin gh-pages && git checkout main
```

## Branch Structure

| Branch | Purpose | `docs/` folder |
|--------|---------|----------------|
| **main** | Source files only | Ignored (in .gitignore) |
| **gh-pages** | Deployment | Tracked and pushed |

## Troubleshooting

### Site not updating after push
- Did you run `quarto render` on the gh-pages branch *after* merging?
- Wait 2-5 minutes for GitHub Pages to deploy
- Check GitHub repo > Actions tab for deployment status
- Clear browser cache

### Merge conflicts
1. Resolve conflicts in source files
2. Run `quarto render` again
3. Commit and push

## Links

- **R Package**: https://github.com/essatech/CEMPRA
- **Shiny App**: https://github.com/essatech/CEMPRAShiny
- **Shiny App (Live)**: https://essa.shinyapps.io/CEMPRAShiny/
