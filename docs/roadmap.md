# Roadmap

## Current state

Version `0.1.0` on `main` contains:

- repo manifest (`council.yaml`)
- advisor schema
- shared principles
- full CTO plugin
- full CISO plugin
- `founder-mode` pack
- git workflow enforcement hooks

---

## Phase 2 — Complete the core advisor set

**Goal:** give the repo enough breadth to cover a full founder-led business, not just engineering and security.

### Advisors to add

Priority order reflects the frequency and weight of decisions in a typical founder context.

| Advisor | Key concerns |
|---|---|
| `ceo` | Strategy, prioritization, capital allocation, leadership tradeoffs |
| `cfo` | Financial planning, unit economics, cash runway, vendor cost discipline |
| `product` | Product strategy, roadmap management, discovery quality, feature tradeoffs |
| `coo` | Operating model, execution cadence, service quality, process design |
| `people` | Hiring systems, org design, performance management, management standards |
| `legal` | Contracts, compliance posture, policy review, regulatory coordination |
| `sales` | Pipeline quality, qualification discipline, revenue execution |
| `marketing` | Positioning, messaging, demand generation, channel strategy |

### Each advisor needs

The same full folder contract as `cto` and `ciso`:

- `advisor.yaml`
- `prompt.md`
- `responsibilities.md`
- `domains.md`
- `tools.yaml`
- `playbooks/` — at least two core playbooks
- `checklists/quarterly-review.md`
- `templates/` — at least one standard output template
- `metrics.md`
- `escalation.md`

---

## Phase 3 — Shared content layer

**Goal:** create the shared resources that make advisors coherent as a set rather than independent silos.

### Files to add

- `shared/schemas/playbook.schema.yaml` — playbook structure validation
- `shared/templates/memo.md` — standard decision memo
- `shared/templates/plan.md` — standard plan structure
- `shared/templates/review.md` — standard review output
- `shared/templates/scorecard.md` — standard scorecard
- `shared/decision-rubrics/prioritization.md` — shared prioritization framework
- `shared/decision-rubrics/risk.md` — shared risk assessment framework
- `shared/decision-rubrics/tradeoffs.md` — explicit tradeoff language guide
- `shared/glossary.md` — common terms used across advisors

---

## Phase 4 — Packs and scenarios

**Goal:** make the repo useful for different business contexts without modifying advisor core files.

### Packs to add

- `packs/saas-b2b.yaml` — stronger focus on reliability, security, customer commitments
- `packs/regulated-company.yaml` — more controls, traceability, approvals, compliance
- `packs/agency-mode.yaml` — project delivery, staffing, margin, client risk
- `packs/technical-due-diligence.yaml` — focused pack for investor or acquirer reviews

### Scenarios to add

- `scenarios/startup-zero-to-one/` — advisor defaults and emphasis for pre-product stage
- `scenarios/saas-growth/` — post-PMF scaling, hiring, and operational complexity
- `scenarios/consulting-firm/` — project economics, client management, utilization

---

## Phase 5 — Automation and validation

**Goal:** make advisor content machine-verifiable so quality degrades gracefully as the library grows.

- CI pipeline with a schema validation job against `advisor.schema.yaml` and `playbook.schema.yaml`
- Lint check for required files in every advisor folder
- Link validation for cross-advisor escalation references
- Release workflow to tag and publish version bumps
- Changelog automation

---

## Phase 6 — Vercel SaaS product layer

**Goal:** turn the advisor content library into a usable commercial product.

This repo stays as the portable content layer. A separate application repository imports it.

### Application concerns (out of this repo)

- Next.js app router frontend
- Vercel hosting and preview environments
- Auth provider for user and team identity
- Stripe billing and entitlement model
- Postgres for tenant, session, artifact, and entitlement state
- Object storage for documents and generated reports
- Background job runner for long-running advisor evaluations

### Content concerns to prepare in this repo

- Ensure all advisor IDs are stable across versions
- Add `monetization_tags` and `app_surfaces` to all advisor manifests (started in CTO and CISO)
- Define a tenant override model: how a consuming app extends a playbook or template without modifying upstream files
- Add version fields and changelogs so the app can surface freshness and release notes

### Likely product surfaces

- Advisor chat per role, backed by this repo's prompt and tools files
- Multi-advisor review workspace for cross-functional decisions
- Quarterly health assessment reports drawing on metrics files
- Downloadable executive memos using templates from this repo
- Team workspaces with shared advisor session history and artifacts

### Pricing tier mapping

| Tier | Advisors | Capabilities |
|---|---|---|
| Free | Limited subset | Capped usage, no saved artifacts |
| Pro | CTO, CISO, CEO, CFO, Product | Full advisor depth, saved artifacts, higher limits |
| Team | All advisors | Shared workspaces, admin, policy packs, review workflows |
| Expert | All advisors + premium packs | Regulated templates, advanced reports, concierge workflows |

---

## Immediate next actions

1. Branch and scaffold CEO, CFO, and Product advisors as a unit
2. Add the shared templates folder and core output templates
3. Add the playbook schema
4. Add a basic CI schema-validation job
5. Open the application repository for the Vercel product layer
