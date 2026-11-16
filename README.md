# Prod Echo

Rebuild the screens UiPath bots use, over a copy of the data they use, so agents can be tested
without production and without waiting on app teams. Start with `docs/01-problem-statement.md`,
then `docs/02-architecture.md`, then `docs/03-plan.md`.

## Working in VS Code with Claude Code

- `CLAUDE.md` at the repo root is loaded automatically; it holds the working agreement, hard
  constraints and stack. Keep it short and keep it true.
- `.claude/commands/*.md` are slash commands: `/next-item`, `/finish-item`, `/review-item I-04`.
- The plan is strictly sequential. One item per branch, one PR per item, `/review-item` before merge.

## Setup (once I-00 exists)

```
uv sync
uv run playwright install chromium
uv run echo --help
uv run pytest
```

## Repository map

See the "Repository layout" section of `CLAUDE.md`. Contracts live in `docs/04-data-contracts.md`
with examples under `specs/`; decisions under `docs/adr/`; finished work under `docs/CHANGELOG.md`.

## What must never be in this repo

Production hostnames, connection strings, credentials, real customer data, real capture files.
Fixtures come from the local harness. Real sample files (a XAML, a log export) are reviewed for
selectors and values before being checked in, and only if the team agrees they carry no PII.
