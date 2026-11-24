# Contributing / Как работим

## Branches / Клони

- Never commit directly to `main`; every change goes through a Pull Request. / Нищо директно в `main`.
- Name branches `type/short-description`: `feat/…`, `fix/…`, `docs/…`, `chore/…`, e.g. `docs/runbook`.
- One task (Issue) = one branch = one Pull Request.

## Commits / Комити

- Imperative mood, short subject (≤ 72 characters): `Add glossary terms`, not `added stuff`.
- One logical change per commit.

## Pull Requests

- Title starts with the task: `T07: Glossary terms`.
- Description contains `Closes #<issue>` so the issue closes on merge.
- At least one approving review before merging; use **Squash and merge** and delete the branch.
- Resolve conflicts locally (`git fetch`, then `git merge origin/main` or `git rebase origin/main`).

Branching strategy: GitHub Flow. `main` is always releasable; every change is a short-lived branch merged through a reviewed PR, and releases are tags on `main`. It fits a small team with CI and frequent small changes better than GitFlow, and keeps reviews unlike pure trunk-based.
