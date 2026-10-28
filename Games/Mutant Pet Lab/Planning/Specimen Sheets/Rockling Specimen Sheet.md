---
type: specimen-sheet
game: "[[Mutant Pet Lab]]"
species: "[[Rockling]]"
body_plan: Shellback
rarity: Common
habitat: Geological
sheet_status: blender-anchor
production_status: "Blender Anchor (production model), pending the 7-anchor review"
body_family: Shellback
review_flag: "none"
updated: 2026-10-22
source: "Studio template ReplicatedStorage.MutantPetLab.Creatures.Species.Rockling (C1 + C2 refinements)"
tags:
  - mutant-pet-lab
  - specimen-sheet
---
# Rockling · Specimen Sheet

## Blender production spec (2026-10-22, before modelling)
Approved direction: [[Design Decisions#Production creature style: Frostpup + Mossbit Blender anchors approved]]. Surface: **rock/crystal = strongest faceting** (shell); the critter body stays soft planes.

| Field | Target |
|---|---|
| Silhouette | Not a turtle: a **chubby sandy mole-pup** carrying a **geode boulder shell** of interlocking faceted plates, with a **crack across the top where a cyan crystal cluster grows out**. A round head with small round ears and a button snout pokes out of the front, 4 stubby paws, a short tail nub. The shell is taller than it is wide (boulder, not a flat turtle dome) |
| Face | Big friendly brown eyes (Roblox face parts), blush, small smile; reads curious, not grumpy |
| Mutant feature | The geode crack + crystal cluster (its glow core is the only glow) |
| Materials | Shell plates warm grey (130,120,110) + darker rim plates (98,90,82); body sandy (184,162,130); crystals pale cyan (170,225,255) Glass T ≈ 0.1; crystal core Neon (150,235,255) |
| Roles | Shell: shell plates · Body: body, head, ears · Accent: crystals · Glow: core · Leg: paws · Tail: tail nub · Eye: face |
| Luminous | Crystals + core glow **vivid cyan** (tint (60,200,255), mix 0.7); shell + body matte |
| LOD | Medium: mouth + blush hidden. Far: silhouette (shell, head, crystals, paws); core, tail nub, eyes hidden |
| Budget | ≤ 650 tris |


> [!success] Production status: **Baseline Approved** (C3, 2026-10-21)
> The seven body-plan baselines were approved for roster conversion after the C3 review ([[C3 Review 2026-10-21]]).

| Header | Value |
|---|---|
| Species · Body plan | **Rockling** · Shellback |
| Rarity · Habitat | Common · Geological |
| Descriptor | POCKET STONE. *A pocket-sized living stone with a steady core glow.* |
| Scale vs avatar | DisplayScale ×1.12 |
| Parts (close / medium / far) | 22 / 18 / 14 |
| Favourite food · Sample class | Quartzroot · Mineral |
| Review flag | none |

## Blender production model (2026-10-22)
![[rockling-blender-34.png|420]] ![[rockling-blender-front.png|300]]
![[rockling-blender-side.png|300]] ![[rockling-blender-back34.png|300]]
![[rockling-blender-silhouette-side.png|260]] ![[rockling-blender-silhouette-front.png|260]]

| Field | Result |
|---|---|
| Source | `MutantPetLab/blender/rockling_style_anchor.blend` → FBX (imported 2026-10-22) |
| Meshes / triangles | **9 MeshParts, 720 tris**: Shell 180, ShellRim 140, Head 112, Crystals 100, Paws 80, Body 48, Nose / CrystalCore / TailNub 20 each |
| Design | A chubby sandy mole-pup under a **geode-boulder shell** of interlocking strongly-faceted plates, with a crystal crack on top. Not a turtle: the shell is a tall boulder and the head is round with ears and a button snout. v2 enlarged the head ×1.22 for cuteness and trimmed plates for budget |
| Face | Old face set reseated ×1.6 (the old eyes were tiny); big friendly brown eyes |
| In-game fit | Floor: lowest point mean 1.49 on 1.50; faces the player; Shellback waddle |
| 30 studs | Reads by the crystal tuft + grey boulder; small (Common scale) |
| Animation | **20.0 µs close · 17.4 medium · 5.1 far** |
| LOD | Medium: mouth + blush + nose hidden. Far: silhouette (shell, rim, head, crystals, paws, body); core, tail nub, eyes hidden |
| Luminous | First pass (tint (60,200,255), mix 0.7) bloomed white → **fixed to tint (20,165,255), mix 0.9**: vivid cyan crystals; shell rim opts out; body + shell matte |
| Viewer / Index | Pass |

![[magmawisp-rockling-studio-front.jpg|420]] ![[rockling-blender-viewer-luminous.jpg|420]]

Old part-built model: **ARCHIVED / EXPERIMENTAL** in `ServerStorage.MPL_DesignReview.Archive.Rockling_PartBuilt_C3`.

## History: part-built C3 production checklist (archived 2026-10-22)
| Field | Value |
|---|---|
| **Production status** | Baseline Approved (Experimental → Baseline Approved → Final) |
| **Body family** | Shellback |
| **Silhouette test** | Pass: low shell with rim + small head and feet + crystals. |
| **Gameplay-distance test** | Pass. |
| **Variant readability** | Luminous: moss cap + crystals glow. |
| **Animation notes** | Shellback idle (slow); shell is Body. |
| **LOD notes** | Standard C1. |
| **Estimated part/mesh cost** | 22 parts close. |
| **C3 changes** | No model change in C3. |

## Views
| Front | Side | Back | Silhouette |
|---|---|---|---|
| ![[rockling-front.jpg|220]] | ![[rockling-side.jpg|220]] | ![[rockling-back.jpg|220]] | ![[rockling-silhouette.jpg|220]] |

## Expression
Approved face language ([[Creature Face Language]]): neutral · happy (closed-eye) · curious (head tilt; Curious trait tilts toward the player) · sleepy · sad/tired (low wellbeing, **never angry**). Blink every 3–6 s near the camera.

## Materials
Rock-textured grey shell with a rim, cream head/limbs, moss cap, crystal shards. **Faceted finish candidate** (geological) for the shell.

## Mutant feature
Shell crystals with a faint core; moss.

## Glow / accent location
Crystal core only (faint).

## Rarity differences
Common: no marker. Higher tiers: more crystals, a geode opening in the shell.

## Variant looks
Luminous: glow organs go Neon + pulse · Chromatic: accent hue drift · Prismatic: glass accents + sparkle. Stronger variant language is candidate C-V1 ([[Variant Visual Language]]).

## Mutation lineage / inheritance
Egg: Field Research (24%). Parent in: +Sparkbug → Tidegill · +Embercub → Cinderhorn · +Mossbit → Pebbletoad · +Prismaclaw → Geodewisp · +Slimelet → Magmawisp. **Inheritance cue:** stone shell / crystals.

## Known issues / next pass
Faceted shell test after the Frostpup faceting method is chosen.
