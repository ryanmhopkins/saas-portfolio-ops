# ClearFrame (CLEARFRAME)

**Status:** Focus product · Stage: launch, pre-revenue · Health: Amber · Last verified 2026-10-24

## What it is
On-device (in-browser) photo metadata scanner and selective cleaner for JPEG, PNG, WebP, GIF, HEIC/HEIF, AVIF, TIFF; Pro adds RAW (DNG, CR2, NEF, ARW), folder cleaning and presets. Photo bytes are not uploaded. — [README](https://github.com/ryanmhopkins/clearframe/blob/main/README.md)

## Audience
People who share photos and want location/camera/author metadata removed privately. Specific segments: UNKNOWN - source needed: customer research / analytics.

## Stack
- Static HTML/CSS/JS, self-hosted fonts, exifr, JSZip, ExifTool WASM (~25 MB, loaded on demand) — README, repo tree
- Vercel serverless `api/auth/*`, `api/pro/module.js`; helpers in `server-lib/` (moved out of `api/` to stay under the Hobby 12-function limit, [PR #3](https://github.com/ryanmhopkins/clearframe/pull/3))
- Strict CSP (`connect-src 'self'`, `script-src 'self'`) — [vercel.json](https://github.com/ryanmhopkins/clearframe/blob/main/vercel.json)
- Tests: `node --test` (metadata, auth, UI, trust surface)

## Deploy
- Vercel project `clearframe` (`prj_suSuE8nujIW6XlEsd9Y696VA6q16`), team `team_Eka6MeEAws2pIq1MxtBmRDWA`, Hobby plan (Ryan brief) — Vercel MCP `get_project`
- Domains: getclearframe.app, www.getclearframe.app, clear-frame-app.vercel.app (+ Vercel aliases) — Vercel MCP
- Latest production: `dpl_6NyDmnnfiCXmmshKaBkj4u5jX7kC` READY, `main` @ 24092e31, created 2026-10-24 22:11 ET — Vercel MCP `get_deployment`
- Domain getclearframe.app bought 2026-10-24 via Cloudflare, $8.20/yr, auto-renew **off**, renews at $14.20 — Ryan brief (registrar record not read)

## Integrations
Polar (payments), Resend (magic-link email from login@getclearframe.app), Cloudflare (registrar/DNS), support inbox (support@getclearframe.app → clearframe-desk@mail.grokbot.com; triage routine drafts replies, never auto-sends). Vercel env var **names** present: `EMAIL_API_KEY`, `EMAIL_FROM`, `POLAR_ACCESS_TOKEN`, `POLAR_ORG_ID`, `POLAR_PRODUCT_ID`, `SESSION_SECRET`, `SITE_URL` (Vercel MCP `filter_project_envs`, names only). Analytics: **none**. Details: [operations/integrations.md](../operations/integrations.md).

## Revenue model
- Free: full standard-format cleaning, no account, page never calls `/api` — README
- Pro: **$15 one-time** (Polar product "ClearFrame Pro", fixed 1500 USD cents, not recurring); discount **LAUNCH9** (fixed, $6 off → $9), 0 redemptions — Polar MCP
- Checkout: public Polar link on home page (`buy.polar.sh/...`) — [index.html](https://github.com/ryanmhopkins/clearframe/blob/main/index.html)
- Paid users sign in by passwordless email magic link (no license keys); server checks for a paid Polar order before emailing the link — README, [PR #2](https://github.com/ryanmhopkins/clearframe/pull/2)
- Orders to date: **0** (Polar MCP `GET /v1/orders`, 2026-10-24). MRR/revenue: $0.

## Known risks
1. **BLOCKER:** Polar org `clearframe` status `created`, `details_submitted_at` null → payments not live (test mode). Ryan must complete org details, payout and review. — Polar MCP
2. Paid path unproven end-to-end in production (no real order; sign-in email delivery untested live).
3. No analytics, no Search Console, no uptime monitoring → health and growth are blind.
4. Hobby plan 12-function limit: new `api/` files can break deploys (PR #3 context).
5. Legal pages (privacy, terms, contact) are plain drafts, not legal advice; must not include Ryan's personal name or other sites (Ryan brief).
6. Domain auto-renew off → domain lapses ~Oct 2027 unless renewed (Ryan brief).
7. Any analytics must stay consistent with privacy claims in `how-privacy-works.html` / CSP.

## Open questions
- When will Ryan finish Polar org setup/review?
- Should the $9 test purchase be refunded afterwards?
- Which analytics (if any) fits the privacy promise — Vercel Web Analytics (same-origin) vs none?
- "Folder mode" idea vs existing Pro folder cleaning — what is missing? UNKNOWN - source needed: Ryan.
- Is Resend domain verification for getclearframe.app complete? UNKNOWN - source needed: Resend dashboard.

## Later ideas (not prioritized beyond backlog)
Location-only removal, preset improvements, SEO landing pages, cookieless analytics, folder mode, HEIC/RAW progress bar.

## Evidence
- Repo: https://github.com/ryanmhopkins/clearframe · PRs [#1](https://github.com/ryanmhopkins/clearframe/pull/1), [#2](https://github.com/ryanmhopkins/clearframe/pull/2), [#3](https://github.com/ryanmhopkins/clearframe/pull/3) (all merged 2026-10-24 ET)
- Vercel MCP: `get_project`, `get_deployment`, `filter_project_envs` (names only)
- Polar MCP: organization, product, orders, discounts (read-only)
- HTTP: https://getclearframe.app and /signin → 200 (2026-10-24 22:40 ET)
