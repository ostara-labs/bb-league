# bb-league

A responsive web companion for a **Blood Bowl league campaign**: the league's
scorekeeper and team manager. It runs seasons (divisions, fixtures,
standings), keeps teams (drafting, treasury, staff), records match days, and
tracks player progression (experience, injuries, level-ups) — so coaches
never do bookkeeping by hand. It organizes and records; it never simulates
the tabletop game.

Grounded in the current official ruleset: Blood Bowl — Third Season Edition
(BB2025). The domain rules and glossary live in
[docs/domain/](docs/domain/README.md).

[![CI](https://github.com/ostara-labs/bb-league/actions/workflows/ci.yml/badge.svg)](https://github.com/ostara-labs/bb-league/actions/workflows/ci.yml)
[![Security](https://github.com/ostara-labs/bb-league/actions/workflows/security.yml/badge.svg)](https://github.com/ostara-labs/bb-league/actions/workflows/security.yml)
[![Release](https://img.shields.io/github/v/release/ostara-labs/bb-league)](https://github.com/ostara-labs/bb-league/releases)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/ostara-labs/bb-league/badge)](https://api.scorecard.dev/projects/github.com/ostara-labs/bb-league)

## What the app does (planned)

| Area | Scope |
|---|---|
| Season | Leagues and divisions, fixtures, automatic standings, play-offs, end-of-season re-draft |
| Team | Guided draft within the 1,000,000 gp budget, live team-value computation, treasury and staff |
| Match day | Step-by-step pre-game sequence, one-screen result entry, automatic post-game processing (winnings, fans, SPP, injuries) |
| Progression | Level-ups and skill choices, persistent injuries, journeymen, hiring/firing |

## What's inside

| Area | Contents |
|---|---|
| Stack | `typescript/` — web app package `@ostara-labs/bb-league` (Node 22 + pnpm, Biome, vitest) |
| Tooling | GNU Make, gitleaks, Conventional Commits, release-please |
| CI/CD | GitHub Actions: aggregate CI (devtools), security scan, release automation |
| Governance | AGENTS.md, CONTRIBUTING.md, SECURITY.md, CODE_OF_CONDUCT.md, ADRs |

## Getting started

1. Clone with submodules: `git clone --recurse-submodules <url>` (or run
   `git submodule update --init` in an existing clone).
2. Install dependencies and hooks: `make deps && make hooks` — hooks are
   the devtools git hooks (pre-commit, commit-msg, pre-push).
3. Run the full gate: `make ci`.

## Commands

| Target | What it does |
|---|---|
| `make help` | List all targets |
| `make hooks` | Activate the devtools git hooks |
| `make deps` | Install dependencies |
| `make format` | Format code |
| `make lint` | Biome + tsc --noEmit |
| `make test` | Vitest |
| `make build` | tsc build |
| `make ci` | `lint` + `test` — the full local gate |
| `make clean` | Remove build artifacts |

## Requirements

- GNU Make >= 4
- Node 22 + pnpm (via corepack)
- **Windows:** `choco install make` for GNU Make >= 4, and Git Bash in PATH —
  the Makefile recipes are POSIX. Line endings are enforced as LF by
  `.gitattributes`.

## Documentation

- MANIFEST.md — file inventory
- CONTRIBUTING.md — setup, conventions, PR process
- docs/domain/ — the Blood Bowl league domain: glossary and one concept doc
  per core area (league, team, player, match)
- docs/architecture/ARCHITECTURE.md — layout rationale and CI/CD flow
- docs/guidelines/ — engineering principles (coding-patterns.md)
- SECURITY.md — supported versions and vulnerability reporting

## License

MIT — see LICENSE.
