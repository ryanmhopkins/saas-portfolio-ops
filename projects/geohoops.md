# GeoHoops (GEOHOOPS)

**Status:** Secondary (audience building) · Stage: MVP live · Health: Amber (HTTP 200; critical Next.js advisories, feature use UNKNOWN) · Last verified 2026-10-24

## What it is
Mobile-first daily basketball geography game: five map guesses per UTC day, 200 points each, 1,000 max, no account (anonymous HttpOnly cookie). Questions span player origins and iconic moments. — [README](https://github.com/ryanmhopkins/geohoops/blob/main/README.md), [broaden_trivia_bank migration](https://github.com/ryanmhopkins/geohoops/blob/main/supabase/migrations/20260928171500_broaden_trivia_bank.sql)

## Repo identity
**ryanmhopkins/geohoops** (private). Confirmed: latest Vercel production deployment git metadata `githubOrg: ryanmhopkins`, `githubRepo: geohoops` (Vercel MCP `get_deployment dpl_D4EbUkwfwxZGcJEuZ6BhTJaC2mg5`), and GitHub repo search (homepage https://geohoops.vercel.app).

## Audience
NBA/basketball fans who like daily puzzle games (Wordle-style). Size: UNKNOWN - source needed: analytics.

## Stack
Next.js 16.0.10, React 19, TypeScript, d3-geo + topojson world map, Supabase (`@supabase/supabase-js`), API routes `app/api/game`, `app/api/guess` — [package.json](https://github.com/ryanmhopkins/geohoops/blob/main/package.json). No tests or lint script (typecheck only). No CI. Supabase project `geohoops`, RLS on, answers server-only — README. Vercel env names: `SUPABASE_URL`, `SUPABASE_SECRET_KEY` (names only). Supabase connector needs auth.

## Deploy
- Vercel project `geohoops` (`prj_U8Zsb2kshsn3zYfyiDmxnwHRbmr2`), Next.js, created 2026-09-28 — Vercel MCP
- Latest production: `dpl_D4EbUkwfwxZGcJEuZ6BhTJaC2mg5` READY, `main` @ 5cd72bdc "Add playful court-inspired visual theme", 2026-09-29 09:27 ET — Vercel MCP; AUD-FORGE-001
- Live: https://geohoops.vercel.app (HTTP 200 at ~22:46 ET). `/api/game` returned 200, `"mode":"live"`, total 0 (AUD-GUARD-001, 2026-10-24). No custom domain
- 19 commits (2026-09-28 → 09-29), 0 issues, 0 PRs — GitHub MCP

## Integrations
GitHub, Vercel, Supabase (env present; connector **needs auth**). No CI or branch protection. Analytics: **none**. No uptime monitor, error monitor, or cost feed (spend UNKNOWN). No support intake. Social/X account for GeoHoops: UNKNOWN - source needed: owner.

## Revenue model
None (free, no account). The owner treats it as audience building, not revenue.

## Known risks
1. next@16.0.10 has critical advisories GHSA-673q-mjm6-r5xr (use cache RCE) and GHSA-2464-fhr4-w9xw (image optimizer SVG RCE), fixed from 16.4.1, plus a high-severity Server Actions DoS. Upgrade target is the latest 16.4.x (GH-005, draft PR only). Whether GeoHoops uses the affected features is UNKNOWN. — AUD-FORGE-001
2. No tests or lint script (typecheck only). No CI or branch protection. No security headers. — AUD-FORGE-001
3. `/api/game` was 200, mode `live`, total 0. Thin question bank (repo seeds about 25; live count UNKNOWN - source needed: Supabase). Dormant since 2026-09-29. No support intake. — AUD-GUARD-001
4. No analytics, uptime monitor, error monitor, or cost feed. Spend UNKNOWN. Audience size UNKNOWN. — AUD-PULSE-001
5. SEO: client-rendered, so crawlers see no content; no share tags; robots and sitemap 404. — AUD-SPARK-001
6. No leaderboard, abuse controls, cross-device identity, or scheduled publishing (README "future work").

## Open questions
- What audience channel should GeoHoops feed? UNKNOWN - source needed: owner.
- Should GeoHoops cross-promote ClearFrame/TurtleType? Decision needed.

## Evidence
- Repo: https://github.com/ryanmhopkins/geohoops
- Vercel MCP: `get_project`, `get_deployment` (git metadata), `filter_project_envs` (names only)
- HTTP: https://geohoops.vercel.app, /api/game → 200 (2026-10-24)
