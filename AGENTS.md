# AI Agent Instructions for Council

## Purpose
This repository is a reusable library of advisor plugins for founder-operators and leadership teams. It is a content-first repo, not an application codebase.

## What to do here
- Edit or add advisor plugin content under `advisors/`.
- Keep advisor definitions consistent with the contract described in `README.md`.
- Prefer adding or updating metadata, prompts, responsibilities, domains, tools, playbooks, and documentation.
- Preserve the advisor contract shape and point to existing docs rather than duplicating them.

## Key conventions
- Each advisor folder should include at least:
  - `advisor.yaml`
  - `prompt.md`
  - `responsibilities.md`
  - `domains.md`
  - `tools.yaml`
  - `playbooks/`
- Use `shared/schemas/advisor.schema.yaml` and `shared/schemas/playbook.schema.yaml` as the canonical schema references.
- `council.yaml` defines project metadata, distribution modes, and the intended product direction.
- The repository is meant to be portable and importable by other projects.

## Branching and merge rules
- Do not work directly on `main`.
- Create a branch for every change.
- Commit only from a branch.
- Push only from a branch.
- Merge through review or an explicit promotion step.
- There are local git hooks under `.githooks/` to help enforce this workflow.

## What not to do
- Do not invent a build/test workflow for this repo; there is no application runtime or package manifest here.
- Do not add runtime or app scaffolding (no frontend/backend implementation code unless it is explicitly part of this content library).
- Do not assume this repo is a Node app or deployable service.
- Do not merge directly to `main` without review.

## Useful links
- [README.md](README.md)
- [CONTRIBUTING.md](CONTRIBUTING.md)
- [`.github/README.md`](.github/README.md)
- [shared/schemas/advisor.schema.yaml](shared/schemas/advisor.schema.yaml)
- [shared/schemas/playbook.schema.yaml](shared/schemas/playbook.schema.yaml)
- [council.yaml](council.yaml)

## Best practices for agents
- Link to existing documentation rather than copying it.
- Keep advisor prompts and definitions aligned with the existing advisor contract.
- When adding new advisors, keep scope boundaries narrow and explicit.
- Keep playbooks practical, repeatable, and consistent with the repo's leadership/advisor model.
