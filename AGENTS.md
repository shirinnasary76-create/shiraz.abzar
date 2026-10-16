# Base44 Dev Environment

## Project Overview
Static single-page HTML storefront (Persian RTL e-commerce for "شیراز ابزار" / Shiraz Tools).
One file: `index.html` — inline CSS and JS, no build step, no backend, no dependencies to install.
External resources: Google Fonts (Vazirmatn) and Font Awesome CDN — loaded at runtime, no credentials.

## Running the app
```
docker compose -f docker-compose.base44.yml up -d
```
Serves `index.html` via nginx:alpine on host port 3000.

## Verifying
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` → 200
- Preview at http://localhost:3000/ shows the storefront.

## No secrets required
No external service credentials are needed. All data is hardcoded in the HTML.
