# Landlord Tools — Calculator Suite

Public calculator suite hosted on GitHub Pages. Lives at thegalleryrealestate.github.io/landlord-tools/.

## Repo

- Repo: `Thegalleryrealestate/landlord-tools`
- Auto-deploys on push to main
- No git CLI available in Cowork. Upload via GitHub web UI.

## Calculators

All 8 live and linked from the hub (`index.html`), in two hub sections:

The toolkit (01): `rental-yield.html`, `cash-flow.html`, `investment-roi.html`, `mortgage.html`
Fees and income (02): `fee-comparison.html`, `fee-savings.html`, `income-maximiser.html`, `appraisal.html`

Notes on the July 2026 relaunch of the second four:
- Fee figures come from the standard proposal schedule: 6% management, 155% of one week letting, $500 marketing, $9/mo admin. On both fee pages every TGRE figure is an editable input, never a hardcoded claim.
- `appraisal.html` is a real lead form: two-step (property details, then contact), POSTs to `https://tgre-team.netlify.app/api/report-lead` with `source_page: calc-appraisal`.
- `income-maximiser.html` uses hardcoded indicative suburb medians (July 2026) with visible "guide figures only" disclaimers. Update the `SUBURB_DATA` object when refreshed figures are available.
- `rent-converter.html` is a small embeddable widget for the website, not part of the hub.

## Design conventions

Redesigned Jul 2026 to read as real pages of the website (editorial style, matching the report tool / proposal v5).

- The hub and all 4 live calculators load the LIVE site design system for their chrome: `beforeload.css`, `site.css`, `fonts_local.css`, `fonts_remote.css` from `www.thegalleryrealestate.com.au`, plus the site JS (`customelements.js`, `cowtools.js`, `cssvars.js`) for the menu. This keeps header, mobile menu and footer exactly in sync with the site.
- Header, mobile sidenav and footer markup are copied verbatim from the live site (root-relative hrefs rewritten to absolute). To refresh them, re-scrape from a live page and update the blocks in `index.html`, then re-run the calculator transform.
- Body/editorial framing is scoped (`.lt` on the hub, `.ltc` on calculators) so `site.css` cannot clash. Note: the calculators' own `.hero` class collides with `site.css` — the calc hero was renamed `.calc-hero`. The calc card UI (`.calc-card`, inputs, sliders, charts) is class-scoped and survives `site.css` untouched.
- Light mode only (matches the site). The old dark-mode toggle and `prefers-color-scheme` auto-switch were removed from the calculators.
- Cream background (#F9F2ED), dark sections (#181819), terracotta accent (#d46144), Aventa headings.
- Calculators keep their embedded base64 Aventa fonts for the calc UI; the site CSS also loads Aventa for the chrome.
- Embedded/iframe mode: site chrome, hero and CTA are hidden via `html.embedded` rules so only the calculator shows (postMessage resize preserved).
- Editorial guide layer (Jul 2026): each live calculator has a `.edt` section between the capture form and the dark CTA — guide prose, three `.edt-card` benchmark cards, a details/summary FAQ, "Keep running the numbers" cross-link pills and a compliance disclaimer. Scoped CSS appended to the page's style block; hidden in embedded mode via `html.embedded .edt`. Keep new calculators to the same shape (~1,000 words a page).

The transform script that applied the shell to the calculators is at
`TGRE Claude/.../scratchpad/transform_calcs.py` (re-derives shared blocks from `index.html`).

## Workflow

1. Edit the relevant `.html` file locally in this folder
2. Test in browser
3. Upload via GitHub web UI to `Thegalleryrealestate/landlord-tools`
4. GitHub Pages deploys within a minute or two

## Watchouts

- Each calculator is a single-file HTML (~800 KB with embedded fonts). Do not split the calc UI into external assets (chrome CSS/JS is loaded from the live site).
- When adding a new calculator, add an editorial numbered row to the hub in `index.html`, then apply the same shell (copy the head links, site header/sidenav/footer blocks, `.calc-hero`, dark CTA and site JS) via the transform script. There is no longer a per-page calculator nav; cross-navigation is the "All tools" back link plus the footer.
- Performance stats and copy references live in `../reference/stats.md` and `../reference/brand-positioning.md`.
