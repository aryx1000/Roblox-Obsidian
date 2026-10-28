---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: creatures
status: approved
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - phase-2
  - creature-face
---
# Creature Face Language

> [!success] APPROVED (owner 2026-10-16) with refinements: low wellbeing = sad/tired (not angry); curious adds a head tilt; eye shapes vary by species (round / oval / narrower / iris proportions). Built in `ServerStorage.MPL_DesignReview.Tools.CreatureMockBuilder` (`face()` / `eye()`). Production use: CREATURE-C1 templates. Review: [[Visual Direction Review 2026-10-16]].

![[creature-face-expressions-frostpup-C.jpg]]

## Eyes (the identity of a pet)
| Rule | Value |
|---|---|
| Eye height | 28–36% of head height (A/C). B (biological) uses 18–24%, which is too small at 30 studs |
| Eye width | about 80% of eye height (slightly tall ovals) |
| Spacing | centres at ±0.36 of the head half-width; never touching; gap ≈ 1 eye width |
| Height on head | at or just above the head's equator (lift 0–0.1); low eyes = younger, cuter |
| Layers | iris ellipsoid (species colour) → black pupil (62% of iris, slightly low) → **large glint** upper-outer (36% of eye width, white) → **small glint** lower-inner (16%) |
| Solid style (A) | one glossy black ellipsoid + a coloured sheen at the bottom instead of an iris |
| Material | SmoothPlastic with a little Reflectance; glints are the only Neon on a common creature |
| Placement | exactly on the head surface along its normal (no floating stickers) |

## Mouth
- **w-mouth** (two small tilted dark ellipsoids): default resting/content.
- **Open** (dark ellipsoid + pink tongue): happy, excited, eating.
- **o**: curious, sleepy (yawn).
- **Frown** (a flat line + down-turned corners): upset / low wellbeing.
- **Pups:** the mouth sits on the **muzzle**, not on the head (the muzzle hides it otherwise).
- **Plants:** the mouth sits low on the body; no tongue on B-style pods.

## Blush
Pink transparent ellipsoids under the outer eye corners on cute directions (A/C). It is the cheapest way to add warmth.

## Expressions (all built from the same parts)
| Expression | Eyes | Mouth | Gameplay hook |
|---|---|---|---|
| Neutral | open | w | default |
| Happy | closed **∩ arcs** (dark crescent + skin cover) | open + tongue | favourite food, being petted, level-up |
| Curious | open, one eye slightly larger + **head tilt ~12°** | o | player within look range, new object nearby |
| Sleepy | upper lid 78% down, flat | o | idle at night / rest window |
| Sad / tired (low wellbeing) | lid ~50% down, **tilted outward-down** (droopy, not angry), small tear-free | small frown / wobbly line | low wellbeing ("Stable" with unmet needs) |

## Blink
- Lids or eye parts scale Y to about 15% for 0.12 s every 3–6 s (Calm trait: 6–9 s).
- Ellipsoid eyes now squash correctly (the overnight Ball eyes could only shrink).

## Rules
- Never tiny dot eyes.
- Faces must stay readable at 30 studs. If a direction loses its eyes at that distance, enlarge the eyes or add contrast (dark heads use bright irises).
- Face parts are the first LOD casualties beyond 40 studs, except the two eye bases.

## Per-family eye shapes (approved: shared language, varied shapes)
| Family | Eye shape | Iris |
|---|---|---|
| Critter (Frostpup) | large round | coloured iris, big glints |
| Sprout (Mossbit) | soft oval, slightly low | warm brown/amber |
| Flyer (Sparkbug) | very large round (bug-cute) | bright teal ring |
| Gel (Slimelet) | tall oval, set wide | solid glossy + sheen |
| Hopper (Pebbletoad) | big bulging round on top bumps | gold iris, horizontal pupil |
| Wisp (Magmawisp) | narrower almond, glowing-ember iris | dark pupil |
| Shellback (Rockling) | small-ish round, peeking | soft brown |
