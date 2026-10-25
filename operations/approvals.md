# Approvals

Single list of items that need Ryan's explicit approval. Atlas adds items; only Ryan approves. Specialists never act on an item until it is marked `approved` here **and** Ryan confirmed in chat.

## Standing rules (require approval every time)
- Production changes: merges to app repos, deploys, env vars, DNS, Vercel/Polar/Cloudflare settings, database migrations
- Spending money (purchases, subscriptions, domain renewals, paid tools)
- Publishing anything public (site copy, posts, emails to lists)
- Contacting customers or third parties; auto-sending any reply
- Deleting or pausing accounts, projects or data

## Pending
| ID | Date added | Project | Request | Why | Risk if not done | Backlog | Status |
|---|---|---|---|---|---|---|---|
| A-001 | 2026-10-24 | CLEARFRAME | **Polar org setup and review** — Ryan completes org details, payout account and submits for review (Polar org status is `created`, details not submitted) | Checkout is test mode until then; only Ryan can do it | No revenue possible | CF-001 | pending (Ryan action) |
| A-002 | 2026-10-24 | CLEARFRAME | **$9 live test purchase** of ClearFrame Pro with LAUNCH9 (Ryan's card; refund afterwards: decide) | Proves payment → magic-link sign-in → Pro access in production | Paid path stays unproven | CF-002, CF-003 | pending (after A-001) |
| A-003 | 2026-10-24 | CLEARFRAME | **Any auto-send permission for support FAQ replies** (currently triage drafts only, never sends) | Faster responses once FAQ answers are stable | None now; keep drafts-only | CF-007 | pending — default **no auto-send** |
| A-004 | 2026-10-24 | PORTFOLIO | **Cleanup of out-of-scope Vercel projects**: shinobi-archive, clearframe-old, clear-frame, recruitmerge, pricewatcher, claude-workout (see [integrations.md](integrations.md#out-of-scope-vercel-projects-cleanup-candidates)) | Reduce clutter and confusion with CLEARFRAME (two old ClearFrame projects) | Accidental edits/deploys to wrong project | OPS-002 | pending |
| A-005 | 2026-10-24 | PORTFOLIO | **Hello Brevard account deletion decision** (newsletter cancelled, D-003; Beehiiv connectors still connected) | Close out cancelled product | Lingering account/data | OPS-003 | pending |
| A-006 | 2026-10-24 | CLEARFRAME | Search Console: add DNS TXT record on Cloudflare + grant property access | Search visibility data, sitemap submit | No search data | CF-006 | proposed |
| A-007 | 2026-10-24 | PORTFOLIO | Activate recurring routines ([bots/automation-schedule.md](../bots/automation-schedule.md)) after the first manual cycle | Ryan: no scheduling until workflow tested | Manual effort | OPS-001 | proposed (not yet requested) |
| A-008 | 2026-10-24 | TURTLETYPE | Plus billing go-live (live Stripe in RevenueCat + set `REVENUECAT_WEB_PUBLIC_KEY`) or park TurtleType Plus | Billing not connected | No TurtleType revenue | TT-002 | proposed |

## Resolved
| ID | Date | Decision | By |
|---|---|---|---|
| — | — | — | — |
