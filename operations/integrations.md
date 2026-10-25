# Integrations

Verified 2026-10-24 by Atlas, then updated the same day from AUD-FORGE-001, AUD-GUARD-001, AUD-PULSE-001, and AUD-SPARK-001. Env vars listed by **name only**. "Connected" means Atlas has a working read connector or the integration is confirmed in project config.

## Status per project
| Integration | CLEARFRAME | TURTLETYPE | GEOHOOPS | Atlas access | Source |
|---|---|---|---|---|---|
| GitHub | ✅ ryanmhopkins/clearframe (public) | ✅ ryanmhopkins/turtletype (private) | ✅ ryanmhopkins/geohoops (private) | read (GitHub MCP) | GitHub MCP |
| CI / branch protection | ❌ no Actions; main not protected | ❌ same | ❌ same | read | AUD-FORGE-001. Sole collaborator is the repo admin |
| Vercel hosting | ✅ `clearframe` | ✅ `turtletype` | ✅ `geohoops` | read (Vercel MCP) | Vercel MCP `get_project`. Prod READY on the dates in the project profiles |
| Vercel deployment protection | SSO on all except custom domains | same | same | read | Vercel MCP |
| Custom domain | ✅ https://getclearframe.app, www | ❌ (vercel.app only) | ❌ (vercel.app only) | — | Vercel MCP. getclearframe.app is **not** proxied by Cloudflare, so there are no Cloudflare analytics |
| Cloudflare (registrar/DNS) | ✅ getclearframe.app (owner brief). Auto-renew **off** (lapses ~Oct 2027) | — | — | read (Cloudflare MCP, whoami OK; zone not read) | Cloudflare MCP; AUD-GUARD-001 |
| Payments | Polar — **test mode** (org `created`, details not submitted). 0 orders, $0, 0 subscriptions, 3 checkouts started, 0 completed, 0 customers, 1 product ($15 one-time). Site links to production checkout | RevenueCat in code — **not configured** (`REVENUECAT_WEB_PUBLIC_KEY` absent). `/api/results` 503 when signed in | none | Polar: read (Polar MCP). RevenueCat: ❌ no connector. Stripe: ❌ needs auth | Polar MCP; AUD-PULSE-001; Vercel env names |
| Email (transactional) | Resend (env `EMAIL_API_KEY`, `EMAIL_FROM`). SPF includes Cloudflare, DMARC p=none, Resend DKIM exists. Domain verification: UNKNOWN - source needed: Resend dashboard | Neon Auth handles auth email (assumed; UNKNOWN - source needed: Neon Auth config) | none | ❌ no Resend connector | repo + Vercel env names; AUD-GUARD-001 |
| Auth | Magic link + signed session (`SESSION_SECRET`). Auth store: UNKNOWN - source needed: a readable user store. Live sign-in not verified | Neon Auth | anonymous cookie | — | READMEs; AUD-PULSE-001; AUD-FORGE-001 |
| Database | none (stateless; Polar is source of truth) | Neon Postgres (Vercel integration). ❌ no Neon connector | Supabase `geohoops` (`SUPABASE_URL`, `SUPABASE_SECRET_KEY`). ❌ connector needs auth | neither connector works | Vercel env names; AUD-PULSE-001 |
| Support inbox | support@getclearframe.app → clearframe-desk@mail.grokbot.com. Forwarding **verified** 2026-10-24 22:00 ET. `/contact` still shows a personal address (commit 9f0a70a9), not support@. Triage drafts only; a 22:03 outbound reply's cause is UNKNOWN | none | none | inbox exists (ListEmailInboxes) | AUD-GUARD-001 |
| Analytics | ❌ none (no script; CSP blocks third parties) | ❌ none | ❌ none | Vercel Web Analytics toggle: UNKNOWN - source needed: Vercel dashboard (not exposed by MCP) | repo search; AUD-PULSE-001 |
| Search Console | ❌ indexing UNKNOWN | ❌ | ❌ | ❌ no connector | AUD-SPARK-001 |
| Uptime monitoring | ❌ | ❌ | ❌ | ad-hoc HTTP checks only. All three returned 200 ~22:46 ET | AUD-GUARD-001 |
| Error monitoring | ❌ (Vercel logs only, Hobby ~1h) | ❌ | ❌ | Vercel runtime logs via MCP | AUD-GUARD-001 |
| Cost feed | ❌ spend UNKNOWN | ❌ spend UNKNOWN | ❌ spend UNKNOWN | no billing read | AUD-PULSE-001; AUD-GUARD-001 |
| Social / X | UNKNOWN - source needed: which accounts map to which project | same | same | X connector present | connector list |

Other connectors available to Atlas (not mapped to a project): Gmail, Google Drive, Google Calendar, Notion, Beehiiv (incl. Hello Brevard — cancelled, D-003), Zernio, Firebase.

## Metrics still missing (AUD-PULSE-001)
Only measured billing source: Polar for CLEARFRAME, figures in the payments row above. Everything else is UNKNOWN, not zero.

Gaps, in the order Pulse ranked them: (1) no web analytics, (2) no readable user store, (3) no TurtleType billing, (4) no cost feed, (5) no ClearFrame funnel events beyond the Polar checkout counts, (6) registry URL drift — ClearFrame's live URL is https://getclearframe.app.

Minimum metrics once a source exists:
- CLEARFRAME: visitors, source, checkout start/completion, orders, revenue, refunds
- TURTLETYPE: visitors, signups, 7-day active, then paid conversion and MRR
- GEOHOOPS: visitors, daily active, 7-day and 30-day retention

## Missing integrations (ranked by need)
1. **Analytics** — CLEARFRAME first (privacy-compatible, same-origin to fit CSP), then TURTLETYPE, GEOHOOPS (CF-004, TT-003, GH-002)
2. **Google Search Console** — CLEARFRAME (CF-006). DNS change is the owner's
3. **Uptime and error monitoring** — all three; ClearFrame sign-in path first (CF-008)
4. **Cost feed** — spend is UNKNOWN on all three (OPS-005)
5. **RevenueCat connector + `REVENUECAT_WEB_PUBLIC_KEY`** — TURTLETYPE (TT-002). Stripe connector needs auth
6. **Supabase (needs auth) and Neon (no connector)** — GEOHOOPS question count, TURTLETYPE results
7. **CI and branch protection** — all three repos (OPS-004)
8. **Resend delivery visibility** — CLEARFRAME magic links
9. **Social/X account mapping** — GEOHOOPS audience building (GH-003). Mapping is UNKNOWN

## Out-of-scope Vercel projects (cleanup candidates)
Listed once, not managed by Atlas. Cleanup needs the owner's approval (A-004 / OPS-002). Source: Vercel MCP `list_projects`, team `team_Eka6MeEAws2pIq1MxtBmRDWA`, 2026-10-24.

| Vercel project | Project ID | Note |
|---|---|---|
| shinobi-archive | prj_Ypj7Yd7IxBOGAmDMNAg0F9fTT4uK | not in portfolio |
| clearframe-old | prj_LcUwWrxb5OMytjNxylbXlzCN5yXs | old ClearFrame — confusion risk with CLEARFRAME |
| clear-frame | prj_fLnkf6AjGqk7qAeSrX004Qep0iT2 | old ClearFrame — confusion risk with CLEARFRAME |
| recruitmerge | prj_W2nT8SLkR8DDhdJSTRB8ZjDmOSmk | not in portfolio |
| pricewatcher | prj_WQaEMjbCIlN01L4fE09fGWb2xTgA | not in portfolio |
| claude-workout | prj_ebgMirxLU7VykQ1fToMj0bcDTiAh | not in portfolio |
