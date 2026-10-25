# ClearFrame (CLEARFRAME)

**Status:** Focus product · Stage: launch, pre-revenue · Health: Amber (possible P1-risk: Polar org unsubmitted) · Last verified 2026-10-24

## What it is
On-device (in-browser) photo metadata scanner and selective cleaner for JPEG, PNG, WebP, GIF, HEIC/HEIF, AVIF, TIFF; Pro adds RAW (DNG, CR2, NEF, ARW), folder cleaning and presets. Photo bytes are not uploaded. — [README](https://github.com/ryanmhopkins/clearframe/blob/main/README.md)

## Audience
People who share photos and want location/camera/author metadata removed privately. Specific segments: UNKNOWN - source needed: customer research / analytics.

## Stack
- Static HTML/CSS/JS, self-hosted fonts, exifr, JSZip, ExifTool WASM (~25 MB, loaded on demand) — README, repo tree
- Vercel serverless `api/auth/*`, `api/pro/module.js`; helpers in `server-lib/` (moved out of `api/` to stay under the Hobby 12-function limit, [PR #3](https://github.com/ryanmhopkins/clearframe/pull/3))
- Strict CSP (`connect-src 'self'`, `script-src 'self'`) — [vercel.json](https://github.com/ryanmhopkins/clearframe/blob/main/vercel.json)
- Tests: `node --test tests/*.test.js`. Nothing runs in CI. "35 passing" is the author's claim and is unverified (AUD-FORGE-001)

## Deploy
- Vercel project `clearframe` (`prj_suSuE8nujIW6XlEsd9Y696VA6q16`), team `team_Eka6MeEAws2pIq1MxtBmRDWA`, Hobby plan (owner brief) — Vercel MCP `get_project`
- Domains: https://getclearframe.app, www.getclearframe.app (+ Vercel aliases) — Vercel MCP
- Latest production: `dpl_6NyDmnnfiCXmmshKaBkj4u5jX7kC` READY, `main` @ 24092e31 (PR #3), created 2026-10-24 22:11 ET — Vercel MCP `get_deployment`. Now 6/12 serverless functions. An earlier PR #2 deploy was ERROR (exceeded the serverless function limit) — AUD-FORGE-001
- Domain getclearframe.app bought 2026-10-24 via Cloudflare, $8.20/yr, auto-renew **off**, renews at $14.20, lapses ~Oct 2027 — owner brief; AUD-GUARD-001 (registrar record not read)

## Integrations
Polar (payments, test mode), Resend (magic-link email from login@getclearframe.app), Cloudflare (registrar/DNS; domain is not proxied, so no Cloudflare analytics). Support: support@getclearframe.app → clearframe-desk@mail.grokbot.com, forwarding verified 2026-10-24 22:00 ET. `/contact` does not show that address (commit 9f0a70a9). No CI, no branch protection, no analytics, no Search Console, no uptime or error monitor, no cost feed. Vercel env var **names** present: `EMAIL_API_KEY`, `EMAIL_FROM`, `POLAR_ACCESS_TOKEN`, `POLAR_ORG_ID`, `POLAR_PRODUCT_ID`, `SESSION_SECRET`, `SITE_URL` (Vercel MCP `filter_project_envs`, names only). Details: [operations/integrations.md](../operations/integrations.md).

## Revenue model
- Free: full standard-format cleaning, no account, page never calls `/api` — README
- Pro: **$15 one-time** (Polar product "ClearFrame Pro", fixed 1500 USD cents, not recurring); discount **LAUNCH9** (fixed, $6 off → $9), 0 redemptions — Polar MCP
- Checkout: public Polar link on home page (`buy.polar.sh/...`) — [index.html](https://github.com/ryanmhopkins/clearframe/blob/main/index.html)
- Paid users sign in by passwordless email magic link (no license keys); server checks for a paid Polar order before emailing the link — README, [PR #2](https://github.com/ryanmhopkins/clearframe/pull/2)
- Orders to date: **0**. Revenue **$0**. Subscriptions 0. Checkouts started 3, completed 0. Customers 0. One product, $15 one-time (AUD-PULSE-001, 2026-10-24). Other traffic figures: UNKNOWN.

## Known risks
1. **Possible P1-risk (not a verified incident):** Polar org `clearframe` status `created`, details not submitted, 0 orders. The site links to production checkout. — Polar MCP; AUD-GUARD-001
2. Payments and magic-link sign-in are not live-verified. — AUD-FORGE-001
3. `/contact` shows a personal email address instead of support@getclearframe.app (commit 9f0a70a9), so some mail bypasses triage. support@ forwarding itself worked at 22:00 ET. An outbound reply at 22:03 ET has an UNKNOWN cause. — AUD-GUARD-001
4. Pro source is readable in the public repo (`api/pro/files/_pro.js`, `_pro-worker.mjs`). Only the served copy is gated. Decision: CF-015. — AUD-FORGE-001
5. No CI, no automatic tests, main not protected. Merges go straight to production. — AUD-FORGE-001
6. No analytics, Search Console, uptime monitor, error monitor, or cost feed. Spend UNKNOWN. Hobby logs about 1 hour. Indexing UNKNOWN. — AUD-GUARD-001, AUD-PULSE-001, AUD-SPARK-001
7. Domain auto-renew is off (lapses ~Oct 2027, renewal $14.20). — AUD-GUARD-001
8. Hobby 12-function limit. PR #2 deploy ERROR on that limit; production is now 6/12. — AUD-FORGE-001
9. Homepage does not show the price. Social tags exist; no share image; no JSON-LD. Name collision with an unrelated iOS app "ClearFrame: Photo Cleaner" (naming is the owner's call). — AUD-SPARK-001
10. SPF includes Cloudflare, DMARC p=none, Resend DKIM exists. — AUD-GUARD-001
11. Legal pages are drafts, not legal advice, and must not name the owner or the owner's other sites. Analytics must stay consistent with `how-privacy-works.html` and the CSP.

## Open questions
- When will the owner finish Polar org setup and review?
- Should the $9 test purchase be refunded afterwards?
- Which analytics tool, if any, fits the privacy promise? Not chosen (CF-004).
- Should the readable Pro source stay in the public repo? (CF-015)
- Turn domain auto-renew on? (CF-012)
- "Folder mode" idea vs existing Pro folder cleaning — what is missing? UNKNOWN - source needed: owner.
- Is Resend domain verification for getclearframe.app complete? UNKNOWN - source needed: Resend dashboard.

## Later ideas (not prioritized beyond backlog)
Location-only removal, preset improvements, SEO landing pages, cookieless analytics, folder mode, HEIC/RAW progress bar.

## Evidence
- Repo: https://github.com/ryanmhopkins/clearframe · PRs [#1](https://github.com/ryanmhopkins/clearframe/pull/1), [#2](https://github.com/ryanmhopkins/clearframe/pull/2), [#3](https://github.com/ryanmhopkins/clearframe/pull/3) (all merged 2026-10-24 ET)
- Vercel MCP: `get_project`, `get_deployment`, `filter_project_envs` (names only)
- Polar MCP: organization, product, orders, discounts (read-only)
- HTTP: https://getclearframe.app and /signin → 200 (2026-10-24 22:40 ET; again ~22:46 ET, AUD-GUARD-001)
