# Backlog

**Scoring:** Impact, Urgency, Confidence, Effort each 1–5 (Effort 5 = largest). Priority = (I × U × C) / E, rounded to 1 decimal; sorted high → low. Incidents use P0–P3 and override scores (D-011). Limits: max 3 strategic priorities per project ([registry](../projects/registry.md)); max 2 `in_progress` tasks per specialist. `awaiting_approval` and `blocked` do not count toward that cap.

**Status:** `backlog` | `ready` | `in_progress` | `in_review` | `awaiting_approval` | `done` | `blocked`.

Nothing is `in_progress` or `ready`: no task has been approved to start. See [active.md](active.md). Last updated 2026-10-24 from AUD-FORGE-001, AUD-GUARD-001, AUD-PULSE-001, AUD-SPARK-001. Pre-existing scores are unchanged. Notes on CF-002, CF-004, and CF-013 were updated 2026-10-25; scores were not changed.

| ID | Project | Title | Objective | Deliverable | Owner | Status | Approval required | I | U | C | E | Priority |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CF-001 | CLEARFRAME | Finish Polar org setup, payout & review | Make Polar checkout live (org status ≠ created). Blocked on the owner | Polar org details submitted, payout connected, review passed; GUARD re-verifies via Polar MCP | Owner; GUARD tracks | blocked | yes — only the owner can do it | 5 | 5 | 5 | 2 | **62.5** |
| CF-014 | CLEARFRAME | /contact shows support@getclearframe.app | Replace the personal address on /contact (commit 9f0a70a9) so mail is triaged | Draft PR. Page shows support@getclearframe.app | FORGE | awaiting_approval | yes — production copy | 3 | 4 | 5 | 1 | **60.0** |
| CF-015 | CLEARFRAME | Decide if Pro source stays public | `api/pro/files/_pro.js` and `_pro-worker.mjs` are readable in the public repo; served copy is gated | Owner decision recorded in operations/decisions.md | ATLAS | awaiting_approval | yes — business-model decision | 4 | 3 | 5 | 1 | **60.0** |
| CF-002 | CLEARFRAME | Live $9 test purchase with LAUNCH9 | Prove real payment works in live mode. Blocked until CF-001. LAUNCH9 was removed in PR #9 (2026-10-25, D-019); this task has not been replaced | One real order visible in Polar; refund decision recorded | GUARD | blocked | yes — spends money; refund decision | 5 | 4 | 4 | 2 | **40.0** |
| CF-006 | CLEARFRAME | Google Search Console verification + sitemap submit | Get indexing/search data for getclearframe.app. Indexing is UNKNOWN | After approval: property verified, sitemap.xml submitted | SPARK | awaiting_approval | yes — DNS TXT on Cloudflare + Search Console access | 3 | 3 | 4 | 1 | **36.0** |
| CF-003 | CLEARFRAME | Live magic-link sign-in end-to-end test | Confirm a paid user gets email, signs in, and sees Pro. Blocked until CF-002 | Test checklist + result log (no secrets) | FORGE | blocked | yes — needs the purchase inbox | 4 | 4 | 4 | 2 | **32.0** |
| CF-004 | CLEARFRAME | Choose privacy-compatible analytics | Close the analytics gap without breaking privacy claims or CSP. A-012 is still pending. PR #9 added event pro_dialog_opened; a PostHog request returned 200 on 2026-10-25; the event was not confirmed in PostHog Live Events | Spec: tool, events (visit, upgrade click, sign-in), privacy-copy changes, cost | PULSE | awaiting_approval | yes — tool choice (A-012); enablement is a later prod change | 4 | 4 | 4 | 2 | **32.0** |
| OPS-004 | PORTFOLIO | Minimal CI and branch protection | All three repos have no GitHub Actions and unprotected main | Draft CI using existing tests or typecheck, plus a branch-protection proposal. No merge | FORGE | awaiting_approval | yes — repo settings | 4 | 3 | 5 | 2 | **30.0** |
| CF-007 | CLEARFRAME | Verify support@ forwarding | Confirm support mail reaches the clearframe-desk inbox | Verified 2026-10-24 22:00 ET. Log said a draft was prepared. Outbound reply at 22:03: cause UNKNOWN (AUD-GUARD-001) | GUARD | done | — | 3 | 3 | 3 | 1 | **27.0** |
| GH-005 | GEOHOOPS | Upgrade Next.js to latest 16.4.x | Clear critical advisories in next@16.0.10 (GHSA-673q-mjm6-r5xr, GHSA-2464-fhr4-w9xw, fixed from 16.4.1) plus a high-severity Server Actions DoS. Feature use is UNKNOWN | Draft PR only. No merge, no deploy | FORGE | awaiting_approval | yes — production dependency upgrade | 5 | 4 | 4 | 3 | **26.7** |
| OPS-001 | PORTFOLIO | First manual Atlas cycle, then propose routine activation | Baseline is filed. A second manual cycle is not started | Baseline (reports/weekly/2026-10-24-baseline.md) plus one more manual cycle before any schedule | ATLAS | backlog | yes — owner confirms before any routine is scheduled | 3 | 2 | 4 | 1 | **24.0** |
| CF-005 | CLEARFRAME | Implement analytics per CF-004 as draft PR | Ship measurement after the tool is chosen. Blocked until CF-004 | Draft PR in clearframe; function count stays ≤12 | FORGE | blocked | yes — merge/deploy | 4 | 3 | 4 | 2 | **24.0** |
| CF-008 | PORTFOLIO | Uptime and error monitoring | Detect outages on all three; ClearFrame sign-in path first. No monitor exists | Options + cost. After approval, monitor configured | GUARD | awaiting_approval | yes — any new account or spend | 3 | 3 | 4 | 2 | **18.0** |
| TT-001 | TURTLETYPE | Verify server entitlement check in api/results.js | Confirm RevenueCat v1 /subscribers with the public web key | Done (AUD-FORGE-001): approach sound; configuration gap, not a code bug. Results cannot be spoofed; client gates are UI only. Follow-up is TT-005 | FORGE | done | — | 3 | 2 | 3 | 1 | **18.0** |
| TT-005 | TURTLETYPE | Entitlement hardening from TT-001 | Build-check an rcb_ key prefix, honor grace_period_expires_date, add node --test for hasPlus. GET creates RevenueCat customers. No caching | Draft PR. Redeploy client and server only after the key is set (TT-002) | FORGE | awaiting_approval | yes — merge/deploy | 3 | 3 | 4 | 2 | **18.0** |
| TT-002 | TURTLETYPE | RevenueCat web key and Plus go-live or park | Set `REVENUECAT_WEB_PUBLIC_KEY` (live Stripe in RevenueCat) or explicitly park Plus | Owner decision. If yes, FORGE checklist then env var set by the owner | Owner; FORGE executes | awaiting_approval | yes — payment account + production env change | 4 | 2 | 4 | 2 | **16.0** |
| TT-007 | TURTLETYPE | Review @neondatabase/neon-js beta caret | Package is on a beta caret range (AUD-FORGE-001). Impact is UNKNOWN | Note, or a draft pin. No production change until approved | FORGE | backlog | yes to merge | 2 | 2 | 4 | 1 | **16.0** |
| CF-012 | CLEARFRAME | Domain auto-renew decision | getclearframe.app auto-renew is off; renews at $14.20; lapses ~Oct 2027 | Decision recorded | GUARD | awaiting_approval | yes — spending / registrar change | 3 | 1 | 5 | 1 | **15.0** |
| OPS-005 | PORTFOLIO | Cost feed for hosting spend | Spend is UNKNOWN on all three. Hobby logs last about 1 hour | A named connector or export. No guessed dollars | PULSE | blocked | yes — billing access | 3 | 2 | 5 | 2 | **15.0** |
| CF-009 | CLEARFRAME | SEO basics | Share image, JSON-LD, visible price, Free vs Pro table. How-to pages stay drafts (AUD-SPARK-001) | Draft PR. No publish until approved | SPARK | awaiting_approval | yes — publish/merge | 4 | 3 | 3 | 3 | **12.0** |
| CF-010 | CLEARFRAME | HEIC/RAW progress bar | Reduce perceived wait on the ~25 MB engine download | Draft PR | FORGE | backlog | yes — merge/deploy | 3 | 2 | 4 | 2 | **12.0** |
| TT-003 | TURTLETYPE | Analytics baseline | Measure visits and tests started, after CF-004 | Spec reusing the CF-004 approach | PULSE | backlog | yes to enable | 3 | 2 | 4 | 2 | **12.0** |
| GH-001 | GEOHOOPS | Expand researched question bank | Avoid repeating the same places daily (README). Live count is UNKNOWN | Researched question set + Supabase migration as a draft PR | SPARK → FORGE | backlog | yes — DB migration on production | 3 | 2 | 4 | 2 | **12.0** |
| GH-002 | GEOHOOPS | Analytics baseline | Measure audience-building progress, after CF-004 | Spec reusing the CF-004 approach | PULSE | backlog | yes to enable | 3 | 2 | 4 | 2 | **12.0** |
| TT-006 | TURTLETYPE | SEO basics | Two H1s, no canonical, no social tags; robots and sitemap 404. No custom domain | Draft checklist. Domain purchase is a separate approval | SPARK | backlog | yes to publish; domain purchase needs approval | 3 | 2 | 4 | 2 | **12.0** |
| OPS-006 | PORTFOLIO | Security headers on TurtleType and GeoHoops | Both lack security headers (AUD-FORGE-001). ClearFrame is not in this task | Proposal, then a draft PR if approved | FORGE | backlog | yes — merge/deploy | 3 | 2 | 4 | 2 | **12.0** |
| OPS-002 | PORTFOLIO | Cleanup of out-of-scope Vercel projects | Reduce clutter and risk (6 projects) | Inventory + recommendation. Owner deletes or pauses | GUARD | awaiting_approval | yes — deletion/pausing | 2 | 1 | 5 | 1 | **10.0** |
| CF-011 | CLEARFRAME | Location-only removal preset | One-click GPS strip | Draft PR | FORGE | backlog | yes — merge/deploy | 3 | 2 | 3 | 2 | **9.0** |
| CF-013 | CLEARFRAME | Legal page review decision | Drafts are not legal advice. 2026-10-25: six LEGAL REVIEW sentences in terms.html, including "Polar as merchant of record"; "This section is a draft for review" is still visible (A-020) | Owner decision on a professional review | GUARD | awaiting_approval | yes — possible spend; publishing | 3 | 2 | 3 | 2 | **9.0** |
| TT-004 | TURTLETYPE | Plus sign-in + results sync end-to-end test | Verify Neon Auth + /api/results before billing launch. Blocked until TT-002 | Test log | FORGE | blocked | no for a preview test | 3 | 2 | 3 | 2 | **9.0** |
| GH-006 | GEOHOOPS | SEO basics | Client-rendered, so crawlers see no content; no share tags; robots and sitemap 404 | Draft checklist (headings, robots, sitemap). No posting | SPARK | backlog | yes to publish | 3 | 2 | 4 | 3 | **8.0** |
| GH-003 | GEOHOOPS | Audience channel plan | Decide where GeoHoops builds an audience | Draft plan. No posting | SPARK | backlog | yes — publishing or new accounts | 3 | 2 | 2 | 2 | **6.0** |
| OPS-003 | PORTFOLIO | Hello Brevard account deletion decision | Close out the cancelled newsletter | Owner decision | Owner | awaiting_approval | yes — account deletion | 1 | 1 | 3 | 1 | **3.0** |
| GH-004 | GEOHOOPS | Leaderboard / abuse controls / scheduled publishing | README future work | Proposal only | FORGE | backlog | yes — merge/deploy | 2 | 1 | 3 | 3 | **2.0** |

## In progress
None. Every specialist is at 0/2.

| Specialist | in_progress | Waiting (does not count) |
|---|---|---|
| FORGE | 0/2 | GH-005, OPS-004, CF-014, TT-005 awaiting approval; CF-003, CF-005, TT-004 blocked |
| SPARK | 0/2 | CF-006, CF-009 awaiting approval |
| PULSE | 0/2 | CF-004 awaiting approval; OPS-005 blocked |
| GUARD | 0/2 | CF-008, CF-012, CF-013 awaiting approval; CF-001 blocked on the owner |
| ATLAS | 0/2 | CF-015 awaiting approval |
