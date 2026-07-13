# Landlord Tools — Calculator Suite

Public calculator suite hosted on GitHub Pages. Lives at thegalleryrealestate.github.io/landlord-tools/.

## Repo

- Repo: `Thegalleryrealestate/landlord-tools`
- Auto-deploys on push to main
- No git CLI available in Cowork. Upload via GitHub web UI.

## Calculators

Live and linked from the hub:
- `rental-yield.html`
- `cash-flow.html`
- `investment-roi.html`
- `mortgage.html`
- `index.html` (hub page)

Built but hidden (need work before going live):
- `fee-savings.html`
- `fee-comparison.html`
- `appraisal.html`
- `income-maximiser.html` (blocked on real REA suburb median rent data)

## Design conventions

Match the main TGRE website:
- Cream background (#F9F2ED), dark sections (#181819)
- Terracotta accent (#D46144)
- Aventa headings, Geist body
- Self-contained single-file HTML (no external CSS, JS or image assets)
- Fonts embedded as base64

## Workflow

1. Edit the relevant `.html` file locally in this folder
2. Test in browser
3. Upload via GitHub web UI to `Thegalleryrealestate/landlord-tools`
4. GitHub Pages deploys within a minute or two

## Watchouts

- Each calculator is a single-file HTML (~800 KB with embedded fonts). Do not split into external assets.
- When adding a new calculator, link it from `index.html` and add it to the nav inside existing calculator files so the nav stays consistent.
- Performance stats and copy references live in `../reference/stats.md` and `../reference/brand-positioning.md`.
