# TurtleType (TURTLETYPE)

**Status:** Maintain · Stage: built / beta, pre-revenue · Health: Amber · Last verified 2026-10-24

## What it is
"A dark, minimal typing test with local progress and targeted practice." 15/30/60-second and 10/25/50-word tests. Free stores the last 20 results and preferences locally. **Plus** ($10/year) adds account-synced results, progress, commonly missed words, focused practice and a daily challenge. — [README](https://github.com/ryanmhopkins/turtletype/blob/main/README.md)

## Audience
People practicing typing speed/accuracy (Monkeytype-style users; README states it is independent of Monkeytype). Size/segments: UNKNOWN - source needed: analytics.

## Stack
- Static app built with esbuild (`scripts/build.mjs`) → `dist/`; build runs tests first (`npm test && node scripts/build.mjs`). `npm test` is `node --test engine/insights` — [package.json](https://github.com/ryanmhopkins/turtletype/blob/main/package.json). No lint or typecheck script. `api/results.js` is untested. No CI — AUD-FORGE-001
- Vercel function `api/results.js`: Neon Auth session lookup + RevenueCat entitlement check, stores results in `public.test_results` — [api/results.js](https://github.com/ryanmhopkins/turtletype/blob/main/api/results.js)
- Neon Postgres + Neon Auth via Vercel integration (env names `DATABASE_URL`, `DATABASE_URL_UNPOOLED`, `NEON_AUTH_BASE_URL`, `VITE_NEON_AUTH_URL`, `NEON_PROJECT_ID`, PG*/POSTGRES_* — Vercel MCP, names only)
- RevenueCat Web SDK (`@revenuecat/purchases-js`), product `turtletype_plus_yearly`, entitlement `plus` — README

## Deploy
- Vercel project `turtletype` (`prj_EbSYep99cG9hN30a3HBb9FTlu4sJ`), created 2026-10-24 — Vercel MCP
- Latest production: `dpl_yjzGtDG9WaNAV5ev6mvZBAFkiXyR` READY, `main` @ 53ff48a5 "Add Turtletype Plus account and progress foundation", 2026-10-24 20:33 ET — Vercel MCP; AUD-FORGE-001
- Domains: turtletype-henna.vercel.app (+ Vercel aliases); no custom domain — Vercel MCP
- Repo private, created 2026-10-24; 4 commits; 0 issues, 0 PRs — GitHub MCP

## Integrations
GitHub, Vercel, Neon (via Vercel integration; **no Neon connector**). RevenueCat is referenced in code but **`REVENUECAT_WEB_PUBLIC_KEY` is not set** → checkout shows "checkout opening soon" and `/api/results` returns 503 for signed-in users. Without a session, `/api/results` returns 401 (expected). No RevenueCat connector. Stripe connector needs auth. No CI or branch protection. No analytics, uptime monitor, error monitor, cost feed, or support intake. Live Stripe connection to RevenueCat: UNKNOWN - source needed: RevenueCat dashboard.

## Revenue model
Free + Plus $10/year subscription via RevenueCat (Stripe). **Not live.** Subscribers and revenue: UNKNOWN - source needed: RevenueCat dashboard (no connector). Do not treat the gap as zero.

## Known risks
1. `REVENUECAT_WEB_PUBLIC_KEY` is unset. `/api/results` returns 503 for signed-in users. Plus and sync have never run live (TT-002). — AUD-FORGE-001, AUD-GUARD-001
2. TT-001 review is done. The entitlement approach is sound: the server checks `neon_auth.session`, then RevenueCat v1 `/subscribers` with the public key. Results cannot be spoofed. Client gates are UI only. It is a configuration gap, not a code bug. Not shipped (TT-005): an `rcb_` prefix build check, `grace_period_expires_date`, and `node --test` for hasPlus. A sandbox key (`rcb_sb_`) in production would grant Plus on test purchases. GET creates RevenueCat customers. No caching. Client and server both need a redeploy after the key is set. — AUD-FORGE-001
3. No security headers. `@neondatabase/neon-js` is on a beta caret range (impact UNKNOWN). — AUD-FORGE-001
4. No CI or branch protection. No lint/typecheck. `api/results.js` is untested. — AUD-FORGE-001
5. No analytics, uptime monitor, error monitor, or cost feed. Spend and revenue UNKNOWN. No support intake. — AUD-GUARD-001, AUD-PULSE-001
6. SEO: two H1s, no canonical, no social tags, robots and sitemap 404. No custom domain. Head terms are dominated by Monkeytype and keybr. — AUD-SPARK-001

## Open questions
- Does the owner want TurtleType Plus live now, or parked while ClearFrame is the focus? (TT-002)
- Custom domain wanted? UNKNOWN - source needed: owner. A domain purchase needs approval (TT-006).

## Evidence
- Repo: https://github.com/ryanmhopkins/turtletype (commits a41da13b, 8c336abb, d1156ace, 53ff48a5)
- Vercel MCP: `get_project`, `get_deployment`, `filter_project_envs` (names only)
- HTTP: https://turtletype-henna.vercel.app → 200 (2026-10-24)
