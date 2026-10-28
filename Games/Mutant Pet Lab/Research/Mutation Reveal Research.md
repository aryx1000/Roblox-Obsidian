---
type: research
game: "[[Mutant Pet Lab]]"
research_target: "mutation / fusion / evolution reveals"
researched_on: 2026-10-15
category: topic · mutation
status: complete
tags:
  - research
  - mutation
---
# Mutation Reveal Research

> [!success] Decision outcome
> Owner decision 2026-10-16: **the interaction stays at the Mutation Machine;** the Reactor responds (Machine → cable pulse → Reactor → result). **Discovery notices default OFF.** See [[Design Decisions]] (*Phase 2:* entries) and [[Mutation Reveal Spec]].

> Authority: REFERENCE-level research. Nothing here is approved. Labels: OBS / INF / MPL. Sources: [[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)]].

## MPL today (from `current/source`)
- **Where:** The Mutation Lab panel opens at the campus `MutationMachine`. The approved map plan adds the **Mutation Reactor** as the central landmark ([[Design Decisions#Map: Mutation Reactor approved as the central landmark]]).
- **Rules:**
  - Two owned, unassigned creatures + Research → **both parents are consumed** → the result is added instantly.
  - First discovery grants extra rewards.
  - Secret recipes have server-side conditions (trait/variant/care/research).
  - A failed secret attempt costs **nothing** and returns a category message + the recipe's hint.
- **Reveal:** A result card in the panel (purple tile) and a status line. There is no world event and the reactor doesn't participate.
- **Information:** A normal recipe becomes visible in the Index once **both parents are discovered**. Secrets show only a hint. Unknown species show "???".

## Examples
| Game | Mechanic | OBS | Why it works | Annoying / risky |
|---|---|---|---|---|
| [[Adopt Me]] **Neon Cave** | 4 full-grown pets of one kind on 4 coloured circles → **fusion animation** → Neon pet appears in the central circle; irreversible; the result is a newborn again (S42) | A **physical ritual place** (hidden cave under a bridge); you watch your pets step in | Visible inputs → visible output in the world; the place itself is memorable | Consuming 4 (later 16) pets; reset to newborn |
| [[Grow a Garden]] **Pet Mutation Machine** | Pet must be level 50; 500M Sheckles; **1 hour** processing; random mutation; the pet returns with a **new appearance + ability** and reset to level 1. Re-roll replaces the old mutation. Guides cite a 49-Robux skip (S43) | The machine sits next to the Egg Shop; the reveal is collecting the changed pet | Visual change on the pet itself is the payoff | Hour-long wait + paid skip; pure randomness; level reset; the community-listed odds conflict |
| Grow a Garden **weather mutations** | Rain → Wet, Thunderstorm → Shocked, Frost → Chilled/Frozen, Blood Moon → Bloodlit, Meteor → Celestial; big value multipliers (S44) | The **environment** causes the mutation, and everyone sees the weather | Shared world events that create surprise and talk | Admin-only events with no schedule (S44) feel random |
| [[Bee Swarm Simulator]] **Royal Jelly** | Use on a bee → re-rolls it (≈70% Rare / 27% Epic / 3% Legendary; small Gifted/Mythic chance); can *downgrade* a Legendary (S49) | Fast re-roll on the hive slot | A cheap gamble on one slot | Can make a bee worse, which feels bad (OBS: wiki notes the same odds regardless of input) |
| [[Dragon Adventures]] **breeding** | Offspring inherit element, stats and colour mutations from both parents (S30, D-source) | Lineage you can see | Results feel authored by the player | Grind for perfect lineages |
| [[Sol's RNG]] **crafting** | Craft gear from collected auras (official description, S39) | Collection feeds crafting | Turns duplicates into progress | Gear-as-multiplier |

## Patterns: how reveals create each feeling
- **Anticipation:** a place and a ritual. You walk your creatures in, put them on pads, and the machine powers up (Neon Cave, GaG machine).
- **Uncertainty:** must be *bounded*. Players accept surprise in **appearance/variant**, but dislike losing value (Royal Jelly downgrade; GaG mutation replacement). INF from OBS mechanics + guide warnings.
- **Visual transformation:** the result **looks different on the creature** (GaG new appearance, Neon glow).
- **Result reveal:** happens at the place, not in a menu.
- **Rare-result excitement:** shared visibility, e.g. weather everyone sees, server notices ([[Sol's RNG]], S46).
- **First-discovery payoff:** reserved for the first time only, so it never gets old (Sol's RNG cutscene threshold pattern).

## How the Mutation Reactor could take part (candidates, not decisions)
Fits the approved reactor (visual landmark; terminal moved to its front). All visual-only hooks on existing server events; no new logic required for v1.
1. **Pads at the reactor:** Two specimen pads on the reactor dais, and the creatures walk onto them.
   - Panel flow stays the same: pick → confirm → MUTATE.
   - The world shows the creatures entering.
   - *Spatial change:* the Mutation Lab interaction moves next to the reactor. That needs an owner decision and an `APPROVED_MOVES` entry; the prompts are frozen geometry today.
2. **Charge-up (~2 s):** The reactor core spins up, and green → purple light runs up the pylons. The parents dissolve into light streams that meet at the core.
3. **Reveal:** The core flashes. The result materialises on the dais in a silhouette → colour flood. The card shows: name, rarity, trait, variant, and **"from Slimelet + Rockling"** with both parent icons.
4. **First discovery:** The reactor crown emits a beacon visible from every plot (sight lines already guaranteed by the map plan). There is a soft server notice "A new species was discovered: Magmawisp". It can be toggled off.
5. **Secret discovery:** Same, with a sky tint in the species' colour for a few seconds. The rarest moment in the game, and it happens only once per player per species.
6. **Failed secret attempt:** The reactor sputters (a short fizzle animation) and the hint appears as a "lab note". It makes failure feel like *research progress*, not an error. It still costs nothing, as today.
7. **Ambient:** The reactor brightness slowly scales with the server's total discoveries this session, a cheap social signal.

## Evolution / growth
- MPL has no growth stages. Adopt Me!, Creatures of Sonaria and Dragon Adventures use them (OBS, pass 1). This is a large scope; it stays in [[Creature Overhaul]] open questions. **Not recommended now.**

## What MPL should avoid
- Hour-long processing timers with paid skips (GaG).
- Random outcomes that can *lower* value (Royal Jelly downgrade, GaG mutation replacement).
- Level resets after a mutation.
- Consuming many creatures for one result (4 → 1 → 16 → 1). MPL's 2 → 1 is already moderate.

## Sources
[[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)]]
