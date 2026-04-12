# Council

Council is a reusable repository of role-based advisor plugins for founder-operators and small leadership teams.

The intent is to make this repository importable into other projects as a git submodule, subtree, or read-only reference so those projects can expose a consistent set of business advisors with clear responsibilities, playbooks, and operating standards.

## What This Repo Should Be

This repo should act like an advisor operating system rather than a loose collection of prompts.

Each advisor plugin should define:

- its mandate
- its decision rights
- its core responsibilities
- the questions it should ask
- the tools it is allowed to use
- the outputs it should produce
- the situations where it should escalate to another advisor
- the standards and frameworks it should follow

The result is a portable leadership layer you can reuse across products, companies, or experiments.

This should also be designed as a future product asset. The same advisor definitions should support both:

- repo-level import into private projects
- a monetized web application, likely built on a Vercel-hosted Next.js stack

## Git Workflow

This repository should never be developed directly on `main`.

Rules:

- create a branch for every change
- commit only from a branch
- push only from a branch
- merge into `main` through review or an explicit promotion step

The repo includes local git hooks to block commits and pushes on `main` once `core.hooksPath` is configured.

## Design Goals

- Reusable: easy to mount into other repos without heavy integration work
- Composable: advisors can collaborate, hand off work, and challenge each other
- Opinionated: focused on practical operating standards, not generic roleplay
- Auditable: each advisor has explicit scope, checklists, and output formats
- Extensible: new advisors can be added without changing the whole system
- Safe: high-risk domains like security, legal, finance, and compliance have stronger guardrails

## Core Model

An advisor plugin is a folder with a standard contract.

Suggested shape:

```text
council/
  README.md
  council.yaml
  shared/
    glossary.md
    principles.md
    decision-rubrics/
      prioritization.md
      risk.md
      tradeoffs.md
    templates/
      memo.md
      plan.md
      review.md
      scorecard.md
    schemas/
      advisor.schema.yaml
      playbook.schema.yaml
  advisors/
    cto/
      advisor.yaml
      prompt.md
      responsibilities.md
      domains.md
      tools.yaml
      playbooks/
      checklists/
      templates/
      metrics.md
      escalation.md
    ciso/
      advisor.yaml
      prompt.md
      responsibilities.md
      domains.md
      tools.yaml
      playbooks/
      checklists/
      templates/
      metrics.md
      escalation.md
    ceo/
    coo/
    cfo/
    product/
    marketing/
    sales/
    people/
    legal/
  scenarios/
    startup-zero-to-one/
    saas-growth/
    consulting-firm/
  packs/
    founder-mode.yaml
    saas-b2b.yaml
    regulated-company.yaml
```

## Standard Advisor Contract

Every advisor should expose the same top-level fields so consumers can load them consistently.

Example manifest:

```yaml
id: cto
name: Chief Technology Officer
version: 0.1.0
mission: Ensure the company builds the right technology, in the right way, at the right level of quality and speed.
reports_to: ceo
peer_advisors:
  - ciso
  - cfo
  - product
scope:
  owns:
    - technical strategy
    - architecture
    - engineering execution
    - delivery health
    - technical quality
  advises_on:
    - product feasibility
    - build-vs-buy decisions
    - team design
  must_not_decide_alone:
    - legal risk
    - material financial commitments
    - security exceptions
inputs:
  - business goals
  - product roadmap
  - engineering telemetry
  - architecture docs
outputs:
  - strategy memos
  - technical plans
  - risk reviews
  - architecture decisions
operating_modes:
  - strategic
  - review
  - incident
  - planning
tool_classes:
  - repo-analysis
  - architecture-review
  - roadmap-analysis
  - metrics
playbooks:
  - architecture-review
  - delivery-recovery
  - platform-strategy
escalates_to:
  - ceo
  - ciso
success_metrics:
  - delivery predictability
  - reliability
  - engineering throughput
  - architecture coherence
```

## What Each Advisor Folder Should Contain

`advisor.yaml`
Defines the machine-readable contract.

`prompt.md`
Defines the advisor voice, posture, priorities, challenge style, and collaboration rules.

`responsibilities.md`
Defines what the advisor owns, influences, reviews, and explicitly does not own.

`domains.md`
Defines topic coverage. This is where you prevent vague overlap between roles.

`tools.yaml`
Defines allowed tools, prohibited tools, required evidence before decisions, and output expectations.

`playbooks/`
Contains repeatable procedures for common scenarios.

`checklists/`
Contains preflight, review, launch, incident, audit, and quarterly operating checklists.

`templates/`
Contains standard output structures like decision memos, incident reports, hiring scorecards, or risk registers.

`metrics.md`
Defines how the advisor measures health and how often those metrics should be reviewed.

`escalation.md`
Defines when the advisor should loop in other roles or refuse to proceed without approval.

## Initial Advisor Set

Recommended first wave:

- `cto`: technology strategy, architecture, engineering effectiveness, delivery quality
- `ciso`: security strategy, controls, threat posture, incident readiness, security governance
- `ceo`: strategy, prioritization, capital allocation, leadership tradeoffs
- `coo`: process, operational cadence, execution system, service quality
- `cfo`: financial planning, unit economics, capital discipline, risk
- `product`: product strategy, roadmap discipline, discovery quality, value definition
- `sales`: pipeline quality, sales process, qualification discipline, revenue execution
- `marketing`: positioning, demand generation, messaging, channel mix
- `people`: hiring systems, org design, performance management, management standards
- `legal`: contracts, compliance posture, policy review, regulatory coordination

If the immediate goal is usefulness rather than breadth, start with `cto`, `ciso`, `ceo`, `cfo`, and `product`.

## The CTO Plugin

This should be one of the deepest and most operationally useful advisors in the repo.

Primary concerns:

- technical strategy aligned to business strategy
- system architecture and long-term maintainability
- engineering operating model
- development velocity versus quality tradeoffs
- platform and tooling choices
- hiring and leveling for engineering teams
- reliability, observability, and scalability
- build-vs-buy and vendor evaluation
- AI usage policy for engineering teams

Key playbooks:

- architecture review
- roadmap feasibility review
- technical debt triage
- incident postmortem review
- engineering org design
- delivery recovery plan
- platform standardization
- vendor and tool evaluation
- AI engineering governance

Standard outputs:

- architecture decision record
- quarterly technology strategy memo
- engineering health review
- delivery risk assessment
- buy-vs-build memo
- technical due diligence memo

Metrics the CTO should care about:

- deployment frequency
- lead time for change
- change failure rate
- mean time to restore
- uptime and error budgets
- cycle time by work type
- defect escape rate
- infrastructure cost efficiency
- percentage of roadmap blocked by platform debt

## The CISO Plugin

This should be more than a generic security reviewer. It should behave like a risk-based security executive.

Primary concerns:

- security governance and ownership clarity
- identity and access management
- software supply chain security
- application and infrastructure security
- incident readiness and response
- vendor and third-party risk
- data protection and privacy coordination
- compliance mapping where relevant
- security exception handling
- business continuity and resilience

Key playbooks:

- security architecture review
- threat modeling review
- incident severity assessment
- vulnerability triage and remediation planning
- access review
- policy exception review
- vendor security review
- minimum viable security baseline
- breach communication workflow

Standard outputs:

- risk register
- security review memo
- control gap assessment
- incident briefing
- remediation plan
- policy exception decision
- security roadmap

Metrics the CISO should care about:

- open critical vulnerabilities by age
- mean time to remediate by severity
- phishing resistance and training coverage
- privileged access exposure
- control coverage by asset class
- incident response readiness
- third-party review completion rate
- backup and recovery test success rate

## Cross-Advisor Collaboration Model

The repo will be much more useful if advisors are designed to disagree productively.

Examples:

- `cto` and `cfo` should debate cost versus engineering leverage
- `cto` and `ciso` should debate speed versus control strength
- `ceo` and `product` should debate focus versus opportunity capture
- `sales` and `product` should debate roadmap pressure versus product coherence
- `people` and `cto` should debate hiring speed versus talent bar

Add an explicit collaboration contract to every advisor:

- trusted peers
- mandatory review counterparts
- common conflict patterns
- tie-break rules
- escalation route

## Packs And Operating Contexts

Not every consuming project will need every advisor or the same level of rigor.

Use packs to bundle advisors and defaults for a situation.

Examples:

- `founder-mode`: lean defaults, fast iteration, minimal bureaucracy
- `saas-b2b`: stronger focus on reliability, security, and customer commitments
- `regulated-company`: more controls, evidence, approvals, and traceability
- `agency-mode`: project delivery, staffing, margin, and client risk focus

This avoids hard-coding one operating model into every project.

## How Other Repos Should Consume This

Recommended consumption patterns:

- git submodule when you want a pinned external source of truth
- git subtree when you want easier vendoring with fewer git ergonomics issues
- read-only sync or copy when you want to fork the advisor set per business

A consuming repo should be able to do three simple things:

- select a pack
- enable specific advisors
- extend or override local playbooks without modifying upstream core files

That implies a merge model like this:

```text
consumer-project/
  advisors/
    council/               # imported upstream repo
    local-overrides/
      cto/
      ciso/
  council.config.yaml
```

## Productization Path

Because this will likely become a monetized web product later, keep a hard separation between:

- content layer: advisor manifests, playbooks, templates, rubrics, packs
- orchestration layer: agent runtime, tool execution, session handling, evaluation
- application layer: auth, billing, team management, usage limits, analytics, UI

That separation matters because the same content should be usable in three modes:

- local repo reference
- embedded advisor engine inside another app
- first-party SaaS product

For a Vercel stack, the likely future app shape is:

- Next.js app router frontend and server actions
- Vercel hosting and preview environments
- Postgres for tenant, session, and entitlement state
- auth provider for user and team identity
- Stripe for subscriptions and billing
- object storage for uploaded evidence and generated reports
- background jobs for long-running evaluations and advisor workflows

The repo you are building now should remain the portable domain layer that the web app consumes, not the app itself.

## Versioning Strategy

Treat advisors like productized operating assets.

- semantic versions for breaking contract changes
- changelog entries for major playbook or policy shifts
- stable advisor IDs so consuming repos can depend on them
- deprecation windows for renamed roles or changed schemas

## What Good Looks Like

This repo is successful if a consuming project can point an agent system at it and reliably get:

- the right advisor for the right problem
- structured outputs instead of vague commentary
- consistent escalation behavior
- explicit tradeoff reasoning
- reusable playbooks for recurring business situations

## Recommended First Milestone

Build a thin but complete vertical slice before expanding breadth.

Phase 1:

- shared principles and templates
- advisor schema and council manifest
- `cto` plugin
- `ciso` plugin
- one pack such as `founder-mode`
- one scenario such as `saas-b2b`

That gives you enough surface area to validate the structure before you add the rest of the executive suite.

## Recommended Next Files To Add

- `council.yaml` for repo-level metadata and default pack loading
- `shared/schemas/advisor.schema.yaml` for validation
- `advisors/cto/advisor.yaml`
- `advisors/ciso/advisor.yaml`
- `packs/founder-mode.yaml`
- `shared/principles.md`
- `docs/vercel-saas-product.md`

If you want this repo to become genuinely useful, optimize for operating clarity and decision quality, not for theatrical personas. The advisor should be valuable because its scope, standards, and outputs are sharp.