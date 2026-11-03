# Contributing to Ternote

Thanks for helping build Ternote: a local-first native Linux Markdown editor with optional Notion synchronization.

## Before you start

- Read [the draft requirements](docs/SRS.md). Requirements are not yet frozen.
- Use an Issue to describe a change with an outcome and acceptance criteria. For larger design questions, discuss before implementation.
- Do not begin implementing unvalidated Notion API assumptions as if they were guarantees.
- Changes that could silently discard local or remote notes must not be merged.

## Working on an issue

1. Choose or create an Issue. Reference applicable SRS IDs (for example `FR-039`).
2. Create a short-lived branch from `main`.
3. Make focused commits and add tests/evidence when meaningful.
4. Open a **draft PR** while work is in progress; mark ready when reviewable.
5. Include `Closes #<number>` in the PR body only when the PR fully resolves the Issue.
6. Review the diff and tests before merging. Prefer squash merge for a single focused task.

## Branch names

`<type>/<short-kebab-description>`, such as:
- `docs/review-srs`
- `feat/markdown-preview`
- `fix/sync-conflict-recovery`
- `test/notion-roundtrip`
- `chore/setup-ci`

Allowed types: `feat`, `fix`, `docs`, `test`, `refactor`, `perf`, `build`, `ci`, `chore`, `poc`.

## Commit messages

Use [Conventional Commits](https://www.conventionalcommits.org/):

```text
<type>(optional-scope): imperative summary
```

Examples:
- `docs(srs): clarify non-destructive sync requirement`
- `feat(editor): add markdown source preview`
- `test(sync): cover concurrent remote modification`
- `fix(notion): reject truncated page responses`

Use `BREAKING CHANGE:` in the footer for incompatible behavior. Do not claim an issue is fixed before its acceptance criteria are met.

## Review checklist

- Does the change satisfy the linked Issue and relevant SRS acceptance criteria?
- Is the implementation small enough to review?
- Are new behaviors covered by tests or documented manual verification?
- Do destructive sync and conversion paths fail safely?
- Are credentials and note contents excluded from logs?
- Is platform behavior (x86_64/aarch64) considered where relevant?
- Are user-facing documentation and limitations updated?

## Documentation

- `docs/SRS.md`: requirements and IDs.
- `docs/development-workflow.md`: issue, PR, project and milestone process.
- Architecture and PoC findings should go under `docs/` as the project grows.

For now, no strict branch protection or CI status checks are required until the build/test pipeline is established. Never bypass a failing check once checks are configured.
