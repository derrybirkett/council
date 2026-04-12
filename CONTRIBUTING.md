# Contributing

## Branch Policy

Do not write directly to `main`.

Use this workflow for every change:

1. Branch from `main`.
2. Make the change on the branch.
3. Commit and push the branch.
4. Merge back to `main` only after review or explicit approval.

Suggested branch naming:

- `feat/...` for new capabilities
- `fix/...` for corrections
- `docs/...` for documentation
- `chore/...` for repository and tooling work

## Local Enforcement

This repo includes local hooks in `.githooks/` to block commits and pushes on `main`.

Enable them with:

```sh
git config core.hooksPath .githooks
chmod +x .githooks/pre-commit .githooks/pre-push
```

For stronger enforcement, add GitHub branch protection on `main` so remote pushes and force-pushes are also blocked.