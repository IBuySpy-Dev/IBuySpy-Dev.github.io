# IBuySpy-Dev Organization Site — Live Factory Hub

This repo powers the IBuySpy-Dev organization landing page at https://ibuyspy-dev.github.io/

The page is a **live factory hub** — a data-driven control tower that fetches real-time state from the factory registry at runtime.

## Data Source

```
https://raw.githubusercontent.com/IBuySpy-Dev/app-migration-with-ai/main/docs/factory-state.json
```

No build step required. All data is fetched by the browser on page load.

## Sections

| Section | Description |
|---|---|
| **Live Stats Bar** | Total, Active, Blocked, Complete, Reference — computed from live data |
| **Treatment Breakdown** | CSS bar chart showing count/% per treatment (Replatform, Rehost, Rewrite, Retire, Reference) |
| **Blocked Apps Panel** | Red alert panel listing apps with blocked stations (hidden when none) |
| **Station Health Table** | Per-station (S1–S5) counts: Done / Pending / Blocked / N/A |
| **Recently Validated** | Last 5 apps sorted by `lastValidated` date |
| **All Apps Table** | Sortable, collapsible table of all apps with Azure URL links |
| **Migration Stations Pipeline** | Static Intake → S1 → S2 → S3 → S4 → S5 → ✅ diagram |

## Features

- 🔄 **Refresh button** re-fetches with cache-busting (`?t=Date.now()`)
- ⚠️ **Error handling** — shows error message + retry button if fetch fails
- 📱 **Mobile responsive** — works on all screen sizes
- 🚫 **No CDN dependencies** — pure HTML/CSS/JS, offline-capable once loaded

## Local Development

Open `index.html` directly in a browser, or use any static file server:

```bash
npx serve .
# or
python -m http.server 8080
```

Note: Due to CORS, the live data fetch requires a server (not `file://`). The GitHub Pages deployment works correctly.

## Deployment

Automatically deployed to GitHub Pages on push to `main` via the GitHub Actions workflow in `.github/workflows/deploy.yml`.
