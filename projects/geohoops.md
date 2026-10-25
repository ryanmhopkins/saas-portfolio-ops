# GeoHoops (GEOHOOPS)

**Status:** Secondary (audience building) · Stage: MVP live · Health: Green (availability) · Last verified 2026-10-24

## What it is
Mobile-first daily basketball geography game: five map guesses per UTC day, 200 points each, 1,000 max, no account (anonymous HttpOnly cookie). Questions span player origins and iconic moments. — [README](https://github.com/ryanmhopkins/geohoops/blob/main/README.md), [broaden_trivia_bank migration](https://github.com/ryanmhopkins/geohoops/blob/main/supabase/migrations/20260928171500_broaden_trivia_bank.sql)

## Repo identity
**ryanmhopkins/geohoops** (private). Confirmed: latest Vercel production deployment git metadata `githubOrg: ryanmhopkins`, `githubRepo: geohoops` (Vercel MCP `get_deployment dpl_D4EbUkwfwxZGcJEuZ6BhTJaC2mg5`), and GitHub repo search (homepage https://geohoops.vercel.app).

## Audience
NBA/basketball fans who like daily puzzle games (Wordle-style). Size: UNKNOWN - source needed: analytics.

## Stack
Next.js 16.0.10, React 19, TypeScript, d3-geo + topojson world map, Supabase (`@supabase/supabase-js`), API routes `app/api/game`, `app/api/guess` — [package.json](https://github.com/ryanmhopkins/geohoops/blob/main/package.json). Supabase project `geohoops`, RLS on, answers server-only — README. Vercel env names: `SUPABASE_URL`, `SUPABASE_SECRET_KEY` (names only).

## Deploy
- Vercel project `geohoops` (`prj_U8Zsb2kshsn3zYfyiDmxnwHRbmr2`), Next.js, created 2026-09-28 — Vercel MCP
- Latest production: `dpl_D4EbUkwfwxZGcJEuZ6BhTJaC2mg5` READY, `main` @ 5cd72bdc "Add playful court-inspired visual theme", 2026-09-29 09:27 ET — Vercel MCP
- Live: https://geohoops.vercel.app (HTTP 200; `/api/game` returns `"mode":"live"`, 2026-10-24) — no custom domain
- 19 commits (2026-09-28 → 09-29), 0 issues, 0 PRs — GitHub MCP

## Integrations
GitHub, Vercel, Supabase (env present; no Supabase connector for Atlas). Analytics: **none**. Social/X account for GeoHoops: UNKNOWN - source needed: Ryan.

## Revenue model
None (free, no account). Ryan treats it as audience building, not revenue.

## Known risks
1. Thin content: repo migrations seed ~25 questions; README warns the same places recur until the bank expands. Live DB count UNKNOWN - source needed: Supabase.
2. No analytics → audience-building goal cannot be measured.
3. No leaderboard, abuse controls, cross-device identity or scheduled publishing (README "future work").
4. Dormant since 2026-09-29 (no commits/deploys).

## Open questions
- What audience channel (X, Reddit, newsletter) should GeoHoops feed? UNKNOWN - source needed: Ryan.
- Should GeoHoops cross-promote ClearFrame/TurtleType? Decision needed.

## Evidence
- Repo: https://github.com/ryanmhopkins/geohoops
- Vercel MCP: `get_project`, `get_deployment` (git metadata), `filter_project_envs` (names only)
- HTTP: https://geohoops.vercel.app, /api/game → 200 (2026-10-24)
