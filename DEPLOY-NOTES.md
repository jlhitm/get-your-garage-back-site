# Get Your Garage Back — Deploy Notes

## Canonical source
`~/Code/get-your-garage-back-site/` (this repo). Mirrors the HCC pattern at `~/Code/hill-country-cleaning-site/`.

## Stack
- Single-page HTML/CSS/JS
- Hosted on Netlify (site already live at getyourgarageback.co)
- No framework, no build step

## Deploy flow (target state)
1. Edit locally in this repo
2. `git commit -am "…"` and `git push`
3. Netlify auto-builds from GitHub on push
4. Live within ~60 seconds

## Current state (2026-04-10)
- Local git repo initialized
- GitHub remote NOT YET created (Jordan to create in Phase 2b)
- Netlify is currently wired to manual drag-and-drop deploys. After GitHub repo exists, Jordan reconnects the Netlify site to auto-deploy from GitHub.

## Placeholders to fill (Phase 2b)
- `GYGB_PIXEL_ID_PLACEHOLDER` in `index.html` (Meta Pixel base code) — replace with the real GYGB Pixel ID once created in HCC Business Manager
- `+1QUOPLACEHOLDER` in the thank-you SMS CTA — replace with the provisioned QUO phone number
- `https://n8n.placeholder.local/webhook/gygb-lead` — replace with the real n8n webhook URL once the workflow is deployed

## Deployment steps to activate auto-deploy (Jordan, Phase 2b)
1. Create a new GitHub repo: `jlhitm/get-your-garage-back-site` (private is fine)
2. From this directory:
   ```bash
   cd ~/Code/get-your-garage-back-site
   git remote add origin git@github.com:jlhitm/get-your-garage-back-site.git
   git push -u origin main
   ```
3. Netlify dashboard → select getyourgarageback.co site → Site settings → Build & deploy → Link to GitHub repo `jlhitm/get-your-garage-back-site` → branch `main` → build command: (none) → publish directory: `/`
4. Verify next commit triggers auto-build

## UTM parameter convention
Ad URLs should use:
```
?utm_source=meta&utm_campaign=gygb&utm_content=<adname>
```
`utm_content` controls the attention bar neighborhood text via simple substring match (circle-c / legend-oaks / belterra / meridian / shady-hollow / travis-country).
