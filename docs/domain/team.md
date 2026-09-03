# Team

A **team** is the persistent asset of the campaign: one coach, one race, a
roster of players, sideline staff, treasury and fans. Everything the app
tracks between matches hangs off the team.

## Drafting a team

At season setup (the re-draft), a coach builds their team from a budget of
1,000,000 gp (plus bonuses — see [league.md](league.md)):

| Item | Rules |
|---|---|
| Players | 11 to 16, hired from the race's positions at their hiring fee; each position has a max count (e.g. 0-2 Blitzers) |
| Team re-rolls | Max 8, cost depends on the race; **double cost** when bought mid-league |
| Assistant coaches | Max 6, 10,000 gp each |
| Cheerleaders | Max 6, 10,000 gp each |
| Apothecary | Max 1, 50,000 gp |
| Dedicated Fans | Start at 1; may buy up to 2 more at draft, 5,000 gp each (max 3) |

The app must compute the total cost live while drafting and **block any
overspend** — a draft that exceeds the budget is not submittable.

## Team Value

Two derived numbers matter all season long:

- **TV (Team Value)** = sum of all players' current values + sideline staff
  + team re-rolls. Dedicated fans and treasury are NOT included.
- **CTV (Current Team Value)** = TV minus the current value of players who
  miss the next game (MNG). CTV is what inducement balance is computed from
  on match day.

Invariants:

- TV and CTV are recomputed at the end of every post-game sequence; the app
  never stores a hand-entered value.
- Roster size stays within 11..16 at all times.
- Players with MNG count in TV but not in CTV.

## Dedicated Fans

Fan factor moves with results, in the post-game sequence:

- Winning coach rolls D6: on a roll >= current fan level, +1 fan.
- Losing coach rolls D6: on a roll < current fan level, -1 fan.

## Treasury

- Winnings from each match are added to the treasury immediately
  (see [match.md](match.md)).
- The treasury pays for: new players, staff, re-rolls (double price
  mid-league), and match-day inducements.
- **Expensive Mistakes**: if the treasury holds 100,000+ gp at the end of the
  post-game sequence, roll D6 on the Expensive Mistakes table — the team may
  lose gold. (Full table: rulebook.)

## Hiring and firing

Happens in the post-game sequence, in this order:

1. Hire new players (positions, costs as at draft).
2. Fire existing players.
3. Journeymen who played may be hired permanently at their hiring fee plus
   any value increase; otherwise they leave with their SPP.

Roster bounds (11..16) apply after the sequence.

## Source

Blood Bowl Official Rulebook — Third Season Edition (GW, Nov 2025), team
drafting and league play rules; cross-checked against community summaries
(bloodbowlbase.ru, BB2025). Firing edge cases and the Expensive Mistakes
table must be verified against the rulebook before coding.
