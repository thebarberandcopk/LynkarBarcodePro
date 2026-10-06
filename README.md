# LynkKar Pro Label Studio

Cloudflare Workers + Firebase Authentication + Cloud Firestore.

## Deployment

Repository root must contain:

- `public/index.html`
- `src/worker.js`
- `wrangler.toml`
- `package.json`

Cloudflare deploy command:

`npx wrangler deploy`

Root directory: `/`

See `FIREBASE_ADMIN_SETUP.md` before publishing `firebase/firestore.rules`.
