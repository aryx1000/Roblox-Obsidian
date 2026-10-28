---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: creatures
status: experimental
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - phase-2
  - creature-prototype
---
# Creature Prototypes

> [!note] SUPERSEDED (2026-10-16) by CREATURE-C1: [[C1 Review Stage 2026-10-16]]. These overnight prototypes are archived in `ServerStorage.MPL_DesignReview.Archive`.


> [!danger] OWNER FEEDBACK 2026-10-16 (real-device review) — visual direction correction
> **CURRENT 7 CREATURE PROTOTYPES ARE EXPERIMENTAL AND NOT APPROVED AS THE FINAL CREATURE STYLE.**
> **CURRENT BOTTOM NAVIGATION LAYOUT IS NOT APPROVED.**
> Observed problems: creatures still look like primitive Roblox parts assembled together and not like polished collectible pets; the UI is colourful but bland and developer-like; the large bottom nav takes too much of the phone screen; the HUD is too large; panels read as admin/card lists; the saved references must be used much more strongly.
> The owner wants: stronger simulator-style presentation, better use of the saved references, navigation moved to the sides (no large bottom bar), and creatures that look like actual pets/organisms.
> **Do not build the remaining 29 species. Do not migrate every panel again. Do not publish.** Next step: 3 UI directions + 3 directions each for Frostpup, Mossbit, Sparkbug, then wait for the owner's choice.
>
> **Review ready (2026-10-16):** [[Visual Direction Review 2026-10-16]]: 3 side-rail UI directions (recommended C) + 3 directions each for Frostpup / Mossbit / Sparkbug (recommended C) + [[Creature Face Language]]. Waiting for the owner's selection.


> [!warning] EXPERIMENTAL / CANDIDATE — awaiting the owner's look review (checkpoint 2B gate)
> Built 2026-10-16 from Studio parts (no meshes, no Blender), one per approved body plan. Editable templates in `ReplicatedStorage.MutantPetLab.Creatures.Species`. Rendered by the client display layer (2A); every other species still shows the simple proxy.

![[phase2-prototypes-lineup.jpg]]
*Edit-mode lineup. Right to left: Slimelet, Mossbit, Rockling, Pebbletoad, Sparkbug, Frostpup, Magmawisp (flyer and wisp shown at hover height).*

| Prototype | Plan | Rarity | Parts | Signature | Mutant accent |
|---|---|---|---|---|---|
| [[Slimelet Prototype]] | Gel | Common | 15 | eye stalks | neon nucleus |
| [[Frostpup Prototype]] | Critter | Rare | 21 | ice-spike ridge | glowing nose |
| [[Pebbletoad Prototype]] | Hopper | Uncommon | 19 | hind legs + bulging eyes | glowing moss spots |
| [[Sparkbug Prototype]] | Flyer | Uncommon | 18 | glass wings, antennae | neon tips + stinger |
| [[Mossbit Prototype]] | Sprout | Common | 19 | five-leaf crown | glowing tuft |
| [[Magmawisp Prototype]] | Wisp | Epic | 13 | orbiting shards | neon core |
| [[Rockling Prototype]] | Shellback | Common | 18 | dome shell | glowing cracks |

## Close-ups
![[phase2-prototypes-close-a.jpg]]
![[phase2-prototypes-close-b.jpg]]
![[phase2-prototypes-close-c.jpg]]
![[phase2-prototype-magmawisp.jpg]]

*close-a was captured before the Magmawisp eye fix (eyes moved onto the shell) and close-c before the Rockling crack / Slimelet mouth fixes; the lineup and close-b show the final state except Magmawisp, shown fixed in its own capture.*

## Shared rules used
- Front = −Z; `Root` at ground level; every part has a `Role` the animator understands.
- Eyes: white ball + dark pupil + small Neon shine (Wisp: dark eyes on the flame).
- One mutant accent (Role Glow), one signature feature, readable at 30 studs.
- Rarity is NOT in the template: the runtime adds scale (Rare ×1.1, Epic ×1.2) and a ring (Uncommon+).

## Candidates to confirm
- Part budget ≤ 22 instead of ≤ 8/10/12 (measured 13–21 + ring).
- Each look, colour and signature above.
- Wisp without the shadow disc.
- Shrink-blink (Ball eyes can't squash).

## Related
[[Creature Visual Language Spec]] · [[Creature Animation Spec]] · [[PHASE2_IMPLEMENTATION_PLAN]] · [[Creature Overhaul]]
