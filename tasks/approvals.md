# Approvals

Single list of items that need the owner's explicit approval. Atlas adds items; only the owner approves. Specialists never act on an item until it is marked `approved` here **and** the owner confirmed in chat.

Canonical path: `tasks/approvals.md` (D-009).

## Standing rules (require approval every time)
- Production changes: merges to app repos, deploys, env vars, DNS, Vercel/Polar/Cloudflare settings, database migrations
- Spending money (purchases, subscriptions, domain renewals, paid tools)
- Publishing anything public (site copy, posts, emails to lists)
- Contacting customers or third parties; auto-sending any reply
- Deleting or pausing accounts, projects or data

## Pending
| ID | Date added | Project | Request | Why | Risk if not done | Backlog | Status |
|---|---|---|---|---|---|---|---|
| A-001 | 2026-10-24 | CLEARFRAME | **Polar org setup and review** — owner completes org details, payout account and submits for review (Polar org status is `created`, details not submitted) | Checkout is test mode until then; only the owner can do it | No revenue possible. Possible P1-risk while the site links to production checkout | CF-001 | pending |
| A-002 | 2026-10-24 | CLEARFRAME | **$9 live test purchase** of ClearFrame Pro with LAUNCH9 (owner's card; refund afterwards: decide) | Proves payment → magic-link sign-in → Pro access in production | Paid path stays unproven | CF-002, CF-003 | pending (after A-001) |
| A-003 | 2026-10-24 | CLEARFRAME | **Any auto-send permission for support FAQ replies** (currently triage drafts only, never sends) | Faster responses once FAQ answers are stable | None now; keep drafts-only | — | pending — default **no auto-send** |
| A-004 | 2026-10-24 | PORTFOLIO | **Cleanup of out-of-scope Vercel projects**: shinobi-archive, clearframe-old, clear-frame, recruitmerge, pricewatcher, claude-workout (see [integrations](../operations/integrations.md#out-of-scope-vercel-projects-cleanup-candidates)) | Reduce clutter and confusion with CLEARFRAME (two old ClearFrame projects) | Accidental edits/deploys to wrong project | OPS-002 | pending |
| A-005 | 2026-10-24 | PORTFOLIO | **Hello Brevard account deletion decision** (newsletter cancelled, D-003; Beehiiv connectors still connected) | Close out cancelled product | Lingering account/data | OPS-003 | pending |
| A-006 | 2026-10-24 | CLEARFRAME | **Search Console** — add DNS TXT record on Cloudflare + grant property access | Search visibility data, sitemap submit. Indexing is UNKNOWN | No search data | CF-006 | pending |
| A-007 | 2026-10-24 | PORTFOLIO | Activate recurring routines ([bots/automation-schedule.md](../bots/automation-schedule.md)) after the first manual cycle | No scheduling until the workflow is tested | Manual effort | OPS-001 | proposed (not yet requested) |
| A-008 | 2026-10-24 | TURTLETYPE | **RevenueCat key + hardening.** Set `REVENUECAT_WEB_PUBLIC_KEY` (live Stripe in RevenueCat) or park Plus. FORGE may open a draft PR for the TT-001 follow-ups (rcb_ prefix check, grace period, hasPlus tests). Redeploy client and server only after the key is set | Signed-in `/api/results` returns 503 until the key exists. TT-001 review: approach is sound; this is configuration, not a code bug | No TurtleType revenue; sandbox-key footgun if a key is set without the check | TT-002, TT-005 | pending |
| A-009 | 2026-10-24 | GEOHOOPS | **Next.js upgrade to latest 16.4.x** — FORGE may open a draft PR only. Do not merge or deploy | next@16.0.10 has critical advisories fixed from 16.4.1 (AUD-FORGE-001). Whether affected features are used is UNKNOWN | Advisories stay on production | GH-005 | pending |
| A-010 | 2026-10-24 | PORTFOLIO | **Minimal CI and branch protection** on clearframe, turtletype, and geohoops | No GitHub Actions. Main is not protected. Merges can go straight to production | Unreviewed changes reach prod | OPS-004 | pending |
| A-011 | 2026-10-24 | CLEARFRAME | **/contact shows support@getclearframe.app** | The page shows a personal email address (commit 9f0a70a9), so some mail bypasses triage | Support misses messages | CF-014 | pending |
| A-012 | 2026-10-24 | PORTFOLIO | **Analytics tool choice** (privacy-compatible; ClearFrame first) | No web analytics on any project. Traffic is UNKNOWN | Launch stays unmeasured | CF-004 | pending |
| A-013 | 2026-10-24 | CLEARFRAME | **SEO basics** — share image, JSON-LD, visible price, Free vs Pro table (drafts only until approved) | Those gaps are observed. Indexing is UNKNOWN | Organic acquisition stays weak | CF-009 | pending |
| A-014 | 2026-10-24 | CLEARFRAME | **Public Pro code decision** — keep or remove readable Pro source (`api/pro/files/_pro.js`, `_pro-worker.mjs`) | Paid code is in the public repo. Only the served copy is gated | Business-model exposure continues by default | CF-015 | pending |
| A-015 | 2026-10-24 | CLEARFRAME | **Domain auto-renew** for getclearframe.app (currently off; lapses ~Oct 2027; renewal price $14.20) | Avoid a lapse | Domain can expire | CF-012 | pending |
| A-016 | 2026-10-24 | PORTFOLIO | **Uptime and error monitoring** for all three projects (ClearFrame sign-in path first) | None exists. Hobby logs last about 1 hour. Spend is UNKNOWN and is a separate gap (OPS-005) | Outages show up only if someone looks | CF-008 | pending |

## Resolved
| ID | Date | Decision | By |
|---|---|---|---|
| — | — | — | — |
