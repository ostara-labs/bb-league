# Glossary — Blood Bowl league domain

Ubiquitous language for the app. One entry per term: definition, then what it
is **NOT** (the fastest way to kill ambiguity). These terms are used verbatim
in the UI and in the code — a term that drifts from this page is a bug.

Ruleset reference: Blood Bowl Official Rulebook — Third Season Edition
(Games Workshop, November 2025, "BB2025").

## People

| Term | Definition | Is NOT |
|---|---|---|
| Coach | A person who owns and manages one or more teams in the league. | Not a player — a Player is a member of a roster, on the pitch. |
| Commissioner | League administrator: creates the season, sets divisions, validates results. | Not necessarily a coach (may also coach). |
| MVP | Most Valuable Player award, one per team per match, worth 1 SPP. | Not chosen by the app — the coach records what the table rolled. |

## Competition structure

| Term | Definition | Is NOT |
|---|---|---|
| League | The persistent campaign format: teams keep roster, SPP and treasury between matches. | Not a tournament. |
| Tournament | One-day "resurrection" format: rosters reset after every match. Out of scope for this app. | Not a synonym for league. |
| Season | One full cycle of the league: regular season, play-offs, off-season re-draft. | Not the ruleset edition (Blood Bowl "Third Season Edition" is the rules name, BB2025). |
| Division | A group of at least 4 teams playing a round-robin inside the regular season. | Not a skill tier or ranking class. |
| Round (matchday) | A set of fixtures sharing a time window in the schedule. | Not a game turn — turns are an in-match concept the app does not simulate. |
| Fixture | A scheduled match between two teams in a round. | Not a result — a fixture exists before it is played. |
| Match | A played fixture plus its recorded result and post-game processing. | Not a game simulation; the app records, never plays. |
| Standings | Ranking of the teams of a division, derived deterministically from results. | Never entered by hand. |
| Play-offs | Knockout stage after the regular season (extra time + penalties on draws). | Not part of round-robin scoring. |
| Re-draft | Off-season rebuild: fresh budget = 1,000,000 gp + remaining treasury + season results bonus. | Not a new team identity — the coach may keep the team. |

## Teams and assets

| Term | Definition | Is NOT |
|---|---|---|
| Team | A persistent roster of players plus staff, treasury and fans, owned by a coach across the whole season. | Not a roster snapshot — a team lives and changes between matches. |
| Race | One of the 29 playable team types (Human, Orc, Skaven...), each with its own positions and re-roll cost. | Not the team name; many teams share a race. |
| Roster | The players currently on a team: 11 to 16. | Not a tournament roster sheet. |
| Position | A job type inside a race (Lineman, Blitzer...) with a stat line, a max count and Primary/Secondary skill categories. | Not a player's name. |
| Team Value (TV) | Sum of all players' current values + sideline staff + team re-rolls. | Does not include treasury or dedicated fans. |
| Current Team Value (CTV) | TV minus the value of players who miss the next game (MNG). | Not a different valuation basis — same items, MNG excluded. |
| Treasury | The team's gold reserve: winnings in, purchases out. | Not part of TV. |
| Team Re-roll | Team-level dice re-roll bought at draft (max 8); costs double when bought mid-league. | Not a player skill — it belongs to the team. |
| Sideline Staff | Assistant coaches (max 6), cheerleaders (max 6), apothecary (max 1). | Not players — never take the pitch; still count in TV. |
| Dedicated Fans | Team-level fan factor: starts at 1, up to 3 at draft, moves with results. | Not the match Gate. |
| Gate (Fan Attendance) | Attendance of one match: both teams' fan factors combined. | Not a team attribute — it belongs to a match. |

## Players

| Term | Definition | Is NOT |
|---|---|---|
| Player | One roster member: a position, a name, stats, skills, SPP, injuries. | Not the human coach. |
| SPP | Star Player Points — player experience: touchdown 3, casualty caused 2, MVP 1. | Not gold; never spendable on anything but advancements. |
| Level-up | An advancement earned when a player's SPP reach a threshold. | Not automatic — the coach rolls or chooses the advancement. |
| Advancement | A new skill or a characteristic improvement gained at a level-up. | Not free — secondary categories cost more SPP. |
| Primary / Secondary | The skill categories a position learns cheaply / expensively. | Not skills themselves — they are cost classes. |
| Skill | A learned ability belonging to a category: Agility (A), General (G), Strength (S), Passing (P), Mutation (M), Devious (D). | Not a trait — Traits (e.g. Loner) are innate and cannot be chosen. |
| Casualty | Injury rolled on the D16 Casualty table when a player is hurt. | Not every knock-out — KOs recover during the match. |
| Badly Hurt | Casualty result 1-8: no lasting effect. | Not MNG. |
| MNG (Miss Next Game) | Status excluding a player from the next fixture; excluded from CTV. | Not permanent — cleared after the missed match. |
| Niggling Injury | Permanent +1 modifier to all future casualty rolls for that player. | Not MNG by itself (comes with it). |
| Lasting Injury | Permanent characteristic reduction: -1 AV / MA / PA / AG / ST. | Not removable, not optional. |
| Dead | Casualty result 15-16: player removed from the roster. | Not recoverable. |
| Journeyman | Free temporary lineman taken when a team has fewer than 11 available players; has Loner (4+). | Not a signed player — lost with their SPP unless hired permanently post-game. |
| Star Player | Named mercenary hired for a single match. | Not a roster player — never persists between matches. |
| Inducement | Temporary bonus hired before a match, paid with treasury or petty cash. | Not a permanent purchase; never appears in TV. |

## Money and results

| Term | Definition | Is NOT |
|---|---|---|
| Winnings | Gold earned from one match and added to the treasury. | Not the Gate — Gate is attendance, Winnings are money. |
| Expensive Mistakes | D6 roll forced when treasury is 100,000+ gp post-game; may cost gold. | Not a tax — nothing happens on a good roll. |
| Concession | A coach forfeiting a fixture; opponent wins 1-0, gains D6x10,000 gp and two MVP awards. | Not the same as an unplayed fixture (which scores 0-0 as a loss for both). |
