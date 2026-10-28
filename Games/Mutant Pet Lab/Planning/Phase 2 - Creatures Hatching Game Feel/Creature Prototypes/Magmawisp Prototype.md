---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: creatures
status: experimental
species: "[[Magmawisp]]"
plan: Wisp
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - phase-2
  - creature-prototype
---
# Magmawisp — Wisp prototype

> [!warning] EXPERIMENTAL / CANDIDATE (built 2026-10-16, overnight session)
> The direction (Studio parts, silhouette-first, one mutant accent, one signature feature) is approved in [[Design Decisions]]. **These specific looks are not approved yet** — they wait for the owner's look review. Template: `ReplicatedStorage.MutantPetLab.Creatures.Species.Magmawisp` (editable in Studio).

| | |
|---|---|
| Plan | Wisp |
| Rarity | Epic |
| Parts in template | 13 (+1 rarity ring for Uncommon and up, added at runtime) |

## Silhouette
Floating flame drop: round core in a taller flame shell with a flame tip on top, three dark stone shards orbiting around it. No ground contact.

## Proportions
Core 1.4; shell 2.0 × 2.3; floats 1.7 studs up; shards orbit at 1.75 studs. Epic scale ×1.2.

## Colour
Core (255, 140, 40); shell (255, 90, 30) 55% transparent; tips yellow-orange; shards dark basalt (62, 46, 44); dark eyes with white shine.

## Material
Neon core/shell/flames; Basalt shards.

## Signature anatomy
**Orbiting stone shards** (Role Orbit, spin and tumble).

## Mutant feature
**Neon core inside a flame shell** (Role Glow).

## Animation implications
Wisp plan: floating bob (0.3 at 1 Hz), orbit 1.6 rad/s. Spec mentions a shadow disc; not built, because the whole model floats and Roblox already casts a shadow (Candidate deviation).

## Lineage
The first mutation (Slimelet + Rockling): **gel core from Slimelet, stone shards from Rockling.** Parent of Fluxaroo (molten glow).

## Related
- [[Creature Prototypes]] · [[Creature Visual Language Spec]] · [[Creature Animation Spec]] · [[PHASE2_IMPLEMENTATION_PLAN]]
