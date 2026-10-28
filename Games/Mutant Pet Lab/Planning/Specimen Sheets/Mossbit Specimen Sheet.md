---
type: specimen-sheet
game: "[[Mutant Pet Lab]]"
species: "[[Mossbit]]"
body_plan: Sprout
rarity: Common
habitat: Botanical
sheet_status: style-anchor
production_status: "Style Anchor (Blender MeshPart), awaiting owner style review"
body_family: Sprout
review_flag: "owner style review (Frostpup + Mossbit anchors)"
updated: 2026-10-21
source: "Blender MutantPetLab/blender/mossbit_style_anchor.blend -> MeshParts in ReplicatedStorage.MutantPetLab.Creatures.Species.Mossbit (2026-10-21)"
tags:
  - mutant-pet-lab
  - specimen-sheet
---
# Mossbit · Specimen Sheet

> [!success] Production model: **Blender style anchor** (2026-10-21), awaiting owner style review
> The second style anchor proves the blueprint style works for a plant organism ([[Style Anchor Review 2026-10-21]]). The part-built C1–C3 model is **ARCHIVED / EXPERIMENTAL, not deleted**: `ServerStorage.MPL_DesignReview.Archive.Mossbit_PartBuilt_C3`. Its notes are kept below as history.

## Blender production model (2026-10-21)
![[mossbit-blender-34.png|420]] ![[mossbit-blender-front.png|300]]
![[mossbit-blender-side.png|300]] ![[mossbit-blender-back34.png|300]]
![[mossbit-blender-silhouette-side.png|260]] ![[mossbit-blender-silhouette-front.png|260]]

| Field | Value |
|---|---|
| Design | A cute collectible organism first, mutant biology second: a chubby leaf-green bean body, a **drooping leaf hood** (7 broad low-poly blades in two greens + a forehead fringe), a **pink tulip bud** on a stem with 2 sprout leaves and a small pollen core, leaf arms, a moss cluster on the back, **chunky root feet** with stubby root toes. Not a mesh copy of the old part model |
| Source | `MutantPetLab/blender/mossbit_style_anchor.blend` → `Mossbit_StyleAnchor.fbx` → Studio 3D Importer (meshes uploaded as assets; place not published) |
| Meshes | **11 MeshParts**: Body, HoodDark, HoodLight, Stem, Petals, BudCore, Moss, LeafArmL/R, RootFootL/R |
| Face | 10 Roblox parts from the expressive face system (amber iris, pupil, glint ×2, mouth ×2, blush ×2), refit onto the new head with 15% larger eyes |
| Triangles | **594** (Moss 100, Petals 80, root feet 160, hood 98, body 60, stem 48, core 20, arms 28) |
| Materials | Matte SmoothPlastic, **soft (smaller, fewer) facets**: body (128,204,98), hood dark (70,160,78) / light (112,196,92), stem (66,140,72), moss (78,140,64), petals (255,168,206), roots (134,96,62); pollen core Neon (255,236,140), the only glow (biologically justified: bioluminescent pollen) |
| Roles | Body: body, stem, moss · Crown: hood (gentle sway) · Accent: petals, leaf arms · Glow: pollen core · Leg: root feet · Eye: iris, pupil, glint |
| LOD | Close: everything. Medium (40–90): mouth + blush hidden. Far (90–140): silhouette (body, hood, bud, stem, arms, feet); moss, pollen core and eyes hidden. Culled > 140 |
| Animation cost | close 25.5 µs · medium 23.3 µs · far 13.7 µs per creature per frame (best of 5, 200 steps) |
| Scale | DisplayScale ×1.15 (unchanged), ≈ 3.5 studs tall with the bud |

### In-game validation (2026-10-21, Studio Play, Mock profile)
| Check | Result |
|---|---|
| Real pen + roaming | Pass. Placed + assigned through the normal Place/Assign requests; roams and faces the player |
| Floor height | Pass. Resting height on the floor; the shared walk hop moves feet ±0.2 (same as every species) |
| Orientation | Pass. The face leads the movement (face direction · look direction = 1.00) |
| Clipping | None seen front / side / back / 3/4 |
| 30 studs | Pass. Green body, leaf hood and pink bud read; smaller than Frostpup (Common scale) |
| Flower/bud identity | Pass. The tulip bud is the clearest feature from the front and side |
| Leaf-hood identity | Pass. Reads as a leafy hood from front and 3/4; from directly behind it reads a little like a cabbage (known issue) |
| Face readability | Pass. Amber eyes + glints, blush, small mouth |
| Creatures viewer | Pass |
| Index | Pass. Card + detail panel |
| Specimen Showcase | Pass |
| Standard vs **Luminous** | Standard: pale pink bud. Luminous: **glowing hot-pink bud** + pollen core, sparkles close up; leaves stay matte (tint (255,80,175), mix 0.75, leaf arms opt out) |
| Expressions | Blink + Curious tilt work. Happy / sleepy / low-wellbeing are not implemented in game code yet (any species); the face stays separate parts so they can be added |

![[sbs-front.jpg|420]] ![[sbs-luminous-close.jpg|420]]
![[mossbit-viewer.jpg|420]] ![[sbs-index.jpg|420]]
![[mossbit-showcase.jpg|420]]

### Known issues
- The hood reads as a cabbage from directly behind (could add a leaf-tip curl or vein colour).
- Mossbit is small at 30 studs (Common scale): fine for a common, but recheck in a busy ranch.
- The face is a flat-part overlay: at extreme side angles the eyes sit a hair proud of the mesh.

---
## History: part-built C1–C3 model (archived 2026-10-21)

> [!success] Production status: **Baseline Approved** (C3, 2026-10-21)
> The seven body-plan baselines were approved for roster conversion after the C3 review ([[C3 Review 2026-10-21]]).

| Header | Value |
|---|---|
| Species · Body plan | **Mossbit** · Sprout |
| Rarity · Habitat | Common · Botanical |
| Descriptor | FOREST SPROUT. *A tiny forest companion with mossy sensory tufts.* |
| Scale vs avatar | DisplayScale ×1.15 |
| Parts (close / medium / far) | 25 / 21 / 19 |
| Favourite food · Sample class | Voltleaf · Organic |
| Review flag | none |

## Production checklist (C3 fields)
| Field | Value |
|---|---|
| **Production status** | Baseline Approved (Experimental → Baseline Approved → Final) |
| **Body family** | Sprout |
| **Silhouette test** | Pass: round sprout + leaf hood + bud stem + root feet. |
| **Gameplay-distance test** | Pass. |
| **Variant readability** | Luminous: bud + leaf arms glow; Chromatic shifts leaf hue strongly (check it stays 'plant'). |
| **Animation notes** | Sprout sway of the leaf crown. |
| **LOD notes** | Standard C1. |
| **Estimated part/mesh cost** | 25 parts close. |
| **C3 changes** | No model change in C3. |

## Views
| Front | Side | Back | Silhouette |
|---|---|---|---|
| ![[mossbit-front.jpg|220]] | ![[mossbit-side.jpg|220]] | ![[mossbit-back.jpg|220]] | ![[mossbit-silhouette.jpg|220]] |

## Expression
Approved face language ([[Creature Face Language]]): neutral · happy (closed-eye) · curious (head tilt; Curious trait tilts toward the player) · sleepy · sad/tired (low wellbeing, **never angry**). Blink every 3–6 s near the camera.

## Materials
Matte leaf-green round body, leaf hood, root feet (brown), moss patch on the back. **Not faceted** (plant).

## Mutant feature
Glass flower bud with a small glowing core on a stem; moss patch.

## Glow / accent location
Bud core only.

## Rarity differences
Common: no marker. Higher tiers: more petals, a second bud, vine tail.

## Variant looks
Luminous: glow organs go Neon + pulse · Chromatic: accent hue drift · Prismatic: glass accents + sparkle. Stronger variant language is candidate C-V1 ([[Variant Visual Language]]).

## Mutation lineage / inheritance
Eggs: Field Research (22%), Botanical Culture (30%). Parent in: +Sparkbug → Bloomtail · +Slimelet → Gloamgel · +Rockling → Pebbletoad · +Embercub → Thornling · +Frostpup → Miremoth. **Inheritance cue:** leaf hood / moss patch.

## Known issues / next pass
Chromatic variant hue-shifts the leaves strongly (magenta in the C2 capture): fine as a variant read, but check it stays 'plant'.
