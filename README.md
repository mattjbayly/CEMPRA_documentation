# CEMPRA Documentation

Cumulative Effects Model for Prioritizing Recovery Actions (CEMPRA) Guidance Documentation.

**Live Site**: [https://mattjbayly.github.io/CEMPRA_documentation/](https://mattjbayly.github.io/CEMPRA_documentation/)

## Quick Start

### Prerequisites
- [Quarto](https://quarto.org/docs/get-started/) installed
- Git
- R (optional, for rendering R code chunks)

## Development Workflow

### Making Updates to Documentation

1. **Switch to the main branch** (where you do all editing)
   ```bash
   git checkout main
   git pull origin main
   ```

2. **Edit your .qmd files**
   - Edit any `.qmd` files in the root directory
   - Update images in `images/`
   - Modify `_quarto.yml` for configuration changes

3. **Preview locally** (optional but recommended)
   ```bash
   quarto render
   ```
   - Open `docs/index.html` in your browser to preview
   - The `docs/` folder is ignored on main branch

4. **Commit your changes**
   ```bash
   git add .
   git commit -m "Description of your changes"
   git push origin main
   ```

### Publishing to GitHub Pages

Once you're happy with your changes on main, publish them:

1. **Build the site**
   ```bash
   quarto render
   ```

2. **Switch to gh-pages branch**
   ```bash
   git checkout gh-pages
   ```

3. **Merge updates from main**
   ```bash
   git merge main
   ```

4. **Commit the rendered output**
   ```bash
   git add docs/ .gitignore
   git commit -m "Publish updates: [brief description]"
   ```

5. **Push to GitHub**
   ```bash
   git push origin gh-pages
   ```

6. **Return to main for next round of edits**
   ```bash
   git checkout main
   ```

GitHub Pages will automatically deploy your changes within a few minutes!

## One-Command Publishing Script

For convenience, you can use this sequence to publish after making changes on main:

```bash
# On main branch after committing changes:
quarto render && \
git checkout gh-pages && \
git merge main && \
git add docs/ .gitignore && \
git commit -m "Publish updates" && \
git push origin gh-pages && \
git checkout main
```

## Branch Structure

This repository uses a two-branch workflow:

| Branch | Purpose | Contains | Tracked in Git |
|--------|---------|----------|----------------|
| **main** | Development & source control | `.qmd` files, images, configs | Source files only (no `docs/`) |
| **gh-pages** | Deployment to GitHub Pages | Source + rendered HTML | Everything including `docs/` |

### Why Two Branches?

- **main**: Clean source history without build artifacts
- **gh-pages**: Deployment branch with rendered HTML for GitHub Pages
- This keeps your git history clean and separates source from output

## Project Structure

```
CEMPRA_documentation/
├── _quarto.yml           # Quarto book configuration
├── index.qmd             # Front matter / welcome page
├── 01_intro.qmd          # Chapter 1
├── 02_stressor_response.qmd  # Chapter 2
├── ...                   # More chapters
├── images/               # Image assets
├── sample_data/          # Example datasets
└── docs/                 # Rendered output (only on gh-pages)
```

## Troubleshooting

### "docs/ is ignored by .gitignore" when on gh-pages

If you get this error when trying to add docs/ on gh-pages:
- Make sure you're on gh-pages branch: `git branch --show-current`
- The .gitignore on gh-pages should NOT exclude `/docs/`
- The .gitignore on main SHOULD exclude `/docs/`

### Merge conflicts when merging main to gh-pages

If you get conflicts during merge:
1. Resolve conflicts in source files (.qmd)
2. After resolving, run `quarto render` again
3. Then commit and push

### Site not updating on GitHub Pages

- Check the Actions tab on GitHub for deployment status
- Wait 2-5 minutes after pushing
- Clear your browser cache

## Contributing

1. Create a new branch from main for significant changes
2. Make your edits
3. Test with `quarto render`
4. Submit a pull request to main

## Links

- **Live Documentation**: https://mattjbayly.github.io/CEMPRA_documentation/
- **R Package**: https://github.com/essatech/CEMPRA
- **Shiny App**: https://github.com/essatech/CEMPRAShiny
- **Shiny App (Live)**: https://essa.shinyapps.io/CEMPRAShiny/
