# Project registry

Last verified: **2026-10-24** (Atlas, via GitHub MCP, Vercel MCP, Polar MCP, HTTP checks). Times America/New_York (ET).

| ID | Name | Repo | Live URL | Vercel project | Stack | Monetization | Stage | Owner role | Health (evidence) | Last verified |
|---|---|---|---|---|---|---|---|---|---|---|
| CLEARFRAME | ClearFrame | [ryanmhopkins/clearframe](https://github.com/ryanmhopkins/clearframe) (public) | https://getclearframe.app | `clearframe` (`prj_suSuE8nujIW6XlEsd9Y696VA6q16`) | Static HTML/JS + WASM ExifTool (in-browser); Vercel serverless `api/` for Pro sign-in; Polar; Resend | Free (no account) + Pro **$15 one-time** (Polar; code LAUNCH9 $6 off) | Launch, pre-revenue | Atlas (focus product) | **Amber** — prod READY `main` 24092e31 at 2026-10-24 22:11 ET, 6/12 functions (PR #2 deploy had ERROR on the function limit); `/` and `/signin` HTTP 200 (~22:46 ET); Polar org `created`, details not submitted (possible P1-risk); 0 orders, 3 checkouts started, 0 completed; `/contact` does not show support@getclearframe.app | 2026-10-24 |
| TURTLETYPE | TurtleType | [ryanmhopkins/turtletype](https://github.com/ryanmhopkins/turtletype) (private) | https://turtletype-henna.vercel.app | `turtletype` (`prj_EbSYep99cG9hN30a3HBb9FTlu4sJ`) | Static JS (esbuild) + Vercel function `api/results.js`; Neon Postgres + Neon Auth; RevenueCat Web | Free (local, last 20 results) + Plus **$10/year** (RevenueCat) — **checkout not live** | Built / beta, pre-revenue | Atlas (maintain) | **Amber** — prod READY `main` 53ff48a5 at 2026-10-24 20:33 ET; HTTP 200; `REVENUECAT_WEB_PUBLIC_KEY` absent, so signed-in `/api/results` returns 503 (401 without a session). TT-001 review: approach sound. Revenue UNKNOWN | 2026-10-24 |
| GEOHOOPS | GeoHoops | [ryanmhopkins/geohoops](https://github.com/ryanmhopkins/geohoops) (private) — confirmed by Vercel deployment git metadata | https://geohoops.vercel.app | `geohoops` (`prj_U8Zsb2kshsn3zYfyiDmxnwHRbmr2`) | Next.js 16.0.10 / React 19, d3-geo map; Supabase (Postgres, RLS) | None (free, no account) | MVP live, secondary | Atlas (secondary) | **Amber** — prod READY `main` 5cd72bdc at 2026-09-29 09:27 ET; `/` and `/api/game` HTTP 200, mode `live`, total 0; next@16.0.10 has critical advisories fixed from 16.4.1 (feature use UNKNOWN); no CI; thin question bank | 2026-10-24 |

Usage, traffic, and visitors for all three: **UNKNOWN - source needed: analytics** (none found; see [operations/integrations.md](../operations/integrations.md)). ClearFrame Polar revenue to date: $0 (0 orders, 3 checkouts started, 0 completed, test mode). TurtleType revenue: UNKNOWN (no RevenueCat connector). Hosting spend: UNKNOWN.

## Strategic priorities (max 3 per project)
| Project | # | Priority | Backlog IDs |
|---|---|---|---|
| CLEARFRAME | 1 | Turn on live payments and prove the paid path (Polar org → test purchase → magic-link sign-in) | CF-001, CF-002, CF-003 |
| CLEARFRAME | 2 | Measurement: analytics tool + Search Console | CF-004, CF-006 |
| CLEARFRAME | 3 | SEO basics | CF-009 |
| TURTLETYPE | 1 | RevenueCat web key and TT-001 hardening, then Plus go-live or park | TT-002, TT-005 |
| TURTLETYPE | 2 | Measurement baseline | TT-003 |
| GEOHOOPS | 1 | Upgrade Next.js to latest 16.4.x (draft PR only) | GH-005 |
| GEOHOOPS | 2 | Content depth before sharing broadly (question bank) | GH-001 |
| GEOHOOPS | 3 | Measurement baseline for audience building | GH-002 |

Recommendation: **invest** in CLEARFRAME; **maintain** TURTLETYPE (no new features until the billing decision); **maintain** GEOHOOPS. The Next.js upgrade (GH-005) is maintenance, and it stays a draft PR until approved.
