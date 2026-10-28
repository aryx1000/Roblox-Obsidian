---
type: planning
game: "[[Mutant Pet Lab]]"
status: approved-direction
tags:
  - mutant-pet-lab
  - planning
  - creatures
updated: 2026-10-16
source: "SpeciesConfig"
---
# Creature Overhaul

> [!danger] OWNER FEEDBACK 2026-10-16 (real-device review) — visual direction correction
> **CURRENT 7 CREATURE PROTOTYPES ARE EXPERIMENTAL AND NOT APPROVED AS THE FINAL CREATURE STYLE.**
> **CURRENT BOTTOM NAVIGATION LAYOUT IS NOT APPROVED.**
> Observed problems: creatures still look like primitive Roblox parts assembled together and not like polished collectible pets; the UI is colourful but bland and developer-like; the large bottom nav takes too much of the phone screen; the HUD is too large; panels read as admin/card lists; the saved references must be used much more strongly.
> The owner wants: stronger simulator-style presentation, better use of the saved references, navigation moved to the sides (no large bottom bar), and creatures that look like actual pets/organisms.
> **Do not build the remaining 29 species. Do not migrate every panel again. Do not publish.** Next step: 3 UI directions + 3 directions each for Frostpup, Mossbit, Sparkbug, then wait for the owner's choice.
>
> **Review ready (2026-10-16):** [[Visual Direction Review 2026-10-16]]: 3 side-rail UI directions (recommended C) + 3 directions each for Frostpup / Mossbit / Sparkbug (recommended C) + [[Creature Face Language]]. Waiting for the owner's selection.
>
> **C1 review stage (2026-10-16):** [[C1 Review Stage 2026-10-16]]: UI-C1 (side rails, status pod, Lab Task Board, Index with 3D previews) and CREATURE-C1 (7 representatives rebuilt). Waiting for owner review; 29 species not built.


## Scheduling (2026-10-15)
> [!info] Phase 1 (UI + map) is complete. Creature visual direction is **approved** (2026-10-16, [[Design Decisions]]).

> [!note] **Started 2026-10-16 (overnight):** client display layer (2A) and 7 body-plan prototypes (2B) built from Studio parts, Experimental, awaiting the owner's look review → [[Creature Prototypes]]. The other 29 species still show the simple proxy.

## Phase 2 design pass (2026-10-16)
> [!success] Direction approved 2026-10-16 (not implemented): parts-based models for all 36 species first; silhouette-first visual language; client display models; procedural animation. See [[Phase 2 Spec]] → [[Creature Visual Language Spec]] · [[Creature Animation Spec]] · [[Hatch Presentation Spec]] · [[Mutation Reveal Spec]]. Implementation: [[PHASE2_IMPLEMENTATION_PLAN]].

## What exists today
- 36 [[Species]], each defined by a colour + material + descriptors in `SpeciesConfig` (no custom meshes recorded).
- [[Traits and Variants]] (Luminous, Chromatic, Prismatic) change appearance and sample value.
- Mutation-only species come from [[Mutation Recipes]].

## Open questions
- [ ] Art direction and model pipeline (see [[Asset Pipeline (Blender to Roblox)]])
- [ ] How variants should look per species
- [ ] Keep species ids stable — they are saved in player data ([[Persistence]])
