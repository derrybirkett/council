# Activity Log

## 2026-04-12 — Repository Bootstrap

### Session Summary

Designed, scaffolded, and shipped the first working version of the Council advisor-plugin repository.

---

### Work Completed

#### 1. Concept and design

Defined the repository model: a reusable library of role-based advisor plugins intended for import into other projects as a git submodule, subtree, or reference copy, with a second-phase path toward a monetized Vercel-hosted web application.

Established the core design goals: reusable, composable, opinionated, auditable, extensible, and safe. Identified the advisor contract as the central primitive.

#### 2. Repository scaffold

Created the initial file structure:

- `council.yaml` — repo manifest with version, distribution modes, Vercel product direction, and default pack
- `shared/principles.md` — shared operating principles across all advisors
- `shared/schemas/advisor.schema.yaml` — JSON Schema definition for advisor manifests
- `packs/founder-mode.yaml` — first operating pack bundling CTO and CISO with lean defaults
- `docs/vercel-saas-product.md` — product direction note capturing the future Vercel app stack, monetization model, and architectural constraint

Updated `README.md` with full repo model, advisor contract example, folder structure, git workflow, and productization guidance.

#### 3. Git repository setup

Initialized a local git repository on `main`.

Created a private GitHub repository at `github.com/derrybirkett/council`.

Added local enforcement for branch-only development:

- `.githooks/pre-commit` — blocks commits on `main`
- `.githooks/pre-push` — blocks pushes from `main`
- `git config core.hooksPath .githooks` — activates hooks for the local clone
- `CONTRIBUTING.md` — documents the branch workflow and hook setup instructions

Attempted remote branch protection on GitHub; rejected with HTTP 403 as that feature requires a paid plan for private repositories.

#### 4. Initial commit and tag

Moved all work to branch `chore/bootstrap-repo`.

Created the first commit: `68283f1 chore: bootstrap council repository`.

Tagged `v0.1.0`.

Pushed the branch and tag to GitHub.

Promoted `chore/bootstrap-repo` to `main` on GitHub to initialize the default branch.

#### 5. CTO and CISO advisor plugins

Opened branch `feat/cto-ciso-plugin-scaffold`.

Scaffolded complete operating content for both priority advisors:

**CTO advisor** (`advisors/cto/`)

| File | Content |
|---|---|
| `prompt.md` | Mission, posture, default behaviours, collaboration rules, anti-patterns |
| `responsibilities.md` | Owns, influences, reviews, must-not-decide-alone, success conditions |
| `domains.md` | Core domains, adjacent domains, out-of-scope |
| `tools.yaml` | Allowed tool classes, required evidence, prohibited actions, output requirements |
| `playbooks/architecture-review.md` | Steps, inputs, outputs for architecture review |
| `playbooks/delivery-recovery.md` | Diagnosis and recovery process for delivery failures |
| `checklists/quarterly-review.md` | Quarterly operating checklist |
| `templates/architecture-decision-record.md` | ADR template |
| `metrics.md` | Primary and secondary metrics with review cadence |
| `escalation.md` | Escalation paths to CISO, CFO, and CEO |

**CISO advisor** (`advisors/ciso/`)

| File | Content |
|---|---|
| `prompt.md` | Mission, posture, default behaviours, collaboration rules, anti-patterns |
| `responsibilities.md` | Owns, influences, reviews, must-not-decide-alone, success conditions |
| `domains.md` | Core domains, adjacent domains, out-of-scope |
| `tools.yaml` | Allowed tool classes, required evidence, prohibited actions, output requirements |
| `playbooks/security-architecture-review.md` | Steps, inputs, outputs for security architecture review |
| `playbooks/incident-severity-assessment.md` | Incident classification and escalation process |
| `checklists/quarterly-review.md` | Quarterly security operating checklist |
| `templates/security-review-memo.md` | Security review memo template |
| `metrics.md` | Primary and secondary metrics with review cadence |
| `escalation.md` | Escalation paths to CTO, Legal, and CEO |

#### 6. PR, review, and merge

Created pull request #1: `feat: scaffold full CTO and CISO advisor plugins`.

Reviewed the PR: 633 additions, 0 deletions, pure portable domain content, advisor contracts consistent with schema.

Merged via merge commit `69a8d9b` into `main`.

Synced local `main`.

---

### Decisions Made

- Advisor content layer kept strictly separate from application and runtime code to support both submodule reuse and a future Vercel SaaS product
- Branch-only git workflow enforced locally; remote branch protection deferred until GitHub plan allows it on private repos
- CTO and CISO prioritized as first full advisor plugins due to their direct relevance and cross-advisor dependency
- `founder-mode` chosen as the first pack to cover the most likely immediate use case
- Semantic versioning adopted from the start; current library version is `0.1.0`

---

### Open Items

- Remote branch protection on `main` requires GitHub plan upgrade
- No CI pipeline yet; validation of YAML schemas is manual
- Remaining advisor plugins (CEO, CFO, Product, COO, Sales, Marketing, People, Legal) are not yet scaffolded
- No playbook schema defined yet (`shared/schemas/playbook.schema.yaml` is referenced but not created)
- No shared decision templates yet (`shared/templates/`)
- No Vercel app layer exists yet
