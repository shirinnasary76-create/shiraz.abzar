# AGENTS.md — Base44 dev environment notes

## Project
Single-page static Persian (RTL) website for the Ministry of Industry, Mine and Trade (وزارت صمت).
The entire app is one file: `index.html` (HTML + embedded CSS + vanilla JS). No build step, no framework, no backend.

## Running in the sandbox
- `docker compose -f docker-compose.base44.yml up -d` serves `index.html` via `nginx:alpine` on host port 3000.
- The repo is bind-mounted read-only into the container; edits to `index.html` appear on browser refresh (no hot reload — call `reload_preview` after edits if needed).
- A custom `nginx.conf` runs nginx as `user root` so the bind-mounted source is readable regardless of host directory permissions (the sandbox `/app` dir is often `0700`).
- Healthcheck uses `http://127.0.0.1:80/` (not `localhost`) because nginx listens on IPv4 only and `localhost` resolves to `::1` inside the container.

## External links
Official service links point to real government portals: `mimt.gov.ir`, `my.gov.ir`, `ecommerce.gov.ir`, `imidro.gov.ir`, `gsi.ir`. Do not invent government services or URLs.

## Images
Uses Unsplash `images.unsplash.com` photo URLs. Some photo IDs get removed by Unsplash over time and return 404 (visible as console "Failed to load img" errors). Replace broken IDs with known-working industrial photo IDs; check the browser console after edits.
