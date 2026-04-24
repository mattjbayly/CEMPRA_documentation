# CEMPRA Documentation

Cumulative Effects Model for Prioritizing Recovery Actions (CEMPRA) Guidance Documentation.

**Live Site**: [https://mattjbayly.github.io/CEMPRA_documentation/](https://mattjbayly.github.io/CEMPRA_documentation/)

## Publishing Workflow

Everything lives on the `main` branch. GitHub Pages serves from `main/docs`.

```bash
# Edit .qmd files, then:
quarto render --to html
git add .
git commit -m "Update site"
git push origin main
```

Site updates within a few minutes of pushing.

## Links

- **R Package**: https://github.com/essatech/CEMPRA
- **Shiny App**: https://github.com/essatech/CEMPRAShiny
- **Shiny App (Live)**: https://essa.shinyapps.io/CEMPRAShiny/
