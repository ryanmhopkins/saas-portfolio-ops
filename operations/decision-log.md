# Decision log

Newest first. Status: `accepted` · `superseded` · `reversed`. Decisions recorded from Ryan's instructions to Atlas on 2026-10-24 unless another source is cited.

| ID | Date | Project | Decision | Rationale | Decided by | Source | Status |
|---|---|---|---|---|---|---|---|
| D-008 | 2026-10-24 | CLEARFRAME | Merge PRs #1–#3 in ryanmhopkins/clearframe | Ryan instructed the merges | Ryan | Ryan instruction; [PR #1](https://github.com/ryanmhopkins/clearframe/pull/1), [#2](https://github.com/ryanmhopkins/clearframe/pull/2), [#3](https://github.com/ryanmhopkins/clearframe/pull/3) (merged 2026-10-24 ET) | accepted |
| D-007 | 2026-10-24 | CLEARFRAME | Buy domain getclearframe.app (Cloudflare, $8.20/yr; auto-renew off; renews $14.20) | Production domain for launch | Ryan | Ryan brief; domain attached to Vercel project `clearframe` (Vercel MCP) | accepted |
| D-006 | 2026-10-24 | CLEARFRAME | Polar is the payments provider (Pro $15 one-time, LAUNCH9 $6 off) | Chosen by Ryan for one-time checkout | Ryan | Ryan brief; Polar MCP (product + discount exist) | accepted |
| D-005 | 2026-10-24 | CLEARFRAME | Resend is the transactional email provider (magic links from login@getclearframe.app) | Passwordless sign-in delivery | Ryan | Ryan brief; [PR #2](https://github.com/ryanmhopkins/clearframe/pull/2), env name `EMAIL_API_KEY` | accepted |
| D-004 | 2026-10-24 | CLEARFRAME | No license keys: Free needs no account; Pro uses email magic-link sign-in tied to the Polar order | Less friction, nothing to leak or share | Ryan | Ryan brief; [README](https://github.com/ryanmhopkins/clearframe/blob/main/README.md) | accepted |
| D-003 | 2026-10-24 | PORTFOLIO | Hello Brevard newsletter is cancelled (account deletion is a separate pending decision: OPS-003) | Not part of the portfolio focus | Ryan | Ryan instruction | accepted |
| D-002 | 2026-10-24 | GEOHOOPS | GeoHoops is secondary: audience building, not revenue | Focus capacity on ClearFrame | Ryan | Ryan instruction | accepted |
| D-001 | 2026-10-24 | CLEARFRAME | ClearFrame is the focus product | Closest to revenue (live domain, checkout built) | Ryan | Ryan instruction | accepted |
