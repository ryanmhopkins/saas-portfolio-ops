# Backlog

**Scoring:** Impact, Urgency, Confidence, Effort each 1–5 (Effort 5 = largest). Priority = (I × U × C) / E, rounded to 1 decimal; sorted high → low. Security incidents and production outages override scores. Limits: max 3 active strategic priorities per project; max 2 `active` tasks per specialist (others `queued`). Blocked/awaiting-approval items do not count toward WIP. Last updated 2026-10-24 by Atlas. Evidence for each task: project profiles in `projects/`.

| ID | Project | Title | Objective | Deliverable | Owner | Status | Approval required | I | U | C | E | Priority |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CF-001 | CLEARFRAME | Finish Polar org setup, payout & review | Make Polar checkout live (org status ≠ created) | Polar org details submitted, payout connected, review passed; GUARD re-verifies via Polar MCP | Ryan (human); GUARD tracks | blocked (Ryan action) | yes — only Ryan can do it | 5 | 5 | 5 | 2 | **62.5** |
| CF-002 | CLEARFRAME | Live $9 test purchase with LAUNCH9 | Prove real payment works in live mode | One real order visible in Polar; refund decision recorded | GUARD (coordination) | awaiting approval; blocked by CF-001 | yes — spends Ryan's $9; refund decision | 5 | 4 | 4 | 2 | **40.0** |
| CF-006 | CLEARFRAME | Google Search Console verification + sitemap submit | Get indexing/search data for getclearframe.app | Verification steps draft; after approval: property verified, sitemap.xml submitted | SPARK | active (draft steps) | yes — DNS TXT on Cloudflare (prod DNS) + Search Console access | 3 | 3 | 4 | 1 | **36.0** |
| CF-003 | CLEARFRAME | Live magic-link sign-in end-to-end test | Confirm paid user gets email (Resend), signs in, sees Pro dashboard/module | Test checklist + result log with evidence (no secrets) | FORGE | blocked by CF-002 | yes — needs Ryan's purchase email inbox | 4 | 4 | 4 | 2 | **32.0** |
| CF-004 | CLEARFRAME | Choose & spec privacy-compatible (cookieless) analytics | Close the analytics gap without breaking privacy claims/CSP | Spec: tool, events (visit, upgrade click, sign-in), privacy-copy changes, cost | PULSE | active | no for spec; yes to enable (prod change, any spend, privacy page update) | 4 | 4 | 4 | 2 | **32.0** |
| CF-007 | CLEARFRAME | Verify support@ forwarding + triage drafting end-to-end | Confirm support mail reaches clearframe-desk inbox and drafts (never sends) | Test record: message received, draft produced, nothing auto-sent | GUARD | active | yes — a test email must be sent (by Ryan or with his OK) | 3 | 3 | 3 | 1 | **27.0** |
| OPS-001 | PORTFOLIO | First manual Atlas cycle, then propose routine activation | Validate daily workflow before scheduling (per Ryan) | Baseline report (2026-10-24) + one more manual cycle; activation proposal | ATLAS | active | yes — Ryan confirms before any routine is scheduled | 3 | 2 | 4 | 1 | **24.0** |
| CF-005 | CLEARFRAME | Implement analytics per CF-004 as draft PR | Ship measurement | Draft PR in clearframe; function count stays ≤12 | FORGE | queued (after CF-004) | yes — merge/deploy | 4 | 3 | 4 | 2 | **24.0** |
| CF-008 | CLEARFRAME | Uptime monitoring proposal (/, /signin, /api/auth/session) | Detect outages without relying on silence | Options + cost; after approval, monitor configured | GUARD | active | yes — any new account/spend | 3 | 3 | 4 | 2 | **18.0** |
| TT-001 | TURTLETYPE | Verify server entitlement check in api/results.js | Confirm RevenueCat v1 /subscribers with public web key is supported and safe | Read-only review note; fix as draft PR if needed | FORGE | active (read-only review) | no for review; yes to merge a fix | 3 | 2 | 3 | 1 | **18.0** |
| TT-002 | TURTLETYPE | Decide Plus billing go-live (live Stripe → RevenueCat, set REVENUECAT_WEB_PUBLIC_KEY) | Enable $10/yr Plus or explicitly park it | Ryan decision; if yes, FORGE checklist then env var set | Ryan decision; FORGE executes | awaiting approval | yes — payment account + production env change | 4 | 2 | 4 | 2 | **16.0** |
| CF-012 | CLEARFRAME | Domain renewal decision (auto-renew off, renews $14.20) | Avoid getclearframe.app lapse ~Oct 2027 | Decision recorded; calendar note | GUARD | queued (GUARD WIP) | yes — spending / registrar change | 3 | 1 | 5 | 1 | **15.0** |
| CF-009 | CLEARFRAME | SEO landing pages (drafts) | Organic acquisition for metadata-removal searches | Draft pages + keyword rationale as draft PR | SPARK | active (drafts) | yes — publish/merge | 4 | 3 | 3 | 3 | **12.0** |
| CF-010 | CLEARFRAME | HEIC/RAW progress bar (engine ~25 MB download) | Reduce perceived wait on first HEIC/RAW file | Draft PR | FORGE | queued | yes — merge/deploy | 3 | 2 | 4 | 2 | **12.0** |
| TT-003 | TURTLETYPE | Analytics baseline | Measure visits/tests started | Spec (reuse CF-004 approach) | PULSE | queued | yes to enable | 3 | 2 | 4 | 2 | **12.0** |
| GH-001 | GEOHOOPS | Expand researched question bank | Avoid repeating the same places daily (README) | Researched question set + Supabase migration as draft PR | SPARK (content) → FORGE | queued (SPARK WIP) | yes — DB migration on production | 3 | 2 | 4 | 2 | **12.0** |
| GH-002 | GEOHOOPS | Analytics baseline | Measure audience-building progress | Spec (reuse CF-004 approach) | PULSE | queued | yes to enable | 3 | 2 | 4 | 2 | **12.0** |
| OPS-002 | PORTFOLIO | Cleanup of out-of-scope Vercel projects | Reduce clutter/risk (6 projects) | Inventory + recommendation; Ryan deletes/pauses | GUARD | awaiting approval | yes — deletion/pausing | 2 | 1 | 5 | 1 | **10.0** |
| CF-011 | CLEARFRAME | Location-only removal preset | One-click GPS strip (common need) | Draft PR | FORGE | queued | yes — merge/deploy | 3 | 2 | 3 | 2 | **9.0** |
| CF-013 | CLEARFRAME | Legal page review decision | Drafts are not legal advice; keep personal name/other sites out | Ryan decision on professional review | GUARD | queued | yes — possible spend; publishing | 3 | 2 | 3 | 2 | **9.0** |
| TT-004 | TURTLETYPE | Plus sign-in + results sync end-to-end test (preview) | Verify Neon Auth + /api/results before billing launch | Test log | FORGE | queued (after TT-002) | no for preview test | 3 | 2 | 3 | 2 | **9.0** |
| GH-003 | GEOHOOPS | Audience channel plan (draft) | Decide where GeoHoops builds audience | Draft plan; no posting | SPARK | queued | yes — publishing/new accounts | 3 | 2 | 2 | 2 | **6.0** |
| OPS-003 | PORTFOLIO | Hello Brevard account deletion decision | Close out cancelled newsletter | Ryan decision | Ryan | awaiting approval | yes — account deletion | 1 | 1 | 3 | 1 | **3.0** |
| GH-004 | GEOHOOPS | Leaderboard / abuse controls / scheduled publishing | README future work | Proposal only | FORGE | queued | yes — merge/deploy | 2 | 1 | 3 | 3 | **2.0** |

## WIP check (active only)
| Specialist | Active | Queued |
|---|---|---|
| FORGE | TT-001 (1/2) | CF-005, CF-010, GH-001, CF-011, TT-004, GH-004 |
| SPARK | CF-006, CF-009 (2/2) | GH-001, GH-003 |
| PULSE | CF-004 (1/2) | TT-003, GH-002 |
| GUARD | CF-007, CF-008 (2/2) | CF-012, CF-013 |
| ATLAS | OPS-001 (1/2) | — |

