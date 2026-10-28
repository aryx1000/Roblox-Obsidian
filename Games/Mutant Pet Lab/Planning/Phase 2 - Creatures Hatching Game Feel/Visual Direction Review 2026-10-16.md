---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: visual-direction
status: awaiting-owner-selection
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - phase-2
  - visual-direction
  - design-review
---
# Visual Direction Review (2026-10-16)

> [!warning] AWAITING OWNER SELECTION — nothing here is approved
> Response to the owner's real-device review ([[Design Decisions#Phase 2 correction: visual direction reset (owner, real-device review)]]). Three UI directions and three creature directions per hero species were built as **editable Studio mockups** in `ServerStorage.MPL_DesignReview` (never shipped to players). The live game is unchanged: same HUD, same screens, same 7 overnight prototypes. **No species converted, no panels migrated, nothing published.**

## Where to review
- **Images:** `Planning/Assets/visual-review-2026-10-16/` (15 captures, embedded below).
- **Studio (editable):**
  - `ServerStorage.MPL_DesignReview.UIMocks`: 12 ScreenGuis. They are `Mock_<A|B|C>_Phone667_<World|Goals>` plus `Mock_C_<Phone874|TabletAir|Desktop1366>_<World|Goals>`. To view one, copy it into StarterGui and enable it. Each mock draws a true-size device frame showing the Roblox top bar, thumbstick and jump zones.
  - `ServerStorage.MPL_DesignReview.Creatures`: 13 models, the 9 prototypes plus 4 expression variants. Drag one into Workspace to look at it.
  - `ServerStorage.MPL_DesignReview.Tools`: `UIMockBuilder`, `CreatureMockBuilder`, the generators. Local copies are in `MutantPetLab/design_review/`.

---

## 1. References used (actual images inspected)

| Reference | Proportions / shape language | Panel hierarchy & navigation | Icons, cards, text | Colour, depth, hierarchy |
|---|---|---|---|---|
| [[Index Collection Screen]] | Chunky, rounded, slightly irregular frame; a fat title tab overlapping the frame edge | One framed modal; **category tabs live OUTSIDE the frame on the left**, as floating icons with outlined labels; big red X top-right; detail card pops out beside the grid | Illustrated icons with no box; cards = creature render on a saturated rarity tile, name above, odds in outlined text below; "???" silhouettes | Warm cream page inside a dark wooden border = strong depth; heavy dark text strokes; one focal progress bar with reward icon |
| [[Shop Storefront Layout]] | Same frame family; hero banner fills the top half | **Right-side shortcuts outside the frame** (floating icons + labels); section dividers ("-- PASSES --"); left-side Gift icon floating on screen | Big pill buttons in escalating colours; tiny badges ("POPULAR") on card corners; one line of copy | Dramatic hero art with dark vignette; gradient buttons (green→gold→rainbow); depth from layering, not shadows |
| [[Creature Silhouette and Personality]] (Adopt Me) | Head ≈ body or bigger; stubby limbs; distinct ears/tails/wings per species; soft round forms | — | **Eyes are the identity:** huge glossy dark eyes, 1–2 big white highlights, tiny nose/mouth | Matte soft materials; glow only on the special (neon) creature |
| Pet Simulator 99 (shared body plan) | Cube body + huge eyes + paw pads in accent colour | — | Eye whites + vertical pupils; pink paw pads | Bright flat colours; outlined illustration style |
| [[Reward Burst and Wild Encounters]] (BGSI) | **Blocky cube dog that still looks polished:** sparkle eyes, blush, floppy ears | — | Glossy reward bubble, one short number | Proves part-based/blocky can work if the face and proportions are right |
| [[Rarity Reveal Escalation]] (Ride A Pet card) | Rare = more anatomy + VFX (flames, cracks), not just brighter | — | Name / odds / value as three short outlined lines | Dark scene, the creature carries the light |
| Sonaria customisation UI | Realistic anatomy | Panels docked to the screen edges, world visible in the centre | Small text lists (the thing to avoid) | — |

**What was NOT copied:** wood/parchment art, any creature, names, numbers, fonts, branding, Robux/pass/discount content, the exact layouts.

---

## 2. UI problems identified (current build)
1. **Bottom nav bar** 620×82 design px (about 496×66 real px on a 667×375 phone) sits right in the thumbstick/jump band and hides the ground the player walks on.
2. **HUD** 340×96 design px: about 3× the area needed for 4 numbers (DevForum "a third of the screen spent on three numbers" warning, [[Simulator UI Research]]).
3. **Panels** = light rectangle + stacked light cards: no frame depth, no title plate, no focal object, too much explanatory text.
4. Icons sit inside flat tiles with labels inside: icon *and* label both small.
5. Goals = a plain list; no sense of a mission or reward.

## 3. Three UI directions (all side-rail, same layout system)
All three share: compact HUD top-left (under the Roblox top bar), **left rail** Build / My Lab / Creatures / Index, **right rail** Goals / Ranch / Home + a contextual action slot (e.g. samples ready ×3), a top-centre notification toast, and badge support. When a panel opens, the HUD and left rail collapse; the right rail stays slim with the active screen highlighted (gold ring + 1.12 scale). On ≥1100 px (tablet/desktop) the rails expand to icon + label. **The bottom ~35% of the phone screen is now clear.**

### A — Clean Lab Simulator
![[ui-A-clean-lab-phone-world.jpg]]
![[ui-A-clean-lab-phone-goals.jpg]]
- **Look:** dark translucent glass instruments, thin mint/violet accent lines, Gotham type, no outlines.
- **Pros:** calm; the most readable over busy scenes; the most "lab"; little visual noise.
- **Cons:** reads more "app" than "Roblox simulator"; emoji icons look weak on dark tiles; Goals is still a list (cleaner, but still the admin feel the owner rejected). Least like the references.

### B — Playful Cartoon Lab
![[ui-B-playful-phone-world.jpg]]
![[ui-B-playful-phone-goals.jpg]]
- **Look:** thick dark outlines, saturated gradient tiles, Fredoka One, cream paper, sticker cards, a notebook spine, a tilted title tab overlapping the frame, a "DONE!" stamp.
- **Pros:** closest to the saved references (frame + title tab + big red X + chunky outlined type); the Goals "Mission Journal" is the most game-like; the most fun.
- **Cons:** loud; cream paper clashes with the lab world colours; risk of looking generic simulator rather than MPL's identity; heaviest to restyle 8 screens. (Tilted rail tiles were planned but Roblox doesn't render rotation inside the list layout; dropped.)

### C — Balanced (recommended)
![[ui-C-balanced-phone-world.jpg]]
![[ui-C-balanced-phone-goals.jpg]]
- **Look:** B's chunky outlined tiles and Fredoka One, grouped on **dark-teal rail docks** (lab console look); HUD as **one status pod** (level badge + XP + currency chips); panels use a **dark lab frame + gold title plate overlapping the frame + mint glass page** inside (reference structure, lab skin).
- **Goals → "Lab Task Board":** one big **Current Task** hero (focal icon, progress, GO ▶) + 4 pinned task cards (pins, CLAIM in green) + a Lab Rank strip with a reward gift.
- **Pros:** keeps the references' depth and hierarchy without the wood/paper skin; matches the approved "friendly research device" lab skin ([[Design Decisions]]); a clear focal action; readable on phones.
- **Cons:** docks add a little visual weight at the screen edges; still emoji icons (all directions need real icon art eventually).

**C at the other viewports** (same code, scale `clamp(usableHeight/400, 0.8, 1.25)`):
![[ui-C-balanced-874x402.jpg]]
![[ui-C-balanced-tablet-1180x820.jpg]]
![[ui-C-balanced-desktop-1366x768.jpg]]
*Desktop capture predates a dock-width fix; the docks now widen with the expanded rails, as the tablet capture shows.*

### Measured
- **HUD area:** 340×96 → 222×46 design px (**−69%**).
- **Nav:** a 620×82 bottom bar → two 56-px rails on the screen edges. The bottom band is free on all 4 viewports.
- **Phone (667×375, scale 0.8):**
  - Rail tiles = 44.8 px real (≥ 44 target).
  - HUD text 15 → 12 px real.
  - Fails to fix during implementation: badge digits (13 → 10.4 px) and progress-bar labels (13 → 10.4 px). Raise both to 15.
- **Left rail vs thumbstick:** the last tile ends near the top of the thumbstick guide on 667×375. Mitigation if it collides on device: 3 left tiles + a "more" or collapse toggle, or a 52-px tile.

## 4. Recommendations
- **Side-nav:** direction **C** rails.
  - Left = Build, My Lab, Creatures, Index. Right = Goals, Ranch, Home + one contextual action slot.
  - Rails hide in Build Mode (as the bottom bar does today). On panel open: HUD + left rail collapse, the right rail stays slim.
  - Expanded labels only at ≥ 1100 px.
- **HUD:** one status pod, 222×46 design px. Level badge overlapping the left end; XP bar on top; Cash and Research chips below; no stats line; values count up (existing `Kit.CountUp`).
- **Panel style:** dark lab frame with a 4 px ink outline, a gold/accent **title plate overlapping the frame**, a big red X, a **mint glass inner page**, one **focal hero** per screen (Index: selected creature; Egg Shop: featured egg; Mutation: chamber; Goals: current task), cards with rarity frames, icon tabs outside or along the frame edge, max one line of copy per card.

---

## 5. Creature problems identified (overnight prototypes)
![[before-overnight-prototypes.jpg]]
- Bodies were single spheres with cylinders stuck on: the construction showed.
- Eyes were small white balls with a dot pupil: lifeless (the opposite of every reference).
- Glow was the identity (Magmawisp, nuclei, tufts).
- Heads not separated from bodies, no paws/feet/muzzles: animals didn't read as animals.
- Species differed mostly by colour.

## 6. Creature prototypes (3 directions × 3 species)
Construction rules used:
- Overlapping ellipsoids (SpecialMesh spheres on Blocks).
- Features placed exactly on curved surfaces (surface normal math).
- Layered eyes (iris, pupil, two highlights).
- Glass shells over small neon cores for mutant organs.
- Wedges for crystals/bolts; Fabric, Grass and Wood materials for texture.
- All parts anchored and non-colliding, with `Role` attributes kept for `CreatureAnimator`.

### Frostpup (animal pet)
![[creature-frostpup-A-B-C.jpg]]
*Left→right: A, B, C.*
| | A — very cute/chunky (41 parts) | B — biological/mutant (47) | C — balanced (44) |
|---|---|---|---|
| Silhouette | chibi: giant head, stubby legs, curl tail | lean wolf-fox, long snout, crystal spine | pup: head ≈ body, clear muzzle, short legs |
| Face | huge solid glossy eyes + blush (Adopt Me read) | small slit-pupil eyes with sclera | big eyes with blue iris + 2 highlights, w-mouth |
| Mutant identity | one small frost crystal | crystal growths through fur + faint chest core | 3 back crystals + one faint core |
| Cuteness / readability at 30 studs | highest / high | lowest / medium (eyes small) | high / high |
| Animation | easy (bob, waddle) | more limbs, needs leg cycles | easy |

### Mossbit (plant creature)
![[creature-mossbit-A-B-C.jpg]]
| | A (24) | B (38) | C (38) |
|---|---|---|---|
| Silhouette | round bud + two sprout leaves (propeller) | walking seed pod on four root legs, frond crown | bud under a 6-leaf hood + flower bud, leaf arms |
| Face | big solid eyes, open mouth, blush | small yellow eyes with sclera above split pod lips | brown-iris eyes, w-mouth, blush |
| Mutant identity | glass dew-bud | glowing seed inside the pod + floating spores | glass flower bud with a small glowing core + moss patch |
| Notes | cutest, simplest | the most "organism", least cute, root legs read well | best balance; hood reads as plant at a distance |

### Sparkbug (flying insect)
![[creature-sparkbug-A-B-C.jpg]]
| | A (26) | B (35) | C (35) |
|---|---|---|---|
| Silhouette | one round fuzzy bee-ball, tiny wings | segmented insect, 4 veined wings, 6 legs | big round head + plump striped body, layered wings |
| Face | huge solid eyes, blush | **compound eyes** (sphere clusters), mandibles, no mouth | big teal-iris eyes, blush |
| Mutant identity | tiny static spark on the stinger | glowing charge organ in the abdomen | lightning-bolt antenna tips + glass charge cell with spark |
| Notes | very cute, generic bee | strong "mutant bug" but loses the pet feeling | reads as a pet *and* as electric |

### All nine at gameplay distance (~30 studs)
![[creature-all9-at-30-studs.jpg]]
A and C eyes stay readable; B faces mostly disappear at this distance (only silhouettes carry them).

## 7. Face language → [[Creature Face Language]]
![[creature-face-expressions-frostpup-C.jpg]]
*Neutral, Happy, Curious, Sleepy, Upset (low wellbeing). All built from the same eye/lid/mouth parts.*

## 8. Material, lighting and rarity rules (applied in all 9)
- **Matte first:** SmoothPlastic fur/skin, Fabric fuzz, Grass moss, Wood roots. **Neon only** for eye glints and one small mutant organ (cores, sparks, seeds), always smaller than the eye.
- **Rarity is NOT "brighter":** rarity tiers would add silhouette detail and growths (e.g. Frostpup Common = 3 crystals → Rare = shoulder crystals → Epic = crystal crown + breath frost VFX), plus the existing world ring and scale. Commons stay fully polished.

## 9. Recommendation
- **UI:** direction **C** (balanced). Keep B's Mission Journal ideas (stamps, stickers) as accents for reward moments only.
- **Creatures:** direction **C** as the base: head ≈ body, big iris eyes with two highlights, a clear species anatomy, one small mutant organ. Borrow from A the blush and paw pads (cuteness). Use B's anatomy only as **rarity growth** (higher tiers add B-style crystals, roots, extra wings).
- **Blender/MeshPart candidates:**
  - **Frostpup**: the fur body still reads "balloon" at close range. It would gain the most from a single smooth mesh body with the face kept as parts.
  - **Sparkbug B / insect bodies**: segmented chitin is hard in parts.
  - **Mossbit**: works well in parts.

## 10. Performance implications
| | Overnight prototypes | New directions |
|---|---|---|
| Parts per creature | 13–21 | **24–47** (A 24–41, B 35–47, C 35–44) |
| 48 creatures in view | ~900 parts | ~2,000 parts (C) |

- Parts are anchored, non-colliding and non-queryable, so the cost is draw calls and the animator's per-part CFrame writes. The animator moves only Role parts, so it doesn't scale linearly.
- **Mitigations for implementation:**
  - LOD: beyond 40 studs, hide face micro-parts (glints, blush, lids, about 10 parts).
  - A mesh body for the highest-count species.
  - Keep the 24-animated cap.
- Not yet measured on a device. Studio frame rate is throttled when the window is backgrounded.

## 11. Blocked on owner selection
1. Pick a UI direction (A / B / C or a mix).
2. Pick a creature direction (A / B / C or a mix), and whether Frostpup-style fur bodies go to Blender meshes.
3. Then: implement the chosen UI on the real HUD/rails + Goals and Index first; rebuild the 7 body-plan prototypes in the chosen style; **only after a second review, the other species.**
