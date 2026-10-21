# Campaign Performance Analyser

Self-serve dashboard for Klaviyo email + SMS campaign performance. Upload CSVs (or a public Google Sheet); datasets are stored in the viewer's browser.

Live: https://campaign-performance-analyser.vercel.app

## Structure
- `public/index.html` — the app (single self-contained file; Chart.js + PapaParse from jsDelivr)
- `vercel.json` — static hosting config: serves `public/`, no build step
- `archive/` — previous live versions, kept for rollback (not deployed)

## Deploy
Once this repo is connected to the Vercel project, every push to `main` redeploys.

## Roll back
Copy the relevant file from `archive/` over `public/index.html`, commit, push.

## Data notes
- Email and SMS exports can be dropped together or added to an existing dataset ("+ Add file to dataset").
- Channel comes from the `channel` / Campaign Channel column; if missing, from the file name, then campaign name, then presence of opens. Inferred channels are flagged.
- Open rate is email-only. Verdicts benchmark against the median of the campaign's own channel.
- Baselines are compared per channel when filtered; tag baseline rows with a channel to enable this.
