---
type: specimen-sheet
game: "[[Mutant Pet Lab]]"
species: "[[Pebbletoad]]"
body_plan: Hopper
rarity: Uncommon
habitat: Geological
sheet_status: blender-anchor
production_status: "Blender Anchor (production model), pending the 7-anchor review"
body_family: Hopper
review_flag: "none"
updated: 2026-10-22
source: "Studio template ReplicatedStorage.MutantPetLab.Creatures.Species.Pebbletoad (C1 + C2 refinements)"
tags:
  - mutant-pet-lab
  - specimen-sheet
---
# Pebbletoad · Specimen Sheet

## Blender production spec (2026-10-22, before modelling)
Approved direction: [[Design Decisions#Production creature style: Frostpup + Mossbit Blender anchors approved]]. Surface: **soft animal planes** for the toad body + **strong rock faceting** only on the stones.

| Field | Target |
|---|---|
| Silhouette | **Squat, wide hopper**: low broad body with the head merged in front, two raised **eye domes** on top, big folded **hind haunches** at the back sides, small front feet with toe pads. Not stacked spheres: one continuous body volume |
| Face | Curious and friendly: golden eyes high in the domes (Roblox face parts), wide soft smile line, blush. Never grumpy |
| Mutant feature | **River-stone carapace**: 4 flat, strongly faceted stones **sunk into the back** (anatomy, not stuck on) + a moss tuft between them (from the Rockling + Mossbit lineage) |
| Materials | Body moss-green (132,150,90), cream throat/belly **low on the underside** (222,212,160), stones (128,124,120) Slate-grey, moss (86,140,64); all matte |
| Roles | Body: body, eye domes, belly · Leg: haunches, feet · Accent: stones · Body: moss · Eye: face |
| Luminous | The stones glow **warm amber like a geode** (tint (255,170,60), mix 0.6); moss + body stay matte |
| LOD | Medium: mouth + blush hidden. Far: silhouette (body, domes, haunches, stones); moss, belly, eyes hidden |
| Budget | ≤ 650 triangles, ≤ 12 meshes |


> [!success] Production status: **Baseline Approved** (C3, 2026-10-21)
> The seven body-plan baselines were approved for roster conversion after the C3 review ([[C3 Review 2026-10-21]]).

| Header | Value |
|---|---|
| Species · Body plan | **Pebbletoad** · Hopper |
| Rarity · Habitat | Uncommon · Geological |
| Descriptor | RIVER-STONE HOPPER. *A squat geological hopper that resembles a river stone.* |
| Scale vs avatar | DisplayScale ×1.10 |
| Parts (close / medium / far) | 23 / 18 / 15 |
| Favourite food · Sample class | Quartzroot · Mineral |
| Review flag | none |

## Blender production model (2026-10-22)
![[pebbletoad-blender-34.png|420]] ![[pebbletoad-blender-front.png|300]]
![[pebbletoad-blender-side.png|300]] ![[pebbletoad-blender-back34.png|300]]
![[pebbletoad-blender-silhouette-side.png|260]] ![[pebbletoad-blender-silhouette-front.png|260]]

| Field | Result |
|---|---|
| Source | `MutantPetLab/blender/pebbletoad_style_anchor.blend` → `Pebbletoad_StyleAnchor.fbx` (imported 2026-10-22) |
| Meshes / triangles | **9 MeshParts, 688 tris**: Body (+ eye domes) 200, ToePads 120, Stones 100, Moss 60, HaunchL/R 60 each, Belly 48, FrontFootL/R 20 each (slightly over the 650 target; acceptable) |
| Shape | One continuous squat body (not stacked spheres), raised eye domes, folded haunches, front feet with cream toe pads, low cream throat |
| Mutant feature | 5 bold faceted river stones bedded in the back + moss between them (Rockling + Mossbit lineage). v1 stones were too small to read; v2 enlarged + raised |
| Face | Old face set (golden iris, pupil, glints, mouth, blush) reseated into the eye domes, eyes nudged forward 0.05 after the side check; curious/friendly read kept |
| In-game fit | Pen + roaming pass, faces the player (1.00); feet mean 1.57–1.60 on a 1.50 floor (hopper hop drives the max) |
| 30 studs | Reads as a green toad with a grey stone back |
| Animation | Hopper hop + blink; cost **10.1 µs close · 15.6 medium · 10.4 far** (best of 5; medium/far within noise) |
| LOD | Medium: mouth, blush, toe pads, second glints hidden. Far: silhouette (body, haunches, feet, stones, belly); moss + eyes hidden |
| Luminous | Stones glow **warm amber like a geode** (tint (255,170,60), mix 0.6); body + moss matte. Visible in the lineup |
| Viewer / Index | Pass. Card (NEW) + detail panel |

![[pebbletoad-blender-vs-parts-studio.jpg|420]] ![[pebbletoad-blender-lineup.jpg|420]]
![[pebbletoad-blender-pen-30studs.jpg|420]] ![[pebbletoad-blender-viewer.jpg|420]]
![[pebbletoad-blender-index.jpg|420]]

Old part-built model: **ARCHIVED / EXPERIMENTAL** in `ServerStorage.MPL_DesignReview.Archive.Pebbletoad_PartBuilt_C3`.

## History: part-built C3 production checklist (archived 2026-10-22)
| Field | Value |
|---|---|
| **Production status** | Baseline Approved (Experimental → Baseline Approved → Final) |
| **Body family** | Hopper |
| **Silhouette test** | Pass: wide squat body + raised eye bumps + pebble back. |
| **Gameplay-distance test** | Pass: yellow eyes + pebbles read at 30 studs. |
| **Variant readability** | Luminous: pebbles + moss glow warm. |
| **Animation notes** | Hopper bounce (no negative bob). |
| **LOD notes** | Medium hides second glints, blush. |
| **Estimated part/mesh cost** | 23 parts close. |
| **C3 changes** | No model change in C3 (C2 eye fix kept). |

## Views
| Front | Side | Back | Silhouette |
|---|---|---|---|
| ![[pebbletoad-front.jpg|220]] | ![[pebbletoad-side.jpg|220]] | ![[pebbletoad-back.jpg|220]] | ![[pebbletoad-silhouette.jpg|220]] |

## Expression
Approved face language ([[Creature Face Language]]): neutral · happy (closed-eye) · curious (head tilt; Curious trait tilts toward the player) · sleepy · sad/tired (low wellbeing, **never angry**). Blink every 3–6 s near the camera.

## Materials
Matte moss-green toad skin, cream belly, grey pebble growths with a moss patch on the back. Faceting only on the pebble growths (geological accent), not the soft body.

## Mutant feature
Pebble growths + moss on the back.

## Glow / accent location
None.

## Rarity differences
Uncommon: subtle green ground tint. Higher tiers: more pebbles, a crystal in the largest stone.

## Variant looks
Luminous: glow organs go Neon + pulse · Chromatic: accent hue drift · Prismatic: glass accents + sparkle. Stronger variant language is candidate C-V1 ([[Variant Visual Language]]).

## Mutation lineage / inheritance
Egg: Unstable Mutagen (12%). Mutation: **Rockling + Mossbit → Pebbletoad** (stone back from Rockling, moss from Mossbit). Parent in: Fungloom + Pebbletoad → Sporephant.

## Known issues / next pass
C2 2026-10-20: default eyes changed from sleepy to curious/friendly (round pupils, bigger glints, second sparkle). In profile the iris reads as a flat disc on the eye bump (part-based limit): a domed iris mesh would fix it later. Mouth is hidden behind the belly at the default camera.
