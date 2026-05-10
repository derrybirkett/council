# Copilot Instructions for Council

This repository is a content library of advisor plugins, not an application codebase.

## Primary guidance
- Focus on advisor content in `advisors/`.
- Preserve the advisor contract defined in `README.md` and `shared/schemas/advisor.schema.yaml`.
- Avoid adding runtime application code, build tooling, or infrastructure scaffolding.
- Do not assume `main` is the development branch; use feature branches and do not commit to `main` directly.

## What to edit
- `advisors/*/advisor.yaml`
- `advisors/*/prompt.md`
- `advisors/*/responsibilities.md`
- `advisors/*/domains.md`
- `advisors/*/tools.yaml`
- `advisors/*/playbooks/*.md`
- `docs/*.md`
- `council.yaml`

## What not to do
- Do not create or modify application runtime code outside the advisor content model.
- Do not invent a frontend/backend build/test workflow for this repo.
- Do not introduce deployable app configuration, server code, or package manifests.

## References
- [README.md](../README.md)
- [AGENTS.md](../AGENTS.md)
- [CONTRIBUTING.md](../CONTRIBUTING.md)
- [shared/schemas/advisor.schema.yaml](../shared/schemas/advisor.schema.yaml)
- [shared/schemas/playbook.schema.yaml](../shared/schemas/playbook.schema.yaml)
