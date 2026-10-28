---
type: review
game: "[[Mutant Pet Lab]]"
status: awaiting-owner-review
tags:
  - mutant-pet-lab
  - ui
  - art-pass
date: 2026-10-21
snapshot: 2026-10-21_ui_art_pass
---
# UI Art Pass 2026-10-21

Reference-driven final UI art pass, done after [[C3 Review 2026-10-21]]. Direction C (side rails, compact HUD) stays the identity. Nothing was published. The backend, odds, economy, schema, recipes and ranch authority are unchanged.

> [!quote] Owner feedback this pass answers (recorded 2026-10-21)
> - The reveal is a generic dark rectangle.
> - The creature preview is too small.
> - The hierarchy is weak.
> - The buttons are generic.
> - The panels look system-built.
> - "colorful is not polished"

## What changed

| Checkpoint | Change | Status |
|---|---|---|
| A. Kit art | `C.Polish` on all 9 panels: a dark depth lip under the frame; title plates with a bottom lip, two diagonal sheen stripes, a top light line, a hard text shadow and a vector icon (leading emoji removed); a vector close X with a lip; a soft top highlight on mint pages | Done, seen in Play (Egg Lab, Index, Goals, Ranch) |
| B. Icon system | New `ReplicatedStorage.MutantPetLab.UI.Icons`: original vector primitives (shadow and face layers, ink outlines) for Build, My Lab, Home, Creatures, Index, Goals, Ranch, Egg, Mutation, Research, Upgrades and Close. Used on the rails and title plates. No icon packs used. | Done, seen in Play |
| C. Hatch/discovery reveal | No box. The world dims; a rarity-coloured burst (12 rotating rays, glow, ring, pedestal) sits behind a much larger 3D creature that pops in. Tilted stamp header (NEW DISCOVERY! / LEGENDARY! / RARE HATCH! / HATCHED!), tilted NEW! stamp, name, rarity and % chance pills, trait and source line, "ADDED TO YOUR INDEX" note, one CONTINUE button. Common repeats get a lighter dim, no rays and a 4 s hold. The reveal now counts as modal (HUD, rails and tracker step aside) without closing the screen behind it. | Done, seen in Play at the phone viewport |
| D. Goals | Shared polish; card titles wrap and scale instead of clipping ("Discovery Breakthrough") | Done |
| E. Index | Shared polish; card footers show % chance instead of "1 in N" (display only; matches the Egg Lab odds) | Done. The large-art/rarity-frame rework is **not done** |
| F. Egg Lab | Shared polish | Done |
| G. Mutation Lab | Shared polish only | Partial |
| H. Creatures viewer | Shared polish only; chips instead of text rows **not done** | Partial |
| I. Ranch | Shared polish; slot previews grounded on their shadows and narrowed (no overlap); a large Ranch icon in the empty state | Preview grounding is structural only: the test profile has no pens, so it wasn't seen in Play |
| J. Research | Shared polish only; hex hierarchy rework **not done** | Partial |
| K. My Lab / Upgrades | MOVE button is white on slate blue (was dark text on light grey). **Content bug, reported, not changed:** Upgrades "Extra Incubator Slot" says "Expands creature storage". | Done; bug open |
| L. Rails/HUD | Vector rail icons with a lip | Partial (no further HUD polish) |

## References used per screen (principle adapted / NOT copied)

| Screen | Owner references | Principle adapted | Not copied |
|---|---|---|---|
| Panels (all) | R1, R2, R14 shop/index screens | Full-width coloured header with diagonal sheen; thick outlined white title; square red close; dark body; hard shadows and a thick bottom edge | Their layouts, header shapes, textures, colours and fonts. Direction C palette and corner radii kept |
| Rail icons | R7 (big readable icons), ui-figma-roblox technique notes | Chunky ink-outlined glyphs with a darker offset layer | No icon art from any pack or reference; every icon is an original Frame primitive |
| Hatch reveal | R9 legendary reveal, R4 "New!" reveal | No box, full dim, huge creature over a glowing ring and pedestal, rarity title, "% chance" line, a single continue button; a tilted NEW stamp | R9's gold ring art, fonts, wording ("Awesome!"), layout proportions and R4's stamp art. The title stamp is Direction C's plate with sheen; burst is generic rays |
| Index | R5 egg odds, R14 index | Percent odds on cards; silhouettes for unknown species (already present) | Grid styling and card art |
| Egg Lab | R1/R2 shops | Chunky price button, header sheen | Shop layout and currency art |
| Goals | (no direct reference) | Shared polish and text fitting | — |
| Ranch | R7 | One big readable icon for the empty state | — |

The new downloaded pack (ui-figma-roblox skill assets: Kek UI Essentials, UI Resources) was checked. It's **not used** for art because it has no licence for commercial use. Only techniques were applied: depth copy, outside outline, rim/lip/sheen and hard text shadow.

## Validation

- Fresh Play server: **185/185** unit tests; no game errors (only Roblox CorePackages UIBlox warnings).
- Viewports (the reveal uses the new `FitUniform` uniform fit). Phone (Studio viewport 749×381) was seen visually. All four were computed with the real Theme scale:

| Viewport | Reveal scale | Box (px) | Fits | Creature height |
|---|---|---|---|---|
| 667×375 | 0.684 | 356×312 | yes (top 14, bottom 325 of 339) | ~159 px |
| ~874×402 | 0.738 | 384×337 | yes | ~171 px |
| tablet 1180×820 | 1.25 | 650×570 | yes | ~290 px |
| 1366×768 | 1.25 | 650×570 | yes | ~290 px |

- Not seen visually this pass: the tablet and 1366 reveal (the emulator can't be switched by API), and Ranch slots with creatures.
- Saved to Roblox 2026-10-21 13:32 (not published). Snapshot `2026-10-21_ui_art_pass` (201 scripts, checksum 1944016977, 11,216 instances), commit 87d2af1.
- Backups of everything changed: `ServerStorage.MPL_DesignReview.PreArtPass`.

## Captures

![[reveal-discovery-final.jpg]]
![[reveal-common-repeat.jpg]]
![[reveal-discovery-v1-overflow.jpg]]
*First version overflowed at phone height. Fixed with the Kit `FitUniform` uniform scale and a compact layout.*
![[egg-lab-polish.jpg]]
![[goals-polish.jpg]]
![[index-polish-before-pct.jpg]]
![[rails-icons-phone.jpg]]
![[ranch-empty-before-icon.jpg]]

## Open (next art-pass round, after owner review)
- H: Creatures viewer chips instead of text rows.
- J: Research hex hierarchy.
- E: Index large art and rarity frames.
- G: Mutation Lab beyond shared polish.
- L: HUD polish.
- Visual check of Ranch slots with creatures.
- Upgrades content bug (needs an owner decision on the wording).
