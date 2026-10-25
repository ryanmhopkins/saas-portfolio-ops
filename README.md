# SaaS Portfolio Ops

Shared operating registry for Ryan Hopkins's SaaS portfolio, run by **Atlas** (Product Manager / Chief of Staff). It holds the project registry, backlog, decisions, approvals, integrations and reports. It is **not** a deployment repo and contains no application code, secrets or customer data.

## Portfolio (3 projects)
| ID | Project | Focus | Profile |
|---|---|---|---|
| CLEARFRAME | ClearFrame | **Focus product** | [projects/clearframe.md](projects/clearframe.md) |
| TURTLETYPE | TurtleType | Maintain / decide billing | [projects/turtletype.md](projects/turtletype.md) |
| GEOHOOPS | GeoHoops | Secondary (audience building) | [projects/geohoops.md](projects/geohoops.md) |

Full table: [projects/registry.md](projects/registry.md).

## Structure
| Path | Purpose |
|---|---|
| `projects/registry.md` | Single source of truth: IDs, repos, URLs, stage, health, strategic priorities |
| `projects/<id>.md` | Project profiles with evidence links |
| `tasks/backlog.md` | Scored, prioritized backlog (all projects) |
| `tasks/active.md` | Active work per specialist (WIP view of the backlog) |
| `operations/decision-log.md` | Dated decisions |
| `operations/approvals.md` | Items awaiting Ryan + standing approval rules |
| `operations/integrations.md` | Integration status per project and missing integrations |
| `operations/runbook.md`, `operations/incidents.md` | Incident handling and log |
| `bots/specialists.md`, `bots/{forge,spark,pulse,guard}.md` | Specialist charters and assignment template |
| `bots/automation-schedule.md` | Proposed routines (**not active**) |
| `reports/` | Daily/weekly reports (`reports/YYYY-MM-DD-*.md`, `reports/daily/`, `reports/weekly/`) |

## Operating rules
1. **Ryan's explicit approval is required** for: any production change (deploys, merges to app repos, env vars, DNS, project settings), spending money, publishing anything public, contacting customers or third parties, deleting accounts/projects. See [operations/approvals.md](operations/approvals.md).
2. Never invent metrics, revenue, traffic, users or completed work. Unknowns are written `UNKNOWN - source needed: <what>`. Every fact cites a source (URL or tool).
3. No secrets, tokens, env var values, customer data or private logs in this repo. Env vars may be listed by **name** only.
4. Max **3 active strategic priorities per project**; max **2 active tasks per specialist** (extras are `queued`).
5. Priority = (Impact × Urgency × Confidence) / Effort. Security incidents and production outages override scoring.
6. Prefer improving existing products over starting new ones.
7. Recurring routines stay disabled until each has run once manually and Ryan confirms.

## How Atlas and the specialists use this repo
- **Atlas** owns the registry, backlog, decision log and approvals list; assigns work using the template in [bots/specialists.md](bots/specialists.md); writes daily/weekly reports; is the only role that talks to Ryan.
- **FORGE** (engineering), **SPARK** (growth), **PULSE** (analytics), **GUARD** (operations) are roles executed by Atlas's background workers (no separate bots exist yet). They work read-only or in drafts / draft PRs, report back to Atlas only, and never contact Ryan or customers.
- Every status change is reflected here in the same commit cycle so `registry.md`, `backlog.md`, `active.md` and the latest report stay consistent (same IDs everywhere).
