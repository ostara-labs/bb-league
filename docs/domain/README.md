# Domain

The business domain of bb-league: a Blood Bowl league campaign companion.
These documents describe the rules the app implements — the concepts of the
problem space, independent of any implementation. The code is the source of
truth for behavior; these files are the source of truth for vocabulary.

Ruleset: Blood Bowl — Third Season Edition (Games Workshop, November 2025,
"BB2025"), supplemented by the official FAQ/errata (latest: May 2026).
Values not confirmed against the rulebook are flagged inline.

## Reading order

| File | What it covers |
|---|---|
| [glossary.md](glossary.md) | Ubiquitous language: one entry per term, definition, and what it is NOT |
| [league.md](league.md) | Season lifecycle: setup, regular season, scoring, tie-breakers, play-offs, re-draft |
| [team.md](team.md) | Team drafting, team value (TV/CTV), dedicated fans, treasury, hiring and firing |
| [player.md](player.md) | SPP, level-ups, skill categories, injuries, journeymen |
| [match.md](match.md) | Match day: pre-game sequence, recorded result, post-game sequence, invariants |

## Why it matters

- Onboarding: a new contributor (human or AI agent) reads the domain docs
  before the code and asks 10x better questions
- Naming: arguments about names are really arguments about concepts;
  writing them down settles them once
- Boundaries: concepts that keep appearing together hint at module
  boundaries

## Relationship to code

Domain docs describe the problem; the code implements a solution. They can
legitimately diverge — but if the *vocabulary* diverges (same word means
different things in docs and code), treat it as a bug and fix it.
