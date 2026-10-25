# TurtleType (TURTLETYPE)

**Status:** Maintain · Stage: built / beta, pre-revenue · Health: Amber · Last verified 2026-10-24

## What it is
"A dark, minimal typing test with local progress and targeted practice." 15/30/60-second and 10/25/50-word tests. Free stores the last 20 results and preferences locally. **Plus** ($10/year) adds account-synced results, progress, commonly missed words, focused practice and a daily challenge. — [README](https://github.com/ryanmhopkins/turtletype/blob/main/README.md)

## Audience
People practicing typing speed/accuracy (Monkeytype-style users; README states it is independent of Monkeytype). Size/segments: UNKNOWN - source needed: analytics.

## Stack
- Static app built with esbuild (`scripts/build.mjs`) → `dist/`; build runs tests first (`npm test && node scripts/build.mjs`) — [package.json](https://github.com/ryanmhopkins/turtletype/blob/main/package.json)
- Vercel function `api/results.js`: Neon Auth session lookup + RevenueCat entitlement check, stores results in `public.test_results` — [api/results.js](https://github.com/ryanmhopkins/turtletype/blob/main/api/results.js)
- Neon Postgres + Neon Auth via Vercel integration (env names `DATABASE_URL`, `DATABASE_URL_UNPOOLED`, `NEON_AUTH_BASE_URL`, `VITE_NEON_AUTH_URL`, `NEON_PROJECT_ID`, PG*/POSTGRES_* — Vercel MCP, names only)
- RevenueCat Web SDK (`@revenuecat/purchases-js`), product `turtletype_plus_yearly`, entitlement `plus` — README

## Deploy
- Vercel project `turtletype` (`prj_EbSYep99cG9hN30a3HBb9FTlu4sJ`), created 2026-10-24 — Vercel MCP
- Latest production: `dpl_yjzGtDG9WaNAV5ev6mvZBAFkiXyR` READY, `main` @ 53ff48a5 "Add Turtletype Plus account and progress foundation", 2026-10-24 20:33 ET — Vercel MCP
- Domains: turtletype-henna.vercel.app (+ Vercel aliases); no custom domain — Vercel MCP
- Repo private, created 2026-10-24; 4 commits; 0 issues, 0 PRs — GitHub MCP

## Integrations
GitHub, Vercel, Neon (via Vercel integration). RevenueCat: referenced in code but **`REVENUECAT_WEB_PUBLIC_KEY` is not set** in Vercel env → checkout shows "checkout opening soon" and `/api/results` returns 503 "billing setup pending" for signed-in users. Live Stripe account connection to RevenueCat: UNKNOWN - source needed: RevenueCat dashboard. Analytics: **none**.

## Revenue model
Free + Plus $10/year subscription via RevenueCat (Stripe). **Not live.** Subscribers/revenue: 0 expected but UNKNOWN - source needed: RevenueCat dashboard (no connector).

## Known risks
1. Billing not connected (README: needs live Stripe + live web public key).
2. Server-side entitlement check calls RevenueCat REST v1 `/subscribers/{id}` with the **public** web key — needs FORGE verification that this is supported and not spoofable (TT-001).
3. Plus sign-in/result sync untested live (no Plus users possible yet).
4. No analytics or monitoring.
5. Ops-repo profile previously listed RevenueCat/Neon "unverified" — now verified via code + env names.

## Open questions
- Does Ryan want TurtleType Plus live now, or parked while ClearFrame is the focus?
- Custom domain wanted? UNKNOWN - source needed: Ryan.

## Evidence
- Repo: https://github.com/ryanmhopkins/turtletype (commits a41da13b, 8c336abb, d1156ace, 53ff48a5)
- Vercel MCP: `get_project`, `get_deployment`, `filter_project_envs` (names only)
- HTTP: https://turtletype-henna.vercel.app → 200 (2026-10-24)
