# New Marketplace Demo

New Marketplace is a purple and lilac themed multi-seller B2C marketplace demo. It was created as a synthetic scope and boundary stress test, not from a real customer brief. The goal is to present a full-looking demo, hand over source code, and let a future technical team extend the dashboards, integrations, and production services.

Turkish documentation is available in [README_TR.md](./README_TR.md).

## What This Includes

- Customer storefront with campaign slider, category navigation, search, sorting, favorites, comparison, product detail pages, cart, and sandbox checkout.
- Local product gallery with 12 PNG demo product images under `public/demo-products`.
- Admin dashboard with marketplace metrics, role boundaries, provider health, audit log, and PNG logo upload.
- Seller dashboards for catalog, stock, delivery type, performance, campaign participation, commission, and payout visibility.
- Marketing dashboards for campaigns, banners, landing content, SEO/analytics mock state, banned-word moderation, and PNG logo upload.
- Finance dashboards for payment providers, invoice adapter state, refunds, chargebacks, seller payouts, commissions, and reconciliation.
- Support dashboards for order intervention limits, cancellation/refund handling, seller questions, escalations, and live support health.
- Local Express API that serves marketplace seed data and creates sandbox demo orders.
- English-first UI with a Turkish language toggle.

## Local Setup

```powershell
npm install
npm run dev
```

Default local addresses:

- Customer storefront: `http://localhost:5173`
- API: `http://localhost:4000`
- Health check: `http://localhost:4000/api/health`

## Demo Routes

- `http://localhost:5173` - public customer storefront
- `http://localhost:5173/musteri` - customer storefront alias
- `http://localhost:5173/admin` - admin control dashboard
- `http://localhost:5173/satici1` - seller catalog and stock use-case
- `http://localhost:5173/satici2` - seller performance and payout use-case
- `http://localhost:5173/marketing1` - marketing campaign use-case
- `http://localhost:5173/marketing2` - marketing SEO and moderation use-case
- `http://localhost:5173/finans1` - finance payment and refund use-case
- `http://localhost:5173/finans2` - finance payout and reconciliation use-case
- `http://localhost:5173/destek1` - support order/refund use-case
- `http://localhost:5173/destek2` - support live support and seller question use-case

Only customer categories are shown in the sidebar. Dashboard routes are intentionally reachable by direct URL only.

## Build And Validation

```powershell
npm run lint
npm run build
```

## API Endpoints

- `GET /api/health`: local API health check.
- `GET /api/marketplace`: products, sellers, orders, campaigns, providers, and audit seed data.
- `POST /api/orders/checkout`: creates a sandbox demo order.

## Language Support

The default UI language is English. The sidebar language toggle switches the customer storefront and dashboard interface to Turkish. The localization copy is stored in `src/i18n.ts`.

## Logo Upload

Admin and marketing dashboards can upload their own logos.

- Accepted file type: `image/png`
- Maximum file size: `512 KB`
- Behavior: upload, preview, replace, remove
- Storage: browser `localStorage` for demo use

## Demo Product Images

Product cards use local PNG demo images so the storefront looks populated without relying on external image URLs at runtime. The API seed data returns paths from `public/demo-products`.

## Demo vs Production Boundary

This repository is intentionally a demo delivery, not a production marketplace backend.

- Payment: sandbox/mock
- Shipping: mock adapter
- E-invoice and e-archive: mock adapter
- Analytics and pixels: mock connected
- KVKK/GDPR, commercial messaging consent, production payment contracts, production shipping contracts, invoice integrations, observability, and security hardening must be completed by the production technical and legal teams.

## Source Code Handoff Notes

Useful extension points:

- `server/index.mjs`: demo API boundary that can later connect to real backend services.
- `src/api.ts`: frontend API adapter layer.
- `src/data.ts`: frontend types and fallback seed data.
- `src/i18n.ts`: English and Turkish UI copy.
- `src/App.tsx`: demo screen flows, routes, product detail behavior, and dashboard interactions.
- `src/App.css`: responsive UI, purple/lilac visual system, and dashboard layout.

## Accepted Demo Risks

- This demo does not prove 10M daily visitor production capacity.
- Real payment, shipping, invoice, and CRM integrations are separated as mock/sandbox concerns.
- A marketplace clone can carry legal/IP risk in production. This repo is delivered as a workflow and UI demo.
- Privacy, security, auditability, and compliance controls require production review before go-live.
