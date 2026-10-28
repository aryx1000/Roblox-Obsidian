---
type: specimen-sheet
game: "[[Mutant Pet Lab]]"
species: "[[Magmawisp]]"
body_plan: Wisp
rarity: Epic
habitat: Thermal
sheet_status: blender-anchor
production_status: "Blender Anchor (production model), pending the 7-anchor review"
body_family: Wisp
review_flag: "none (Epic)"
updated: 2026-10-22
source: "Studio template ReplicatedStorage.MutantPetLab.Creatures.Species.Magmawisp (C1 + C2 refinements)"
tags:
  - mutant-pet-lab
  - specimen-sheet
---
# Magmawisp · Specimen Sheet

## Blender production spec (2026-10-22, before modelling)
Approved direction: [[Design Decisions#Production creature style: Frostpup + Mossbit Blender anchors approved]]. Surface: **wisp = floating layered forms**.

| Field | Target |
|---|---|
| Silhouette | A floating **teardrop spirit**: round warm-orange body, a **layered flame crest** (3 flame petals) on top, little nub arms, a **curling ember tail** trailing underneath (no legs, it hovers), and 3 small **basalt stones orbiting** it. Not a fireball: a clear face, a soft body and a defined crest/tail shape |
| Face | Soft magical expression: big warm-amber eyes (Roblox face parts), blush, small smile. Never hostile: no brows, no fangs |
| Mutant feature | **Cooled basalt crust plates** on the lower body with thin magma seams between them (anatomy integrated in the body), and orbiting basalt stones |
| Materials | Body orange (230,108,56) matte; belly peach (255,196,120); crest orange → yellow; crust plates basalt (66,50,48); seams + crest core Neon (255,200,90), **the only glow**, kept thin |
| Roles | Body: body, belly, crust · Crown: crest petals (sway) · Glow: crest core, seams · Accent: arms · Tail: ember tail · Orbit: 3 stones (separate meshes) · Eye: face |
| Luminous | Crest + seams brighter **golden** (tint (255,190,60), mix 0.6); crust + body stay matte, so it doesn't become a neon blob |
| LOD | Medium: mouth + blush hidden. Far: silhouette (body, crest, tail, stones); seams + eyes hidden |
| Budget | ≤ 650 tris |


> [!success] Production status: **Baseline Approved** (C3, 2026-10-21)
> The seven body-plan baselines were approved for roster conversion after the C3 review ([[C3 Review 2026-10-21]]).

| Header | Value |
|---|---|
| Species · Body plan | **Magmawisp** · Wisp |
| Rarity · Habitat | Epic · Thermal |
| Descriptor | MOLTEN MINERAL SPIRIT. *A hovering mineral spirit with a controlled molten core.* |
| Scale vs avatar | DisplayScale ×1.0 (Epic rarity scale ×1.2) |
| Parts (close / medium / far) | 23 / 19 / 17 |
| Favourite food · Sample class | Quartzroot · Thermal |
| Review flag | none (Epic) |

## Blender production model (2026-10-22)
![[magmawisp-blender-34.png|420]] ![[magmawisp-blender-front.png|300]]
![[magmawisp-blender-side.png|300]] ![[magmawisp-blender-back34.png|300]]
![[magmawisp-blender-silhouette-side.png|260]] ![[magmawisp-blender-silhouette-front.png|260]]

| Field | Result |
|---|---|
| Source | `MutantPetLab/blender/magmawisp_style_anchor.blend` → FBX (imported 2026-10-22) |
| Meshes / triangles | **11 MeshParts, 672 tris**: Body 144, CrestSide 112, Crust 100, CrestMain 56, CrestCore 56, EmberTail 56, Seams 48, Arms 40, Stone1-3 20 each |
| Iterations | v1: front crust plate read as a beak, the belly patch as a muzzle, the crest too small, the tail hidden → v2: crust moved to back + sides, bolder crest, but needle flames read hostile → **v3** soft bulb-shaped flame petals and a back-swept tail |
| Face | Old face set (amber eyes) on the body front, ×0.95; friendly, no brows |
| In-game fit | Hovers ≈ 2.1 studs above the floor (Wisp plan hover 1.7 + bob); **rarity ring stays on the ground** (1.64); faces the player |
| Orbit stones | 3 separate Orbit meshes, circling at body height; they never cross the face in the front view |
| 30 studs | Reads as a floating orange spirit with a yellow crest |
| Animation | Wisp bob + orbit + crest sway (Crown) + tail wag + blink: **21.6 µs close · 18.5 medium · 13.6 far** |
| LOD | Medium: mouth + blush hidden. Far: silhouette; seams + eyes hidden |
| Luminous | Crest core + seams glow **gold** (tint (255,190,60), mix 0.6); arms opt out; body + crust stay matte |
| Viewer | **Bug found + fixed:** the viewer framed hovering creatures at rest height, so the animated wisp floated out of frame (crest cut off). `CreatureDetailController` now adds the plan's hover to the frame centre. This fixes every Flyer/Wisp |
| Index | Pass |

![[magmawisp-rockling-studio-front.jpg|420]] ![[magmawisp-rockling-pens-30studs.jpg|420]]
![[magmawisp-viewer-before-hover-fix.jpg|420]] ![[magmawisp-blender-viewer-luminous.jpg|420]]

Old part-built model: **ARCHIVED / EXPERIMENTAL** in `ServerStorage.MPL_DesignReview.Archive.Magmawisp_PartBuilt_C3`.

## History: part-built C3 production checklist (archived 2026-10-22)
| Field | Value |
|---|---|
| **Production status** | Baseline Approved (Experimental → Baseline Approved → Final) |
| **Body family** | Wisp |
| **Silhouette test** | Pass: round floating body + flame tuft + orbit stones. |
| **Gameplay-distance test** | Pass: orange + stones read at 30 studs. |
| **Variant readability** | Luminous: arms + chest crack glow (flame already glows). |
| **Animation notes** | Hover + orbiting stones. |
| **LOD notes** | Standard C1. |
| **Estimated part/mesh cost** | 24 parts close. |
| **C3 changes** | No model change in C3 (C2 face fix kept). |

## Views
| Front | Side | Back | Silhouette |
|---|---|---|---|
| ![[magmawisp-front.jpg|220]] | ![[magmawisp-side.jpg|220]] | ![[magmawisp-back.jpg|220]] | ![[magmawisp-silhouette.jpg|220]] |

## Expression
Approved face language ([[Creature Face Language]]): neutral · happy (closed-eye) · curious (head tilt; Curious trait tilts toward the player) · sleepy · sad/tired (low wellbeing, **never angry**). Blink every 3–6 s near the camera.

## Materials
Matte warm-orange body, cream muzzle, basalt orbit stones (faceting allowed on the stones: geological accent), ember tail.

## Mutant feature
Flame tuft (one small glowing lobe), basalt chest crack, three orbiting stones.

## Glow / accent location
Flame core + chest seam only.

## Rarity differences
Epic: rarity scale ×1.2 + ground tint under the hover. Legendary relatives would add a molten crown / more stones (flag for review).

## Variant looks
Luminous: glow organs go Neon + pulse · Chromatic: accent hue drift · Prismatic: glass accents + sparkle. Stronger variant language is candidate C-V1 ([[Variant Visual Language]]).

## Mutation lineage / inheritance
Eggs: Thermal Core (13%), Unstable Mutagen (6%). Mutation: **Slimelet + Rockling → Magmawisp** (molten core in a gel body from Slimelet, stones from Rockling). Parent in: + Slimelet → Fluxaroo.

## Known issues / next pass
C2 2026-10-20: expression softened (lower muzzle patch, bigger round eyes, centred pupils, bigger glints, small smile) so it reads magical, not angry.
