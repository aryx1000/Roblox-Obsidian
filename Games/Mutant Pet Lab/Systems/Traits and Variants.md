---
type: system
game: "[[Mutant Pet Lab]]"
status: live
system: traits
tags:
  - mutant-pet-lab
  - system
updated: 2026-10-22
source: tools/vault_export.py
generated: true
---
%% BEGIN GENERATED %%
# Traits and Variants

Rolled **server-side** when a creature is created (hatch, mutation, specimen claim) by `Services/CreatureFactory` using an engine-seeded `Random` (Checkpoint E). Before that, rolls were predictable from pet ids — see [[Known Issues]] (fixed).

## Traits (uniform, 1 in 8)

| Trait | Effect |
|---|---|
| Calm | Consumes food more slowly. |
| Curious | Produces a little extra research. |
| Vigorous | Produces biological samples more efficiently. |
| Adaptive | Remains stable in non-preferred habitats. |
| Volatile | Can unlock unstable research reactions. |
| Radiant | Increases research prestige from samples. |
| Insulated | Thrives in thermal or cryogenic conditions. |
| Forager | Favorite foods yield an additional sample chance. |

## Variants

| Variant | Base chance | Sample multiplier |
|---|---|---|
| Luminous | 8.0% | ×1.12 |
| Chromatic | 2.5% | ×1.22 |
| Prismatic | 0.6% | ×1.45 |

Each variant band gets a rarity boost: Common +0.0%, Uncommon +0.3%, Rare +0.7%, Epic +1.2%, Legendary +2.0%, Mythic +3.0%. The Unstable Egg adds +0.8% per band and a 25% Volatile trait bias ([[Egg Families]]).

Secret mutations use traits/variants as conditions: Radiant → [[Biolume]], Volatile → [[Chimerax]], any variant → [[Nullmorph]] ([[Mutation Recipes]]).
%% END GENERATED %%

## Notes
