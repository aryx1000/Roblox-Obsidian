---
type: reference
category: visual-fingerprint
status: active
reviewed: 2026-10-20
decision_status: summary (approved items cite Design Decisions; everything else is a preference, not a decision)
tags:
  - reference
  - mutant-pet-lab
---
# MPL Visual Fingerprint

The owner's recurring visual preferences, condensed from every owner-added reference ([[Owner Reference Library]] R1–R14, [[Index Collection Screen]], [[Shop Storefront Layout]]) plus owner feedback and approved [[Design Decisions]].

**How to read the tags:**
- **Rule:** an item appears only if **several references or an explicit owner comment** support it.
- **APPROVED:** comes from a Design Decision.
- **PREF:** supported by ≥2 references or an explicit comment.
- **NEEDS CONFIRMATION:** thin evidence.

Check [[Do Not Copy]] alongside this note.

**Identity (APPROVED):** cozy bio-lab ranch with a mutant-lab identity. Welcoming, but strange biology, research equipment and glowing mutation energy, with cute creatures living in it.

## UI
| Aspect | Fingerprint | Evidence |
|---|---|---|
| Navigation placement | **Side rails**, bottom of the screen clear, icon-first; labels only on wide screens | APPROVED (Direction C); R6 (BGSI right rail) |
| Panel hierarchy | **One framed modal at a time**: dark outer frame, light inner page, **one focal element** (detail card / hero banner / current task) | APPROVED; [[Index Collection Screen]], R1, R2 |
| Title / header | **Big bold outlined title on a plate** sitting on the frame; **big red X** close | PREF: Index ref, R1, R2, R14 |
| Card density | **Grids of large picture tiles**, 3–4 across; name + one short line (odds, price or stat) | PREF: R1, R2, R5, R14, Index ref |
| Undiscovered | **Dark silhouettes + "???"** | PREF (explicit, R1); Index ref; R5 |
| Odds | **Odds shown visibly** (% or "1 in N") on egg contents and the Index | PREF: R2, R5, R6, R9, Index ref. The approved hatch spec keeps odds *out of the reveal moment*; showing chance on the hatch card (R9) is **NEEDS CONFIRMATION** |
| Icon style | **Illustrated, chunky, colourful icons** (objects, not flat glyphs) | PREF: R7 hex icons, R5 Items/Pets, R2 money stacks, R6 tiles. MPL still uses emoji placeholders |
| Colour usage | **Rarity colour as the card background**; saturated gradients on buttons; green → purple mutation accent | APPROVED (accent); PREF: R1, R14, Index ref |
| Progress | A **completion bar with a reward** next to collections and tasks | PREF: R1, Index ref |
| Locked states | **Dark + lock/chains**, still visible as a goal | PREF (explicit, R8); R7 "???" hexes |
| Repeatedly disliked | Bottom nav bar · oversized HUD · flat white admin panels / stacked cards · text walls · grey dev boxes | Owner feedback 2026-10-16 (APPROVED as rules) |

## Creatures
| Aspect | Fingerprint | Evidence |
|---|---|---|
| Proportions | **Chunky, chibi**, head ≈ body or bigger, short limbs | APPROVED (Frostpup LEFT, C language) |
| Eyes / face | **Big glossy eyes with highlights**, expressive; shapes vary by family | APPROVED ([[Creature Face Language]]); R4 bunny, PS99-style refs |
| Silhouette | Species identity from **anatomy** (ears, crowns, wings, coils), never colour alone | APPROVED; R11, R13 strong silhouettes |
| Motion | **Always animated**; judged **from every angle in motion** | PREF (explicit): R11 "detailed and animated", R13 "display pet animations so I can look at them properly" |
| Production | **Designed on the MPL Creature Specimen File first** (blueprint: front/side/back/top, parts, face, palette, add-ons, scale, lineage) | PREF (explicit): R12 "you should do the same", R15 owner template, R16 Frostpup example |
| Materials | Matte, soft; Neon only for organs / elemental accents | APPROVED (glow rule) |
| Surface finish | **Faceted / low-poly**: crisp planar facets (crystal fur, faceted shells), not smooth balloon ellipsoids | PREF: R16 Frostpup example (owner-made), R11 Leviathan, R10 Voidheart egg; research: Build a Zoo / Raise Animals. **The C1 models are smooth, so this is the biggest look gap** |
| Mutant feature scale | **One bold feature** that frames the body (R16's ice mane collar) rather than several small bits | PREF: R16; APPROVED "one memorable mutant feature" |
| Mutation features | One memorable mutant feature per species; "cute first, mutant second" | APPROVED |
| Rarity treatment | Higher rarity = **more anatomy, detail, platform/aura**, not brighter | APPROVED; R9/R11 hero-tier detail |
| High-tier fantasy | Dragon / serpent / leviathan-class heroes for top rarities | **NEEDS CONFIRMATION**: only R11 + R13 ("cool pets can have a design like that") |
| Never generic | Same eyes / same body / sphere + accessories / colour-only species / whole-body glow | APPROVED |

## Buildings / World
Owner references are **thin** here: only R3, R5, R6 and R8 show world architecture. Most rows rely on approved map decisions.

| Aspect | Fingerprint | Evidence |
|---|---|---|
| Building silhouettes | Distinct per function, readable from plot paths | **NEEDS CONFIRMATION**: no owner building refs. Map decisions approve a landmark Reactor + valley composition |
| Signage | **Big, simple, outlined world labels**; **floor-painted words** at stations ("EGGS", "SPOTTED EGG") | PREF: R5, R6 (floor text), R8 (wooden sign) |
| Physical displays | **Things for sale are physically shown in the world** (eggs on pedestals with price plates) | PREF (explicit): R8; R5, R6 |
| Lab architecture | Research equipment + glowing mutation energy | APPROVED (identity). Form/style **NEEDS CONFIRMATION** |
| Ranch architecture | Wood and natural materials allowed in the world | APPROVED (UI skin decision says the *world* may use wood) |
| Paths / plots | Visible grid while building; clean plot edges | PREF (explicit): R3 |
| Environmental detail | Bright, readable, saturated; biomes per plot gap | APPROVED (map) |

## Eggs / Hatching (strongest category: 7 of 14 owner entries)
| Aspect | Fingerprint | Evidence |
|---|---|---|
| Egg design | **Eggs as trophy objects**: high-tier eggs get wings / halo / cage / orbit rings / altar; element-themed (lava cracks for fire) | PREF (explicit): R10 ×2, R9 |
| Interaction | **The player taps/clicks the egg to crack it** | PREF (explicit): R4 |
| Approach | **Odds appear when you walk up to the egg**; Open ×1 (×3 asked) | PREF (explicit): R5; R6. Multi-open is **NEEDS CONFIRMATION** |
| Anticipation | Light leaks from cracks; dark backdrop for big hatches | PREF: R9, R4; APPROVED tiers |
| Crack / reveal | Short, readable; **"New!" stamp**; discovery label **over the pet in the world** | PREF: R4, R5 |
| Rarity escalation | **The animation gets "crazier" with egg difficulty** | PREF (explicit): R9; APPROVED tiers |
| Result card | **Stat card**: rarity word, name, rarity (+ chance?), one-line description, one button | PREF (explicit): R9 |

## Game feel
| Aspect | Fingerprint | Evidence |
|---|---|---|
| Transitions | Snappy pop/slide; one panel at a time | APPROVED (UI kit) |
| VFX | Restrained everyday; spectacular at reward moments | APPROVED (no constant particles) + R9/R10 |
| Sound | No owner audio references yet | **NEEDS CONFIRMATION** (sound review gate approved) |
| Reward moments | Big text stamps ("New!", "LEGENDARY!"), short numbers, one confirm button | PREF: R4, R5, R9 |
| Physical world interaction | Walk up → it reacts (odds popup, egg in the world, pet appears in the world) | PREF: R5, R8, R4 |
