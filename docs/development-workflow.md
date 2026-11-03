# Ternote development workflow

This page describes the lightweight GitHub workflow for Ternote. See [CONTRIBUTING.md](../CONTRIBUTING.md) for contributor instructions.

## Sources of truth

- **Requirements:** `docs/SRS.md` (stable `FR-*`, `NFR-*`, `POC-*`, `AT-*` IDs).
- **Work items:** GitHub Issues (scope, acceptance criteria, ownership).
- **Progress:** [Ternote Development Project](https://github.com/users/TomGoh/projects/1/views/1).
- **Change review:** Pull Requests linked to Issues.
- **Verification:** tests/CI plus explicit manual evidence where necessary.

Avoid maintaining a separate checkbox backlog in Markdown. Update the Issue and Project instead.

## Recommended Project configuration

Keep the existing board and use status columns:
`Todo` -> `In Progress` -> `Done`.
Add `Blocked` only if the team starts accumulating external dependencies.
Use project fields `Priority` (P0/P1/P2) and `Area` (Requirements/Sync/Editor/Platform/Infrastructure), if useful.
The Project is an overview; Issues remain authoritative.

## Milestones (suggested)

- **M0 Requirements:** review SRS v0.1, resolve MVP scope, release SRS v0.2.
- **M1 Feasibility PoC:** Markdown round trip, merge safety, ARM64 GUI tests.
- **M2 Architecture:** define document model, sync state machine, GUI choice.
- **M3 MVP:** implement P0 functionality and pass acceptance tests.

Do not invent due dates until estimates and resource availability are known.

## Issue readiness and done

**Ready:** clear objective, related SRS IDs, acceptance criteria, dependencies, and PoC/test plan where relevant.

**Done:** evidence provided, criteria met, reviewed/accepted, and documentation updated. A PR merge alone is not enough for a research or requirements Issue.

## Pull request workflow

- One main concern per PR; link the motivating Issue.
- Use a draft PR while incomplete.
- Explain the change, risks, tests and limitations.
- Prefer squash merge after review; branch from `main`.
- Use `Closes #N` only for issues actually completed by the merged PR.

## Requirements changes

When changing a P0 requirement:
1. Explain the reason and user impact in an Issue/PR.
2. Preserve existing requirement IDs if possible; mark removed IDs as superseded rather than silently reusing them.
3. Update linked acceptance tests and impacted Issues.
4. Record unresolved technical claims as `[待验证]` until a PoC confirms them.

## Sync-specific safety gate

Any change to remote writes or format adapters must include tests demonstrating:
- Local files survive failures.
- Conflicts are not silently overwritten.
- Unsupported/truncated Notion content does not trigger destructive replacement.
- Base is advanced only after a verified successful synchronization.
