# Project registry

Last verified: **2026-10-24** (Atlas, via GitHub MCP, Vercel MCP, Polar MCP, HTTP checks). Times America/New_York (ET).

| ID | Name | Repo | Live URL | Vercel project | Stack | Monetization | Stage | Owner role | Health (evidence) | Last verified |
|---|---|---|---|---|---|---|---|---|---|---|
| CLEARFRAME | ClearFrame | [ryanmhopkins/clearframe](https://github.com/ryanmhopkins/clearframe) (public) | https://getclearframe.app | `clearframe` (`prj_suSuE8nujIW6XlEsd9Y696VA6q16`) | Static HTML/JS + WASM ExifTool (in-browser); Vercel serverless `api/` for Pro sign-in; Polar; Resend | Free (no account) + Pro **$15 one-time** (Polar; code LAUNCH9 $6 off) | Launch, pre-revenue | Atlas (focus product) | **Amber** — prod deploy `dpl_6NyDmnnfiCXmmshKaBkj4u5jX7kC` READY on `main` 24092e31 (Vercel MCP); `/` and `/signin` HTTP 200 (curl 2026-10-24 22:40 ET); Polar org status `created`, `details_submitted_at` null → checkout not live; **0 orders** (Polar MCP `/v1/orders`) | 2026-10-24 |
| TURTLETYPE | TurtleType | [ryanmhopkins/turtletype](https://github.com/ryanmhopkins/turtletype) (private) | https://turtletype-henna.vercel.app | `turtletype` (`prj_EbSYep99cG9hN30a3HBb9FTlu4sJ`) | Static JS (esbuild) + Vercel function `api/results.js`; Neon Postgres + Neon Auth; RevenueCat Web | Free (local, last 20 results) + Plus **$10/year** (RevenueCat) — **checkout not live** | Built / beta, pre-revenue | Atlas (maintain) | **Amber** — prod deploy `dpl_yjzGtDG9WaNAV5ev6mvZBAFkiXyR` READY on `main` 53ff48a5 (Vercel MCP); HTTP 200; `REVENUECAT_WEB_PUBLIC_KEY` absent from Vercel env (Vercel MCP env names) so app shows "checkout opening soon" (src/app.js) | 2026-10-24 |
| GEOHOOPS | GeoHoops | [ryanmhopkins/geohoops](https://github.com/ryanmhopkins/geohoops) (private) — confirmed by Vercel deployment git metadata | https://geohoops.vercel.app | `geohoops` (`prj_U8Zsb2kshsn3zYfyiDmxnwHRbmr2`) | Next.js 16 / React 19, d3-geo map; Supabase (Postgres, RLS) | None (free, no account) | MVP live, secondary | Atlas (secondary) | **Green (availability)** — prod deploy `dpl_D4EbUkwfwxZGcJEuZ6BhTJaC2mg5` READY on `main` 5cd72bdc (2026-09-29, Vercel MCP); `/` and `/api/game` HTTP 200, API reports `"mode":"live"` (curl 2026-10-24); content bank thin (README) | 2026-10-24 |

Usage, traffic, visitors and revenue for all three: **UNKNOWN - source needed: analytics** (no analytics found in any repo; see [operations/integrations.md](../operations/integrations.md)). ClearFrame revenue to date: $0 (0 Polar orders, test mode).

## Strategic priorities (max 3 per project)
| Project | # | Priority | Backlog IDs |
|---|---|---|---|
| CLEARFRAME | 1 | Turn on live payments and prove the paid path (Polar live → $9 test purchase → magic-link sign-in → Pro dashboard) | CF-001, CF-002, CF-003 |
| CLEARFRAME | 2 | Measurement: privacy-compatible analytics + Search Console | CF-004, CF-005, CF-006 |
| CLEARFRAME | 3 | Organic acquisition: SEO landing pages | CF-009 |
| TURTLETYPE | 1 | Decide and (if approved) enable Plus billing safely | TT-001, TT-002 |
| TURTLETYPE | 2 | Measurement baseline | TT-003 |
| GEOHOOPS | 1 | Content depth before sharing broadly (question bank) | GH-001 |
| GEOHOOPS | 2 | Measurement baseline for audience building | GH-002 |

Recommendation: **invest** in CLEARFRAME; **maintain** TURTLETYPE (no new features until billing decision); **maintain/low effort** GEOHOOPS.
