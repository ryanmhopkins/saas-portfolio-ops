# ClearFrame (CLEARFRAME)

**Status:** Focus product · Stage: launch, pre-revenue · Health: Amber (possible P1-risk: Polar org unsubmitted, last checked 2026-10-24; not re-checked 2026-10-25) · Last verified 2026-10-25 for the pricing, entitlement, and production facts below

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
- Vercel project `clearframe` (`prj_suSuE8nujIW6XlEsd9Y696VA6q16`), team `team_Eka6MeEAws2pIq1MxtBmRDWA`, Hobby plan. Ryan kept the current Hobby plan on 2026-10-25 and accepted the known risk that Hobby is non-commercial-use only (D-016) — Vercel MCP `get_project`; Ryan Hopkins in chat, 2026-10-25
- Domains: https://getclearframe.app, www.getclearframe.app (+ Vercel aliases) — Vercel MCP
- Production deploy READY on 61f4c25 (2026-10-25). Ryan approved the merge and the deploy of [PR #10](https://github.com/ryanmhopkins/clearframe/pull/10) (refund and past_due grace entitlement rules, squash 873e5a8) and [PR #9](https://github.com/ryanmhopkins/clearframe/pull/9) (squash 61f4c25). D-019
- Previous production: `dpl_6NyDmnnfiCXmmshKaBkj4u5jX7kC` READY, `main` @ 24092e31 (PR #3), created 2026-10-24 22:11 ET — Vercel MCP `get_deployment`. Then 6/12 serverless functions. An earlier PR #2 deploy was ERROR (exceeded the serverless function limit) — AUD-FORGE-001. Function count on 61f4c25: UNKNOWN - source needed: Vercel deployment for 61f4c25
- Domain getclearframe.app bought 2026-10-24 via Cloudflare, $8.20/yr, auto-renew **off**, renews at $14.20, lapses ~Oct 2027 — owner brief; AUD-GUARD-001 (registrar record not read)

## Integrations
Polar (payments), Resend (magic-link email from login@getclearframe.app), Cloudflare (registrar/DNS; domain is not proxied, so no Cloudflare analytics). Support: support@getclearframe.app → clearframe-desk@mail.grokbot.com, forwarding verified 2026-10-24 22:00 ET. `/contact` does not show that address (commit 9f0a70a9). No CI and no branch protection on clearframe main (still true 2026-10-25, A-010). No Search Console, no uptime or error monitor, no cost feed. Atlas live check 2026-10-25: a PostHog request returned 200; the event name pro_dialog_opened was not confirmed in PostHog Live Events (needs Ryan to look). Polar webhook handlers are still stubs. email.js logs the sign-in link if `EMAIL_API_KEY` is unset; the key is set in production. Vercel env var **names** present: `EMAIL_API_KEY`, `EMAIL_FROM`, `POLAR_ACCESS_TOKEN`, `POLAR_ORG_ID`, `POLAR_PRODUCT_ID`, `SESSION_SECRET`, `SITE_URL` (Vercel MCP `filter_project_envs`, names only, 2026-10-24). Details: [operations/integrations.md](../operations/integrations.md).

## Revenue model
- Free: full standard-format cleaning, no account, page never calls `/api` — README
- Pro: **$29/year** (Polar subscription, product be456dd9-4508-4b3a-a517-60fae3c9747b, no trial). **$15 one-time superseded** (D-006 → D-013, 2026-10-25). Old $15 product archived. 0 license keys had been issued. Changed by Ryan with Codex; [PR #7](https://github.com/ryanmhopkins/clearframe/pull/7) and [PR #8](https://github.com/ryanmhopkins/clearframe/pull/8) merged without review; Atlas reviewed afterward. Ryan Hopkins approved in chat, 2026-10-25
- LAUNCH9 removed ([PR #9](https://github.com/ryanmhopkins/clearframe/pull/9)). 2026-10-24 profile, not a 2026-10-25 count: Polar product "ClearFrame Pro", fixed 1500 USD cents, not recurring; LAUNCH9 fixed, $6 off → $9, 0 redemptions — Polar MCP
- Checkout as of 2026-10-24: public Polar link on the home page (`buy.polar.sh/...`) — [index.html](https://github.com/ryanmhopkins/clearframe/blob/main/index.html). Shipped 2026-10-25 in PR #9: checkout returns to `/signin?subscribed=1`; "Receipts" renamed "Manage subscription"; `/checkout` blocked in robots.txt; rate limit 10 per 15 min per IP
- Paid users sign in by passwordless email magic link (no license keys); server checks for a paid Polar order before emailing the link — README, [PR #2](https://github.com/ryanmhopkins/clearframe/pull/2). PR #10 (squash 873e5a8) shipped refund and past_due grace entitlement rules: a refund removes Pro (any refund, including partial, D-014); failed renewals get a 24-hour grace (D-015)
- Refund policy text approved by Ryan (D-018; Pro subscription terms section in PR #9): 14 days from first purchase, 7 days after a renewal, refunds via Polar, email support@getclearframe.app. Wording says Pro access ends within a day of a refund (access is re-checked about once a day, worst case up to 24h)
- Ryan's own $0 test subscription stays active in Polar for his testing (D-017)
- Orders, revenue, and subscription counts were not re-measured on 2026-10-25. Last Polar counts (AUD-PULSE-001, 2026-10-24): 0 orders, revenue $0, 0 subscriptions, 3 checkouts started, 0 completed, 0 customers. Other traffic figures: UNKNOWN.

## Known risks
1. **Possible P1-risk (not a verified incident):** as of 2026-10-24, Polar org `clearframe` status `created`, details not submitted, 0 orders, and the site linked to production checkout. Not re-checked 2026-10-25. — Polar MCP; AUD-GUARD-001
2. Payments and magic-link sign-in are not live-verified. The 2026-10-25 Atlas checks covered the Pro dialog, terms text, console, and a PostHog request, not the paid sign-in path. — AUD-FORGE-001; Atlas live check 2026-10-25
3. `/contact` shows a personal email address instead of support@getclearframe.app (commit 9f0a70a9), so some mail bypasses triage. support@ forwarding itself worked at 22:00 ET. An outbound reply at 22:03 ET has an UNKNOWN cause. — AUD-GUARD-001
4. Pro source is readable in the public repo (`api/pro/files/_pro.js`, `_pro-worker.mjs`). Only the served copy is gated. Decision: CF-015. — AUD-FORGE-001
5. No CI, no automatic tests, main not protected. Merges go straight to production. Still true for clearframe main on 2026-10-25 (A-010). — AUD-FORGE-001; Ryan Hopkins in chat, 2026-10-25
6. Search Console, uptime monitor, error monitor, and cost feed: still none as of the 2026-10-24 audits. Spend UNKNOWN. Hobby logs about 1 hour. Indexing UNKNOWN. Atlas live check 2026-10-25: PostHog request returned 200; pro_dialog_opened was not confirmed in PostHog Live Events (needs Ryan to look). — AUD-GUARD-001, AUD-PULSE-001, AUD-SPARK-001; Atlas live check 2026-10-25
7. Domain auto-renew is off (lapses ~Oct 2027, renewal $14.20). — AUD-GUARD-001
8. Hobby 12-function limit. PR #2 deploy ERROR on that limit; the 2026-10-24 production deploy was 6/12. Function count on 61f4c25: UNKNOWN - source needed: Vercel deployment for 61f4c25. — AUD-FORGE-001
9. Homepage does not show the price. Social tags exist; no share image; no JSON-LD. Name collision with an unrelated iOS app "ClearFrame: Photo Cleaner" (naming is the owner's call). — AUD-SPARK-001
10. SPF includes Cloudflare, DMARC p=none, Resend DKIM exists. — AUD-GUARD-001
11. Legal pages are drafts, not legal advice, and must not name the owner or the owner's other sites. Analytics must stay consistent with `how-privacy-works.html` and the CSP. On 2026-10-25, terms.html still has six LEGAL REVIEW sentences, including "Polar as merchant of record", and the line "This section is a draft for review" is still visible on the terms page (A-020).
12. Vercel Hobby is non-commercial-use only. Ryan accepted that risk and kept the current Hobby plan (D-016, 2026-10-25).
13. Polar webhook handlers are still stubs (2026-10-25, A-022).
14. Optional Forge hardening, not shipped (A-021): 5s fetch timeout on Polar calls; email.js logs the sign-in link if `EMAIL_API_KEY` is unset (the key is set in production); PR #9 dialog nits.
15. Whether Polar's customer email filter is case-insensitive is unverified. UNKNOWN - source needed: Polar customer email filter (A-023).

## Open questions
- When will the owner finish Polar org setup and review?
- Should the $9 test purchase be refunded afterwards? LAUNCH9 was removed in PR #9 (D-019); A-002 has not been replaced.
- Ryan to look at PostHog Live Events for pro_dialog_opened (not confirmed on the 2026-10-25 Atlas check).
- Legal review of the six LEGAL REVIEW sentences in terms.html, including "Polar as merchant of record", and the visible "This section is a draft for review" line (A-020).
- Whether Polar's customer email filter is case-insensitive. UNKNOWN - source needed: Polar (A-023).
- Which analytics tool, if any, fits the privacy promise? Not chosen (CF-004).
- Should the readable Pro source stay in the public repo? (CF-015)
- Turn domain auto-renew on? (CF-012)
- "Folder mode" idea vs existing Pro folder cleaning — what is missing? UNKNOWN - source needed: owner.
- Is Resend domain verification for getclearframe.app complete? UNKNOWN - source needed: Resend dashboard.

## Later ideas (not prioritized beyond backlog)
Location-only removal, preset improvements, SEO landing pages, cookieless analytics, folder mode, HEIC/RAW progress bar.

## Evidence
- Repo: https://github.com/ryanmhopkins/clearframe · PRs [#1](https://github.com/ryanmhopkins/clearframe/pull/1), [#2](https://github.com/ryanmhopkins/clearframe/pull/2), [#3](https://github.com/ryanmhopkins/clearframe/pull/3) (all merged 2026-10-24 ET); [#7](https://github.com/ryanmhopkins/clearframe/pull/7) and [#8](https://github.com/ryanmhopkins/clearframe/pull/8) (pricing, merged without review; Atlas reviewed afterward); [#9](https://github.com/ryanmhopkins/clearframe/pull/9) (squash 61f4c25) and [#10](https://github.com/ryanmhopkins/clearframe/pull/10) (squash 873e5a8), merge and deploy approved by Ryan Hopkins 2026-10-25. Production deploy READY on 61f4c25
- Atlas live checks 2026-10-25: Pro upgrade dialog opens, terms show the refund text, console clean, PostHog request returned 200; pro_dialog_opened not confirmed in PostHog Live Events
- Vercel MCP: `get_project`, `get_deployment`, `filter_project_envs` (names only)
- Polar MCP: organization, product, orders, discounts (read-only)
- HTTP: https://getclearframe.app and /signin → 200 (2026-10-24 22:40 ET; again ~22:46 ET, AUD-GUARD-001)
