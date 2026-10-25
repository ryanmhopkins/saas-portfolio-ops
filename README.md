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
| `tasks/active.md` | `in_progress` work per specialist (empty until a task is approved) |
| `tasks/approvals.md` | Items awaiting the owner, plus standing approval rules |
| `operations/decisions.md` | Dated decisions |
| `operations/integrations.md` | What is connected, and what is missing, per project |
| `operations/runbook.md`, `operations/incidents.md` | Incident handling and log (severity P0–P3) |
| `bots/specialists.md`, `bots/{forge,spark,pulse,guard}.md` | Specialist charters and assignment template |
| `bots/automation-schedule.md` | Proposed routines (**not active**) |
| `reports/daily/` | Daily briefs (`YYYY-MM-DD.md`) |
| `reports/weekly/` | Weekly reports and baselines |

## Operating rules
1. **The owner's explicit approval is required** for: any production change (deploys, merges to app repos, env vars, DNS, project settings), spending money, publishing anything public, contacting customers or third parties, deleting accounts/projects. See [tasks/approvals.md](tasks/approvals.md).
2. Never invent metrics, revenue, traffic, users or completed work. Unknowns are written `UNKNOWN - source needed: <what>`. Every fact cites a source (URL or tool).
3. No secrets, tokens, env var values, customer data or private logs in this repo. Env vars may be listed by **name** only.
4. Max **3 strategic priorities per project**; max **2 `in_progress` tasks per specialist**. `awaiting_approval` and `blocked` do not count toward that cap.
5. Backlog rank: Priority = (Impact × Urgency × Confidence) / Effort, each factor 1–5. Incidents use **P0–P3** and override that score.
6. Prefer improving existing products over starting new ones.
7. Recurring routines stay disabled until each has run once manually and the owner confirms.
8. Canonical files are `tasks/approvals.md` and `operations/decisions.md`. Changes to this repo go through a branch and pull request.

## How Atlas and the specialists use this repo
- **Atlas** owns the registry, backlog, [decision log](operations/decisions.md) and [approvals list](tasks/approvals.md); assigns work using the template in [bots/specialists.md](bots/specialists.md); writes daily and weekly reports; is the only role that talks to the owner.
- **FORGE** (engineering), **SPARK** (growth), **PULSE** (analytics), **GUARD** (operations) are roles executed by Atlas's background workers (no separate bots exist yet). They work read-only or in drafts / draft PRs, report back to Atlas only, and never contact the owner or customers.
- Every status change is reflected here in the same commit cycle so `registry.md`, `backlog.md`, `active.md` and the latest report stay consistent (same IDs everywhere).
