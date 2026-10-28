---
type: research
game: "[[Mutant Pet Lab]]"
research_target: "simulator systems adjacent to MPL"
researched_on: 2026-10-15
category: topic · features
status: complete
tags:
  - research
  - features
---
# Simulator Feature Research

> Authority: REFERENCE-level research. **A feature is not recommended just because a popular simulator has it.** Every row is judged against MPL's identity: mutant creatures, ranch/property, research, mutation, eggs, habitats, feeding, index, discovery, cozy social. Labels: OBS / INF / MPL. Sources: [[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)]] and pass 1.
> Ratings are judgements (INF). "Exists in MPL" is from `current/source` and [[Economy]].

## Feature evaluation
Scale: H = high, M = medium, L = low. **Generic** = risk of becoming a generic simulator. **P2W** and **Grind** = risk of pay-to-win and grind.

| Feature | Seen in (OBS) | Fit | Fun | Complexity | Retention | Generic | P2W | Grind | MPL? |
|---|---|---|---|---|---|---|---|---|---|
| Daily / rotating research objectives | Assignments are common; GaG rotating stock | H | M | L | H | M | L | M | **YES**: rotate 3 "lab requests" from existing events (assignment system exists) |
| Creature requests / contracts | Adopt Me needs-tasks | H | M | M | M | L | L | M | **YES**: "A researcher needs a Luminous Frostpup sample", fulfilled by care, not sacrifice |
| Limited-time mutations | GaG event mutations, BGSI limited secrets | M | H | M | H | M | M | L | **MAYBE**: only as *seasonal research*, re-obtainable later; no FOMO |
| Weather / environmental conditions | GaG weather → crop mutations (S44) | H | H | M | H | L | L | L | **YES (later)**: a valley weather cycle that biases trait/variant odds or secret conditions; fits mutation |
| Biome-specific events | GaG Bee Swarm/Volcano events (S44) | H | M | M | M | L | L | L | **MAYBE**: after biomes get a function |
| Roaming rare creatures | Pet Catchers wild pets ([[Reward Burst and Wild Encounters]]); Bee Swarm wild mobs | H | H | M | M | L | L | L | **MAYBE**: "wild specimen sighting" in a biome → sample/research reward, never steal-able |
| Specimen collection | Bee Swarm pollen/fields; MPL Specimen Supply exists | H | M | L | M | M | L | M | **KEEP** (exists) |
| Creature mood / personality | Adopt Me sleeping idle; Bee Swarm "traits and personalities" (official desc., S39) | H | H | M | H | L | L | L | **YES**: idle-life + reactions; MPL has wellbeing + traits already |
| Friendship / bond | Adopt Me aging through care | H | H | M | H | L | L | M | **MAYBE**: a light bond meter that unlocks a cosmetic idle, not stats |
| Passive creature behaviour | Bee swarm moving; Adopt Me pet follows | H | M | M | M | L | L | L | **YES**: creatures wander in pens, eat, sleep |
| Expeditions | (dormant Expedition Arch exists in MPL world) | M | M | H | M | M | L | M | **MAYBE (later)**: send creatures out, return with samples; the arch is already in the map |
| Collection milestones | BGSI/PS99 indexes; Bee Swarm hive-size gates | H | M | L | H | M | L | L | **YES**: per-family Index completion → cosmetic lab decor |
| Discovery streaks | (no strong example found) | M | L | L | M | M | L | M | **NO**: streak pressure ≈ chores |
| Research milestones | MPL Research tree exists | H | M | L | M | L | L | L | **KEEP** |
| World events | GaG weather / admin events; 99 Nights cultist raids | M | H | M | H | M | M | L | **MAYBE**: scheduled, predictable "reactor surge" (bonus variant odds for 5 min); no admin-only randomness |
| Rare environmental spawns | BGSI Secret Aura Egg 1/50,000 spawn, 10 min (S45) | M | M | M | M | H | L | M | **NO** as random lottery; see roaming creatures |
| Mutation chains | MPL recipes chain to Quasipod | H | H | L | H | L | L | M | **KEEP** (exists) |
| Lineage / family tree | Dragon Adventures inheritance (S30) | H | H | M | M | L | L | M | **YES (light)**: store "parents" on mutated creatures, show in detail view |
| Creature display / showcase | MPL Featured Specimen pedestal + approved Specimen Showcase | H | M | L | M | L | L | L | **YES**: extend into visiting (see [[Social Systems Research]]) |
| Visiting friends' properties | GaG "flex fruits on friends" (official desc.) | H | M | M | M | L | L | L | **YES**: see social note |
| Social comparison without PvP | GaG neighbouring gardens | H | M | L | M | L | L | L | **YES** |
| Trading | Adopt Me trading + scam history (S12) | M | H | H | H | M | H | M | **NO** for now; only with safeguards later |
| Offline progression | GaG grows offline (official desc.); MPL offline incubation exists | H | M | L | H | L | L | L | **KEEP + IMPROVE**: a "while you were away" summary |
| Auto-feeding / automation | BGSI/PS99 auto-hatch; MPL feeders exist | M | L | L | M | H | M | L | **MAYBE**: feeder upgrades only; no auto-play |
| Rare trait hunting | MPL traits/variants; Steal An Egg sizes + mutations (official desc.) | H | H | L | H | M | M | M | **YES**: already the variant system; make variants visible |
| Cosmetic variants | Adopt Me Neon; MPL Luminous/Chromatic/Prismatic | H | H | M | H | L | L | L | **YES** |
| Seasonal research | BGSI weekly updates (official desc.) | M | M | M | H | M | M | L | **MAYBE**: content cadence, not a system |
| Secret recipes | MPL has 4 | H | H | L | H | L | L | M | **KEEP** |
| Prestige / rebirth | Steal a Brainrot, Ride A Pet, BGSI | L | L | M | M | **H** | M | **H** | **NO**: resetting a ranch contradicts the cozy-ownership fantasy |
| Quests / assignments | Bee Swarm bear quests; MPL 22 assignments | H | M | L | H | M | L | M | **KEEP + IMPROVE**: give them NPC voices |
| Daily rewards | Common (genre) | L | L | L | M | H | L | L | **NO** (or a tiny one): reads as mandatory chores |

## World interaction vs menu interaction
**What the successful games keep in the world (OBS/INF across examples):**
- **Shops:** GaG egg/seed stands; Adopt Me Nursery gumball; Steal a Brainrot conveyor.
- **Eggs and incubation:** GaG eggs in the garden; Steal An Egg nests.
- **Fusion/mutation:** Adopt Me Neon Cave; GaG mutation machine.
- **Social:** Ride A Pet friend station.
- **Creatures** themselves.

**What stays in menus:**
- Collection/index.
- Inventory lists.
- Detailed stats and odds.
- Settings.
- Long trees.

**Where MPL leans too heavily on panels (INF from `current/source` controllers):**

| MPL action | Today | Suggested split |
|---|---|---|
| Hatch | Panel reveal | World anticipation + card ([[Egg Hatching Research]]) |
| Mutation | Panel result card | Reactor reveal + card ([[Mutation Reveal Research]]) |
| Assign creature to pen | Select pen → panel → choose → ASSIGN | Keep the panel, plus the creature walks in |
| Harvest crop | Select bed → panel → HARVEST | A direct prompt/tap on a ripe bed |
| Collect bio-assay | Select pen → COLLECT | A direct prompt; the vial arcs to the HUD |
| Load feeder | Select feeder → LOAD | Keep the panel (it is a choice) |
| Egg Shop | Panel at the counter | Eggs displayed physically + panel |
| Research | Panel at the terminal | Keep (it is a tree), plus world unlock previews |
| Index / Creatures / My Lab | Panels | Keep |

## Sources
[[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)]] · priority matrix: [[Roblox Market Research#Simulator feature priority matrix]]
