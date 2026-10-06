# LynkKar Pro Label Studio — V2

This package keeps the working Cloudflare Worker setup and adds a redesigned public/login landing dashboard, animated product preview, subscription pricing on the landing page, and an admin subscription management area.

## Deploy
- Replace `public/index.html` in the GitHub repository.
- Add `public/assets/lynkkar-demo.mp4`.
- Keep `src/worker.js` and `wrangler.toml` as shown.
- Cloudflare Build command: `npx wrangler deploy`
- Root directory: `/`

## Firebase
Publish `firebase/firestore.rules` after confirming the main admin document exists.

The public `settings/subscriptions` document stores only pricing, limits, feature flags, export permissions, and support contacts. Admins can edit it from the **Customers → Subscription Pricing & Features** tab.

## Default plans
- Starter: PKR 999/month, 30-day duration, 500 labels/month, 1 user seat
- Pro: PKR 2,499/month, 30-day duration, 10,000 labels/month, 5 user seats
- Business: PKR 5,999/month, 30-day duration, unlimited labels/month, 20 user seats

These are editable by the main admin.

## Important
The app uses Firebase Authentication + Firestore as the cloud account source of truth. Normal signups remain regular users and require admin approval. The role field is immutable through client rules so users cannot promote themselves to admin.
