---
type: research
category: similar-game
game: "[[Mutant Pet Lab]]"
reviewed: 2026-10-20
status: active
tags:
  - research
  - similar-game
---
# Feature Comparisons (similar games vs MPL)

> Research-level. Owner references ([[Owner Reference Library]]) outrank everything here. Ideas become **candidates** in [[Design Decisions#Candidates to confirm (not approved decisions)]], never decisions by themselves.

## By system
| System | Best examples | What they do | MPL today | Gap? |
|---|---|---|---|---|
| **Breeding / mutation** | Slime Rancher (largos), Dragon City, MSM | A pair → offspring; hybrids **look like both parents** (largos) | 30 recipes + 4 secrets; inheritance table planned ([[Creature Visual Language Spec]]) | Make inheritance visible on the 36 models (planned in 2C) |
| **Eggs / incubation** | DragonVale, MSM, Build a Zoo, owner R4/R5/R8/R9 | Separate nursery with upgradeable slots; eggs placed **physically**; odds shown at the egg | Incubators on the plot; Egg Shop panel | Physical egg pedestals with odds card (R5/R8); tap-to-crack (R4) |
| **Hatch presentation** | Owner R4, R9; Sol's RNG; BGSI | Player-triggered crack; intensity scales with rarity/egg; stat card | Approved hybrid tiers ([[Hatch Storyboard]]), not built | Build 2E; add tap-to-crack + darkened backdrop for high tiers |
| **Ranch / habitat** | DragonVale, Dragon City, Viva Piñata, Slime Rancher | Element-matched habitats; preferences shape the space | Pens + habitats + wellbeing | Visible preference reactions; species-themed pen props |
| **Farming / feeding** | Slime Rancher, Grow a Garden, Dragon City | Food → output; favourite = bonus; feeding levels creatures | Crop beds, feeders, favourite food ×2 samples | Visible eat/happy reaction; samples as physical drops |
| **Plot / base** | MSM islands, Grow a Garden, Build a Zoo, Adopt Me house | Decorated, expandable, **visited by others** | 4-stage expansion + showcase | Decoration layer + visiting/likes |
| **Research / lab** | (none strong) | — | Research tree + Reactor + Mutation Lab | **MPL's unique pillar**; owner R7 suggests a hex board |
| **Discovery / index** | Owner R1, MSM, Dragon City book | Family pages, silhouettes, completion rewards | UI-C1 Index (3D previews, silhouettes) | Family completion rewards (R1 CLAIM) |
| **Social visiting** | MSM, Grow a Garden, Adopt Me | Visit, like, flex | Plots are public in a shared server; no likes | Gap |
| **Creatures in the world** | Adopt Me, Bee Swarm, Slime Rancher, Dragon Adventures | Pets follow, react, sleep, have personality | CREATURE-C1 + procedural idle | Follow-me pet; eat/sleep/react behaviours (2D) |

## UI structure (compared with Direction C)
| Question | Similar games / owner refs | Direction C (UI-C1) |
|---|---|---|
| Where is navigation? | BGSI: **right vertical rail** + top-left tiles (R6); PS99: bottom Items/Pets + top-right Rebirths/Quests (R5); Dragon City/MSM: bottom bar | Side rails, bottom clear. Supported by R6 |
| How much stays on screen? | Popular sims stack currencies + boosts (noise); the owner-liked R5 shows a quest panel + tutorial bar | Compact pod + rails + toast; the guide tracker hides in panels |
| Task board | PS99 right-side Quests panel always visible (R5) | Lab Task Board (panel) + guide tracker. Candidate: a tiny pinned "current task" chip on the HUD |
| Index layout | Owner R1: family pages + completion rewards | 3 tabs + grid + focal detail; family pages/rewards are a candidate |
| Creature inventory | Adopt Me/PS99 grids with equip; owner R11/R13 viewers | Creatures panel (cards); a viewer with Idle/Move tabs is a candidate |
| Shop | Owner R2: hero banner with renders + odds; R8 physical eggs; R5 proximity odds | Egg Shop panel (odds bar, contents strip) |
| Research tree | Owner R7 hex board | 3-column node grid; hex board is a candidate |
| Build mode | Owner R3: grid sizes, rotate/✓/cancel, undo rail | Drag → release → ROTATE/PLACE/CANCEL; grid sizes + undo are candidates |

## Creature presentation (feeds [[Creature Overhaul]])
| Aspect | Strongest examples | Lesson for MPL |
|---|---|---|
| Body proportions | Adopt Me (big heads), Build a Zoo / Raise Animals (chunky voxel, premium) | C1's chibi proportions match; a voxel finish is a possible **material** route that hides part construction |
| Face style | Adopt Me, PS99, owner R4 bunny | Big glossy eyes + highlights: matches the approved [[Creature Face Language]] |
| Animation | Owner R11/R13, Slime Rancher | Always moving; showcase from all angles; personality per species |
| Rarity detail | Build a Zoo mutations, owner R9/R10 | High rarity = extra anatomy + aura/platform; owner eggs show it via cages, halos, wings |
| Idle behaviour | Adopt Me sleeping, Slime Rancher bouncing | Sleep/eat/react states (2D) |
| Alive in the world | Bee Swarm, Adopt Me follow | A "favourite follows you" pet (candidate) |
| Variants | Adopt Me Neon, Build a Zoo mutations | MPL variants are subtle; **strengthen** (candidate) |
| Mutation outcome | Slime Rancher largos | Show both parents' features (planned) |

## Hatching and mutation examples
| Moment | Example | Source |
|---|---|---|
| Anticipation | Lava cracks spreading over a dark backdrop | Owner R9 (0.9–2.8 s) |
| Player-triggered crack | "Tap to open!" | Owner R4 (0.6 s) |
| Rarity reveal | "LEGENDARY!" + name + rarity/chance + description + one button | Owner R9 (4.7 s) |
| Discovery label on the creature | "New pet discovered! Pig 1 in 7" over the pet in the world | Owner R5 (10.2 s) |
| Escalation by egg | Inferno vs basic; Voidheart/Celestial premium eggs | Owner R9, R10 |
| Fusion/mutation transformation | Largo forms when a slime eats another's plort | Slime Rancher (trailers, community) |
| World reaction | MPL's own Reactor plan is stronger than anything found | [[Mutation Storyboard]] |

[[Similar Games Overview]] · [[Similarity Matrix]]
