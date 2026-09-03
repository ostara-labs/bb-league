# Player

A **player** is one member of a team roster: a position from the race's list,
a name, a stat line, skills, experience (SPP) and an injury history. Players
are the unit of progression — teams grow because players do.

## Earning SPP

Star Player Points are earned during a match:

| Event | SPP |
|---|---|
| Touchdown scored | 3 |
| Casualty caused | 2 |
| MVP award | 1 |

Some team special rules modify these values (e.g. Brawlin' Brutes swap the
touchdown and casualty values). The recorded match result must capture the
raw events; SPP computation applies team rules when known.

## Level-ups

When a player's SPP total reaches a threshold, they earn one advancement. The
coach either rolls randomly (cheaper) or chooses (more expensive), and may
pick a skill from a **Primary** category, a **Secondary** category, or a
characteristic increase.

⚠ **Threshold table below comes from a community source and must be verified
against the rulebook before being coded.**

| Level | Random Primary | Chosen Primary | Chosen Secondary | Characteristic |
|---|---|---|---|---|
| 1 | 3 | 6 | 10 | 14 |
| 2 | 4 | 8 | 12 | 16 |
| 3 | 6 | 12 | 16 | 20 |
| 4 | 8 | 16 | 20 | 24 |
| 5 | 10 | 20 | 24 | 28 |
| 6 | 15 | 30 | 34 | 38 |

Skill categories: Agility (A), General (G), Strength (S), Passing (P),
Mutation (M), Devious (D — new in BB2025). Each position lists its Primary
and Secondary categories. Characteristic increases follow the double-rule
from the rulebook.

A player's **current value** (feeding TV) increases with each advancement —
the app must recompute it, never accept a hand-entered value.

## Injuries

When a player is casualties during a match, roll on the D16 Casualty table:

| Roll | Result | Effect |
|---|---|---|
| 1-8 | Badly Hurt | None |
| 9-10 | Seriously Hurt | Miss Next Game (MNG) |
| 11-12 | Serious Injury | MNG + Niggling Injury |
| 13-14 | Lasting Injury | MNG + permanent -1 to a characteristic (see below) |
| 15-16 | Dead | Removed from the roster |

Lasting Injury (D6): 1-2 head injury -1 AV; 3 smashed knee -1 MA;
4 broken arm -1 PA; 5 dislocated hip -1 AG; 6 broken shoulder -1 ST.

A Niggling Injury adds +1 to all future casualty rolls for that player,
permanently.

The app applies injuries when the post-match result is recorded, and clears
MNG when the missed match has been played (or forfeited).

## Journeymen

If a team has fewer than 11 available players for a match, journeymen fill
the gap:

- Free temporary linemen with the **Loner (4+)** trait.
- They count toward CTV for that match.
- After the match the coach may hire one permanently (hiring fee + value
  increase); otherwise the journeyman leaves and takes their SPP with them.
- Journeymen can temporarily push a team above 16 players for one match —
  the roster bound applies again once the match is processed.

## Source

Blood Bowl Official Rulebook — Third Season Edition (GW, Nov 2025), player
progression and casualty rules; cross-checked against community summaries
(bloodbowlbase.ru, Mordorbihan BB2025 pages). The level-up threshold table
and the exact value-increase amounts are flagged for rulebook verification.
