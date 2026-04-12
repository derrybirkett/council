# Council SaaS Direction

This repository should remain the portable content and policy layer for a future web application.

## Product Boundary

Keep this repo focused on advisor definitions, playbooks, templates, packs, and shared decision frameworks.

Do not couple it to:

- UI components
- auth providers
- billing code
- persistence models tied to one app
- agent runtime implementation details

## Likely Future Stack

- Next.js on Vercel for the application surface
- Postgres for tenant, session, entitlement, and artifact metadata
- Stripe for subscriptions, trials, and billing events
- object storage for uploaded documents and generated reports
- background job runner for long-running assessments

## Likely Product Surfaces

- advisor chat per role
- multi-advisor review workspace
- quarterly business health assessments
- repo and document review workflows
- downloadable executive memos and scorecards
- team workspaces with shared history and artifacts

## Monetization Model

Possible pricing layers:

- free: a limited advisor set and capped monthly usage
- pro: deeper advisors like CTO and CISO, saved artifacts, higher limits
- team: collaboration, shared workspaces, admin controls, policy packs
- expert: premium packs, regulated templates, advanced reviews, concierge workflows

## Product Requirements To Preserve Now

Design manifests and packs so the future app can attach:

- entitlements by advisor, pack, or workflow
- version history and changelogs
- scoreable outputs for dashboards and reports
- evaluation metadata for quality tracking
- tenant-specific overrides without mutating upstream source files

## Good Architecture Rule

The future Vercel app should import this repo as domain content. It should not require rewriting the advisor layer just to support billing, auth, or UI concerns.