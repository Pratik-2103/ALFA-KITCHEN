# Alfa Kitchen live site

This folder contains the single-file front end plus the Netlify Function needed for customer-phone orders to reach the restaurant laptop.

## What's included

- `index.html` — landing page, floor manager, customer-only menu, kitchen, billing and director screens. Styles, scripts and the supplied UPI QR image are embedded.
- `netlify/functions/orders.mjs` — shared order API. Orders are stored in Netlify Blobs so a phone and the restaurant laptop see the same orders.
- `netlify.toml` and `package.json` — Netlify build and dependency settings.

## Deploy

Deploy this folder as the site root using the Netlify-connected Git repository or Netlify CLI. The deploy must include the `netlify/functions` folder and `package.json`; uploading only `index.html` will not enable live phone-to-laptop orders.

Before deploying this update, add a private environment variable named `STAFF_PIN` in the Netlify project settings. Use a strong password with at least 12 characters and give it only to restaurant staff. The home page's Staff Login checks this password, and the orders function requires it for kitchen, floor, director and billing data. Customer menu and table order placement remain public. After adding the variable, trigger a fresh production deploy.

Once deployed, open the Floor Manager, choose a table, and use **Customer QR**. Print that table's QR and place it on the table. A customer scan opens only the menu for that table. Their order is sent to the shared order store, where the Kitchen Studio refreshes automatically. Kitchen status changes and bills are also saved to that store.

Open the site over its deployed HTTPS address for real cross-device ordering. Opening the HTML directly from a file uses a local preview and cannot send an order from a phone to a laptop.

The Kitchen Studio's **Enable Sound** button must be clicked once per browser session so the browser permits order and served alerts.
