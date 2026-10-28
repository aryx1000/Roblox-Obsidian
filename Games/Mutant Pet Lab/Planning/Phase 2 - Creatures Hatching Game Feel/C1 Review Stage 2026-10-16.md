---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: visual-production
status: awaiting-owner-review
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - phase-2
  - ui-c1
  - creature-c1
---
# C1 Review Stage (UI-C1 + CREATURE-C1), 2026-10-16

> [!warning] REVIEW STAGE: STOP HERE
> Both checkpoints implement the approved direction ([[Design Decisions#Visual direction APPROVED: UI Direction C, side rails, status-pod HUD, C creature language (owner, 2026-10-16)]]).
> - **The other 29 species are NOT built.** The remaining screens are NOT migrated yet.
> - Not published.
> - **Not saved to Roblox:** the Mac was locked at both checkpoints. Local snapshots `2026-10-16_ui_c1` and `2026-10-16_creature_c1` are verified.

## UI-C1: production side rails, HUD, Goals, Index
**Side rails** replace the bottom nav:
- Left rail: Build / My Lab / Creatures / Index. Right rail: Goals / Ranch / Home.
- Dark lab docks; C-style gradient tiles with ink outlines; badges (NEW, goal count).
- Selected screen: gold ring plus gold pip.
- **Phones:** icon only. Rails collapse while a panel is open.
- **Tablet/desktop (≥1100 px):** icon + label. With a panel open, the rails stay compact beside it, and step aside if they would cover the panel or its X.
- Build Mode hides everything, as before.

**HUD:** one status pod, 222×46 design px (was 340×96, **−69% area**): level badge, XP bar, Cash/Research chips. Values count up as before.

**Goals → Lab Task Board:**
- A "Current Task" hero (the next unfinished task: icon, description, progress, reward).
- Pinned task cards in a 2-column grid (icon tile, progress, reward chip, DONE stamp, green when complete).
- A Lab Tasks progress strip with a gift.
- Gold title plate overlapping the frame; red X.

**Index:**
- Dark lab frame, purple title plate, red X.
- Icon tabs (Species / Eggs / Mutations) with gold selection.
- Mint page and rarity-framed cards.
- **Live 3D previews of the real creature templates** in the cards and the detail card. Undiscovered species show as **dark 3D silhouettes**; species without a template keep the letter glyph.

**Unchanged:** every server call, button routing, persistence, economy, Build Mode.

![[ui-c1-phone667-world.jpg]]
![[ui-c1-phone667-goals.jpg]]
![[ui-c1-phone667-index.jpg]]
![[ui-c1-phone874-world.jpg]]
![[ui-c1-tablet-goals.jpg]]
![[ui-c1-desktop1366-world.jpg]]

**Viewport results** (production elements in true-size device frames + computed audit):

| Viewport | Result |
|---|---|
| 667×375 | Fits; bottom ~35% clear; rails clear the thumbstick/jump zones; text ≥ 12 px and tap targets ≥ 44 px after fixes |
| 874×402 | Fits; left rail sits close to the thumbstick guide but does not overlap it |
| 1180×820 tablet | Labels on rails; compact rails beside panels; close button clear (fix applied) |
| 1366×768 | Labels on rails; layout clean |

## CREATURE-C1: the 7 representatives rebuilt
Style rule: **"Cute collectible organism first, mutant biology second."**

| Species | Plan | Base | Parts (close / medium / far) | Mutant feature | Display scale |
|---|---|---|---|---|---|
| Frostpup | Critter | **LEFT** chunky quadruped + C face | 30 / 22 / 21 | icy fur tufts + one small frost crystal | ×1.05 |
| Mossbit | Sprout | **RIGHT** (C) | 25 / 21 / 19 | glass flower bud with a small glowing core, moss patch | ×1.15 |
| Sparkbug | Flyer | **RIGHT** (C) | 30 / 24 / 21 | lightning-bolt antennae, glass charge cell | ×1.18 |
| Slimelet | Gel | C language | 18 / 11 / 8 | inner glowing nucleus, drip feelers | ×1.10 |
| Pebbletoad | Hopper | C language | 21 / 18 / 15 | pebble growths + moss on the back | ×1.10 |
| Magmawisp | Wisp | C language | 23 / 19 / 17 | flame tuft (one small glowing lobe), basalt chest crack, orbiting stones | ×1.0 (Epic ×1.2 rarity) |
| Rockling | Shellback | C language | 22 / 18 / 14 | shell crystals with a faint core, moss | ×1.12 |

(+1 subtle rarity ring for Uncommon and up, added at runtime.)

![[creatures-c1-front.jpg]]
![[creatures-c1-side.jpg]]
![[creatures-c1-close-heroes.jpg]]
![[creatures-c1-close-others.jpg]]
![[creatures-c1-30studs.jpg]]
![[creatures-c1-gameplay-context.jpg]]
*The close-heroes capture predates moving Magmawisp's chest crack off its eye; the front lineup shows the final version.*

**What changed from the overnight prototypes:**
- Real anatomy: muzzles, paws, toe beans, canine ears, eye bumps.
- Layered iris eyes with per-family shapes (round / oval / tall / wide pupil).
- Matte bodies; Neon only on small organs.
- Rarity scale plus a ring that is smaller, fainter and stays on the ground under flyers.

**Validation (Play, live renderer):**
- All 7 attach. Embercub falls back to the server proxy.
- Ground offset ≤ 0.08 studs; flyers and the wisp hover.
- **LOD:** 0 parts hidden near, 36 at medium (> 40 studs), 54 at far (> 90), restored on return.
- Trait: Curious head tilt added to the animator. Variants (Luminous/Chromatic/Prismatic) use the existing rules.
- Animator cost: Frostpup ~11 µs/step, Sparkbug ~35 µs/step. Worst case 24 animated ≈ 0.6–0.8 ms/frame (budget was 0.5 ms). A device check is still needed.
- 185/185 tests; no client errors.

**Blender/MeshPart candidates:** Frostpup's fur contour still reads slightly "balloon" at close range. Sparkbug's wings could gain from real wing meshes. Neither blocks C1.

## Remaining review items (owner)
1. The 7 creature looks (especially Magmawisp's face and Pebbletoad's eyes) and the display-scale values.
2. The rarity ring at its new subtlety: keep, reduce further, or replace with an anatomy-only read.
3. UI-C1 on a real phone: rail thumb reach, HUD size, the Goals and Index composition.
4. Then: migrate the remaining screens (Egg Shop, Mutation Lab, Creatures, Ranch, Research, My Lab) to the C language; **only after another review**, the other 29 species.
5. Animator cost if all 24 animated creatures are Sparkbug-class: consider a lower wing-flap rate at mid distance.
