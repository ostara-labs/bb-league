# League and season

The app exists to run a **league**: the persistent Blood Bowl campaign format
where teams keep their roster, their experience and their treasury from match
to match. This is what a "season" of the campaign means.

This app does **not** manage tournaments (resurrection format — rosters reset
after every match). See the glossary for the distinction.

## Season lifecycle

A season has three phases, in order:

1. **Setup** — the commissioner creates the season, coaches (re-)draft their
   teams, teams are grouped into divisions, the fixture list is generated.
2. **Regular season** — each division plays a round-robin: every team meets
   every other team of its division (once or twice, commissioner's choice).
   Rounds have a time limit (recommended: one match per week or two weeks).
3. **Play-offs** — knockout stage for the top teams of each division
   (how many qualify: commissioner's choice). Draws are resolved with the
   Extra Time and Penalties rules. The final decides the season champion.

After the play-offs comes the **off-season**, which ends with the re-draft
for the next season (see below).

## Regular season

### Divisions

- A division holds at least 4 teams.
- The commissioner assigns teams to divisions.
- Friendly cross-division matches may be played on a challenge basis; they do
  not affect standings.

### Scoring

| Result | League points |
|---|---|
| Win | 3 |
| Draw | 1 |
| Loss | 0 |

Optional bonus points (commissioner's discretion):

- Score 3+ touchdowns in a match: +1
- Concede 0 touchdowns in a match: +1
- Cause 3+ SPP-generating casualties in a match: +1

### Tie-breakers

When teams are level on league points: 1) total touchdowns scored,
2) total casualties caused.

### Unplayed fixtures and concessions

- A fixture not played within its time limit counts as a **loss for both
  teams** (0-0).
- A coach who **concedes** forfeits the match without further penalty: the
  opponent records a 1-0 win, gains D6 x 10,000 gp, and may award two MVPs.

## Off-season re-draft

Between seasons, each coach rebuilds their team with a fresh budget:

```
budget = 1,000,000 gp + remaining treasury
       + 20,000 gp per fixture played last season
       + 20,000 gp per fixture won
       + 10,000 gp per fixture drawn
```

The re-draft is why the app starts cleanly at season 3: every coach
(re)creates their team in the app during setup, no retroactive data entry.

## Invariants

- Every fixture produces exactly one recorded result — played, conceded, or
  double forfeit. Nothing else.
- Standings are always derivable from recorded results alone. The app never
  stores standings; it computes them.
- A season's regular season ends when every fixture of every round has a
  result. Play-offs open only then.
- League points, tie-breaker counts and bonuses are computed from match
  records, never entered manually.

## Edge cases

- Both coaches fail to play: double forfeit, both take a loss.
- A team dissolves mid-season (all players dead, coach quits): commissioner
  marks it withdrawn; its played results stand, its remaining fixtures count
  as 1-0 wins for the opponents (rulebook: verify exact treatment).
- Odd number of teams in a division: one bye per round; a bye is not a win.

## Source

Blood Bowl Official Rulebook — Third Season Edition (GW, Nov 2025), league
play rules; cross-checked against community summaries (bloodbowlbase.ru,
BB2025 pages). Items marked "verify" were not confirmable from secondary
sources and must be checked against the rulebook before coding.
