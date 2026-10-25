# Integrations

Verified 2026-10-24 by Atlas. Env vars listed by **name only**. "Connected" means Atlas has a working read connector or the integration is confirmed in project config.

## Status per project
| Integration | CLEARFRAME | TURTLETYPE | GEOHOOPS | Atlas access | Source |
|---|---|---|---|---|---|
| GitHub | ✅ ryanmhopkins/clearframe | ✅ ryanmhopkins/turtletype | ✅ ryanmhopkins/geohoops | read (GitHub MCP) | GitHub MCP |
| Vercel hosting | ✅ `clearframe` | ✅ `turtletype` | ✅ `geohoops` | read (Vercel MCP) | Vercel MCP `get_project` |
| Vercel deployment protection | SSO on all except custom domains | same | same | read | Vercel MCP |
| Custom domain | ✅ getclearframe.app, www | ❌ (vercel.app only) | ❌ (vercel.app only) | — | Vercel MCP |
| Cloudflare (registrar/DNS) | ✅ getclearframe.app (Ryan brief) | — | — | read (Cloudflare MCP, whoami OK; zone not read) | Cloudflare MCP |
| Payments | Polar — **test mode** (org `created`, not submitted); 0 orders | RevenueCat in code — **not configured** (`REVENUECAT_WEB_PUBLIC_KEY` absent) | none | Polar: read (Polar MCP); RevenueCat: ❌ no connector | Polar MCP; Vercel env names |
| Email (transactional) | Resend (env `EMAIL_API_KEY`, `EMAIL_FROM`) | Neon Auth handles auth email (assumed; UNKNOWN - source needed: Neon Auth config) | none | ❌ no Resend connector | repo + Vercel env names |
| Auth | Magic link + signed session (`SESSION_SECRET`) | Neon Auth | anonymous cookie | — | READMEs |
| Database | none (stateless; Polar is source of truth) | Neon Postgres (Vercel integration) | Supabase `geohoops` (`SUPABASE_URL`, `SUPABASE_SECRET_KEY`) | ❌ no Neon/Supabase connector | Vercel env names; READMEs |
| Support inbox | support@getclearframe.app → clearframe-desk@mail.grokbot.com (triage drafts only) | none | none | inbox exists (ListEmailInboxes); **forwarding not verified** | Ryan brief; ListEmailInboxes |
| Analytics | ❌ none (no script; CSP blocks third parties) | ❌ none | ❌ none | Vercel Web Analytics toggle: UNKNOWN - source needed: Vercel dashboard (not exposed by MCP) | repo search; Vercel MCP |
| Search Console | ❌ | ❌ | ❌ | ❌ no connector | — |
| Uptime monitoring | ❌ | ❌ | ❌ | ad-hoc curl only | — |
| Error monitoring | ❌ (Vercel logs only) | ❌ | ❌ | Vercel runtime logs via MCP | — |
| Social / X | UNKNOWN - source needed: Ryan (which accounts map to which project) | same | same | X connector present | connector list |

Other connectors available to Atlas (not mapped to a project): Gmail, Google Drive, Google Calendar, Notion, Beehiiv (incl. Hello Brevard — cancelled, D-003), Zernio, Firebase.

## Missing integrations (ranked by need)
1. **Analytics** — CLEARFRAME first (privacy-compatible, same-origin to fit CSP), then TURTLETYPE, GEOHOOPS (CF-004/CF-005, TT-003, GH-002)
2. **Google Search Console** — CLEARFRAME (CF-006)
3. **Uptime monitoring** — all three, ClearFrame sign-in path first (CF-008)
4. **Resend delivery visibility** (connector or dashboard access) — CLEARFRAME magic links
5. **RevenueCat + live Stripe** — TURTLETYPE billing (TT-002)
6. **Error monitoring** — all three
7. **Supabase / Neon read access** — GEOHOOPS question count, TURTLETYPE results
8. **Social/X account mapping** — GEOHOOPS audience building (GH-003)

## Out-of-scope Vercel projects (cleanup candidates)
Listed once, not managed by Atlas. Cleanup needs Ryan's approval (A-004 / OPS-002). Source: Vercel MCP `list_projects`, team `team_Eka6MeEAws2pIq1MxtBmRDWA`, 2026-10-24.

| Vercel project | Project ID | Note |
|---|---|---|
| shinobi-archive | prj_Ypj7Yd7IxBOGAmDMNAg0F9fTT4uK | not in portfolio |
| clearframe-old | prj_LcUwWrxb5OMytjNxylbXlzCN5yXs | old ClearFrame — confusion risk with CLEARFRAME |
| clear-frame | prj_fLnkf6AjGqk7qAeSrX004Qep0iT2 | old ClearFrame — confusion risk with CLEARFRAME |
| recruitmerge | prj_W2nT8SLkR8DDhdJSTRB8ZjDmOSmk | not in portfolio |
| pricewatcher | prj_WQaEMjbCIlN01L4fE09fGWb2xTgA | not in portfolio |
| claude-workout | prj_ebgMirxLU7VykQ1fToMj0bcDTiAh | not in portfolio |
