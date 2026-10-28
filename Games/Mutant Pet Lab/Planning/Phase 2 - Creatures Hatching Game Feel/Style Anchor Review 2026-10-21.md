---
type: review
game: "[[Mutant Pet Lab]]"
status: awaiting-owner-review
tags:
  - mutant-pet-lab
  - creatures
  - style-anchor
date: 2026-10-21
snapshot: 2026-10-21_style_anchors
---
# Style Anchor Review 2026-10-21: Frostpup + Mossbit

**Question:** does the Blender faceted low-poly style ([[Design Decisions#Creature style: every pet follows the blueprint Frostpup (R16)]]) generalize beyond an ice animal?

- **Frostpup** tests animal + fur + ice anatomy.
- **Mossbit** tests plant + organism anatomy.

Both are live templates in Studio. The old part-built models are archived in `ServerStorage.MPL_DesignReview.Archive` (`Frostpup_PartBuilt_C3`, `Mossbit_PartBuilt_C3`), marked *ARCHIVED / EXPERIMENTAL*.

## Side by side
Stage order, left to right in the front shot: Mossbit Luminous · Frostpup Luminous · Mossbit Standard · Frostpup Standard.

| View | Capture |
|---|---|
| Close front (after the Luminous fix) | ![[sbs-front.jpg]] |
| Side | ![[sbs-side.jpg]] |
| Back three-quarter | ![[sbs-back34.jpg]] |
| ~30 studs | ![[sbs-30studs.jpg]] |
| Real pens (Standard pair left, Luminous pair right) | ![[sbs-pens.jpg]] |
| Index grid (both next to the older part-built species) | ![[sbs-index.jpg]] |
| Creatures Viewer | ![[frostpup-viewer.jpg|420]] ![[mossbit-viewer.jpg|420]] |
| Specimen Showcase | ![[frostpup-showcase.jpg|420]] ![[mossbit-showcase.jpg|420]] |
| Luminous close-up (after the fix) | ![[sbs-luminous-close.jpg]] |
| Luminous before the fix (both glows went white) | ![[sbs-front-before-luminous-fix.jpg]] |

## Verdict: the style generalizes
- **Same game.** Both share the same chibi proportions, big glossy Roblox-part eyes with glints, flat-shaded low-poly facets, chunky limbs, one bold mutant feature and a restrained glow.
- **Not the same pet.**
  - Frostpup is a white crisp-faceted canid with an ice collar, tall ears and a bushy tail.
  - Mossbit is a round green sprout with soft facets, a drooping leaf hood, a tulip bud and root feet.
  - Silhouettes, palettes, materials and anatomy are all different.
- **Material adapts as decided:** crisp large facets for ice, softer smaller facets and matte for the plant.
- **Weakest points:**
  - Mossbit's leaf hood reads as a "cabbage" from directly behind.
  - At 30 studs Mossbit is small: the Common scale is smaller than Frostpup's Rare scale, by design.
  - The face is a flat-part overlay, so at extreme side angles the eyes can sit a hair proud of the mesh.

## Numbers
| | Frostpup | Mossbit |
|---|---|---|
| Meshes + face parts | 15 MeshParts + 11 face parts | 11 MeshParts + 10 face parts |
| Triangles | 712 | 594 |
| Close / medium / far | all / no mouth + blush / silhouette only (paws, crest, tail tip, eyes, nose hidden) | all / no mouth + blush / silhouette only (moss, pollen core, eyes hidden) |
| Animation cost per creature per frame (best of 5) | ~26–35 µs close · 18.6 medium · 12.5 far | 25.5 close · 23.3 medium · 13.7 far |
| Old part-built cost (C3) | 31.4 µs | — |
| Floor contact | resting height on the floor; the shared walk hop moves feet ±0.2 | same |

## Luminous refinement
Neon blooms pale colours to white, so the old "lerp 30% toward warm white" turned Frostpup's ice white and Mossbit's bud white. `CreatureKit` now reads three optional template settings (generic, reusable for every species):
- `LuminousTint` (Color3)
- `LuminousMix` (0–1)
- per-part `LuminousGlow = false` to opt out

| Species | Setting | Result |
|---|---|---|
| Frostpup | tint (30,165,255), mix 0.85 · crest / inner ears opt out | **Vivid glowing cyan ice collar**, white body and pale paws stay matte; still reads as ice |
| Mossbit | tint (255,80,175), mix 0.75 · leaf arms opt out | **Glowing hot-pink tulip bud** + pollen core; the leaf body stays matte |

The pulse and the close-range sparkle are unchanged (12 Hz, close range only).

## Expressions
- Blink works for both, and the Curious head-tilt works.
- **Happy / sleepy / low-wellbeing faces are not implemented in game code for any species yet** (design spec only: [[Creature Face Language]]).
- Both models keep the separate Roblox-part face, so those expressions can be added later without touching the meshes.

## New owner references (2026-10-21)
[[Owner Reference Library#R17 · MPL "Creature Blueprints: Core Roster" board (added 2026-10-21)|R17]] (roster board, plush style) and [[Owner Reference Library#R18 · "Pov: you started to make models with Claude design" video (added 2026-10-21)|R18]] (voxel pets in a model viewer) were reviewed and logged.

> [!question] Owner decision needed
> R17's creatures are **soft, plush and detailed**, not faceted low-poly. Is R17 a **UI/layout** reference (Index detail and specimen-sheet layout: hero render + callouts + Front/Side/Back + Variants row + Mutation-paths row), or should the creature finish move toward that softer look? Nothing was changed. The approved direction is still the R16 faceted style.

## Recommendation
1. **Owner style review of these two anchors** (this note).
2. If approved: lock the style. Convert the remaining **5 baseline species** (Sparkbug, Slimelet, Pebbletoad, Magmawisp, Rockling) next, one Blender model each, in the same pipeline. They are the body-family references the other 29 inherit from.
3. Then the [[Roster Conversion Plan]] batches, starting with Gel + Sprout as planned.
4. Separately (UI): adopt R17's specimen layout for the Index detail panel and the Creatures viewer.
