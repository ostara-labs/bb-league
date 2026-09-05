# Match day

The app does not simulate Blood Bowl. It **accompanies the real match**:
guides the pre-game sequence at the table, records the result, then runs the
post-game sequence so that coaches never do bookkeeping by hand.

## Pre-game sequence

Run at the table, guided screen by screen:

1. **The Fans** — each coach rolls D3 and adds their Dedicated Fans level:
   this is their Fan Factor for the match.
2. **The Weather** — both coaches roll D6, sum consulted on the Weather
   table: 2 Sweltering Heat, 3 Very Sunny, 4-10 Nice, 11 Pouring Rain,
   12 Blizzard.
3. **Journeymen** — a team with fewer than 11 available players takes free
   journeymen up to 11 (see [player.md](player.md)).
4. **Inducements** — the team with the lower CTV receives petty cash equal
   to the difference; both coaches may hire Star Players and inducements.
5. **Kicking team** — coin toss (or dice) decides who kicks.

The app computes Fan Factor and petty cash from stored team data; the coach
only enters dice results.

## What gets recorded

After the match, one screen captures everything the post-game sequence needs:

- Touchdowns scored by each team.
- Casualties caused by each team (only those that generate SPP).
- Which players scored, caused casualties, and died (per player detail).
- MVP award for each team (one per team).
- Casualty results rolled for injured players (D16 results, or at minimum
  the outcome per player).
- Concession flag (if applicable).

## Post-game sequence

Processed by the app, in rulebook order:

1. **Record outcome and winnings** — Fan Attendance (Gate) is the two Fan
   Factors combined; winnings are computed and added to the treasury
   (formula: ((Fan Attendance / 2) + touchdowns + 1) x 10,000 gp — exact
   clause to verify against the rulebook). On concession: opponent wins 1-0,
   gains D6 x 10,000 gp and two MVP awards.
2. **Update Dedicated Fans** — winners roll to gain a fan, losers roll to
   lose one (see [team.md](team.md)).
3. **Player advancement** — SPP totals update; players past a threshold are
   flagged for a level-up decision (rolled or chosen advancement).
4. **Hiring, firing, journeymen** — new players hired, unwanted players
   fired, journeymen signed or released.
5. **Expensive Mistakes** — treasury >= 100,000 gp triggers the D6 roll.
6. **Recompute TV and CTV** — MNG status updated for the next fixture.

## Invariants

- One recorded result per fixture, exactly once. Re-editing a processed
  match requires a commissioner action (which replays the affected
  post-game effects) — never silent mutation.
- Each team receives exactly one MVP per match.
- Injuries recorded in step 1 are applied by step 3; a dead player cannot
  receive a level-up the same match.
- MNG set in a match is cleared when that player's team completes its next
  fixture, whatever the result.
- TV/CTV after processing are functions of the team state — never inputs.

## Edge cases

- Draw in a regular-season fixture: 1 league point each, both coaches roll
  for fans (a draw counts as neither win nor loss).
- Match played out of schedule order: record against the fixture it
  belongs to; standings stay consistent because they derive from results.
- Player dies and the team drops below 11: journeymen fill the next match —
  the app must suggest them at pre-game.

## Source

Blood Bowl Official Rulebook — Third Season Edition (GW, Nov 2025), match
sequence and league play rules; cross-checked against community summaries
(bloodbowlbase.ru, BB2025). The winnings formula clause and concession
details are flagged for rulebook verification.
