---
type: planning
game: "[[Mutant Pet Lab]]"
area: ui
status: candidate
updated: 2026-10-20
tags:
  - mutant-pet-lab
  - planning
  - ui
  - creatures
---
# Creature Viewer

> [!success] Built 2026-10-20 (C2)
> The Creatures screen is now viewer-first: real rig (rarity + variant), drag to rotate, front/side/back, zoom, Idle/Move/Still, fact rows (trait, wellbeing meter, favourite, habitat ✓, location, samples). Lineage: later. [[C2 Review 2026-10-20]]


> [!info] CANDIDATE (C-R9, 2026-10-20)
> Based on owner R11 (Idle / Move / Ability tabs) and R13 ("display pet animations so I can look at them properly"), and the **Pokédex 3D** pattern (official: full 360° rotation + zoom). Direction-C styling. Client-only; no server changes.

## Where it opens
- Creatures panel → tap a creature card.
- Index → tap a discovered species (undiscovered: the silhouette only, no rotation of the coloured model).
- Hatch card → VIEW.
- Visiting another lab → tap their creature (**read-only**, no care facts beyond public ones).

## Layout (phone first, 667×375 at scale 0.8)
```
┌ [Species title plate]                          [X] ┐
│ ┌──────────────── viewport ───────────┐ ┌ facts ─┐ │
│ │      creature on its habitat disc   │ │ rarity │ │
│ │  ⟲ drag to rotate · pinch to zoom   │ │ trait  │ │
│ │ [Front][Side][Back][Top]  [⛶ full]  │ │ variant│ │
│ └─────────────────────────────────────┘ │ wellb. │ │
│ [Idle][Walk][Happy][Sleep][Special]      │ food   │ │
│                                          │ habitat│ │
│                                          └────────┘ │
└─────────────────────────────────────────────────────┘
```
- **Viewport:** ~58% of the width. The creature stands on a **habitat-themed disc** (R11's element platform idea: puddle for Gel, snow for Frostpup), with soft rim lighting.
- **Rotate:** one-finger drag / mouse drag. **Zoom:** pinch / wheel (limited 0.7×–1.6×). Idle auto-rotate after 4 s without input.
- **Angle buttons:** Front · Side · Back · Top (snap with a 0.3 s ease). They mirror the [[Creature Template Sheets]] views.
- **Motion tabs:** Idle · Walk · Happy · Sleep · **Special** (the body plan's rare idle from [[Creature World Interaction]]). Played by `CreatureAnimator` inside a `WorldModel` in the ViewportFrame.
- **Full-screen toggle:** hides the facts column; the rails are already hidden while a panel is open.

## Facts column (icons first, short words)
| Fact | Display |
|---|---|
| Species | Title plate + the body-plan descriptor (e.g. "Arctic Canid", from the template sheet) |
| Rarity | Rarity chip (rarity colour) |
| Trait | Icon + word (🌙 Calm …) + a one-line effect on tap |
| Variant | Chip (Luminous / Chromatic / Prismatic) + a **variant toggle** in the Index view to preview looks |
| Wellbeing | 💚 Thriving / 💛 Content / 🤍 Stable (own creatures only) |
| Favourite food | Crop icon |
| Habitat preference | Habitat chip; ✓ if it's in a matching pen |
| Lineage | **Later, if approved:** "from A + B" for mutation species, egg families for egg species |

## Performance
- **One viewer at a time.**
- The viewport model is built from the display template (same part counts) and animated only while the viewer is visible.
- A static frame is used when the app is backgrounded.
- No particles inside the viewport except the Prismatic sparkle (≤ 6/s).

## Tests (when built)
Opens from all 4 entry points · rotation/zoom/angles work with touch and mouse · tabs play the correct motion · read-only when visiting · fits the 4 viewports · ≤ 0.5 ms / frame while open.
