# LynkKar Pro Label Studio

Cloudflare Worker + static assets deployment package.

## Structure
- `public/index.html` — Label Studio dashboard
- `src/worker.js` — Cloudflare Worker static asset handler
- `wrangler.toml` — Wrangler configuration
- `package.json` — deployment script

## Deploy
Run:

`npx wrangler deploy`

The Firebase configuration is already contained in `public/index.html`. Firebase Auth, Firestore, and Storage are configured client-side by the dashboard.
