---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: creatures
status: experimental
species: "[[Sparkbug]]"
plan: Flyer
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - phase-2
  - creature-prototype
---
# Sparkbug — Flyer prototype

> [!warning] EXPERIMENTAL / CANDIDATE (built 2026-10-16, overnight session)
> The direction (Studio parts, silhouette-first, one mutant accent, one signature feature) is approved in [[Design Decisions]]. **These specific looks are not approved yet** — they wait for the owner's look review. Template: `ReplicatedStorage.MutantPetLab.Creatures.Species.Sparkbug` (editable in Studio).

| | |
|---|---|
| Plan | Flyer |
| Rarity | Uncommon |
| Parts in template | 18 (+1 rarity ring for Uncommon and up, added at runtime) |

## Silhouette
Round-headed bug hovering ~2 studs up: two long glass wings, two antennae with balls on top, a striped abdomen behind.

## Proportions
Head 1.05; thorax 1.3; abdomen 1.7 long. Wings 1.7 × 1.05. Hovers 1.6 studs (plan Hover).

## Colour
Navy (44, 52, 92) and bee yellow (255, 208, 60); wings pale blue glass; antenna tips cyan Neon; stinger yellow Neon.

## Material
SmoothPlastic; Glass wings 35% transparent.

## Signature anatomy
**Glass wings** that flap fast (14 Hz, Role Wing) + **antennae**.

## Mutant feature
**Neon antenna tips + glowing stinger** (Role Glow).

## Animation implications
Flyer plan: hover with a slow float bob; wing flap; drifts when moving. Wings currently pivot about their centre — a hinge at the body is a later refinement.

## Lineage
Parent of Bloomtail (antennae → stamen), Circuitfin (static wings → fins), Radisprout, Tidegill (charged shimmer), Fungloom (antenna fronds), Voltusk.

## Related
- [[Creature Prototypes]] · [[Creature Visual Language Spec]] · [[Creature Animation Spec]] · [[PHASE2_IMPLEMENTATION_PLAN]]
