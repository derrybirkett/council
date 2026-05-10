# Council GitHub Conventions

This repository uses branch-based development and local git hooks to protect the main branch.

## Branch workflow
- Create a branch for every change.
- Commit only from a branch.
- Push only from a branch.
- Merge into `main` only through review or an explicit promotion step.

## Local hooks
- A git hooks path is configured in `.githooks/`.
- The hooks are designed to prevent commits or pushes directly on `main` once the repo is set up.
- Do not bypass the hooks unless you are fixing the hook setup itself.

## What to edit
- `advisors/*` content files
- `docs/*.md`
- `council.yaml`

## What not to do
- Do not add runtime app code, build tooling, or infrastructure scaffolding.
- Do not assume this repo is an application with a standard build/test workflow.
