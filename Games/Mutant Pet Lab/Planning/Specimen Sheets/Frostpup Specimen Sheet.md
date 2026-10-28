---
type: specimen-sheet
game: "[[Mutant Pet Lab]]"
species: "[[Frostpup]]"
body_plan: Critter
rarity: Rare
habitat: Cryogenic
sheet_status: style-anchor
production_status: "Style Anchor (Blender MeshPart), awaiting owner style review"
body_family: Critter
review_flag: "owner style review (Frostpup + Mossbit anchors)"
updated: 2026-10-21
source: "Blender MutantPetLab/blender/frostpup_style_anchor.blend -> MeshParts in ReplicatedStorage.MutantPetLab.Creatures.Species.Frostpup (2026-10-21)"
tags:
  - mutant-pet-lab
  - specimen-sheet
---
# Frostpup · Specimen Sheet

> [!success] Production model: **Blender style anchor** (2026-10-21), awaiting owner style review
> Built from the owner's blueprint ([[Owner Reference Library#R16 · Frostpup filled example (added 2026-10-20)|R16]]) under [[Design Decisions#Creature style: every pet follows the blueprint Frostpup (R16)]]. The earlier part-built C3 hybrid is **archived, not deleted**: `ServerStorage.MPL_DesignReview.Archive.Frostpup_PartBuilt_C3`. Its notes are kept below as history.

## Blender production model (2026-10-21)

![[frostpup-blender-34.png|420]] ![[frostpup-blender-front.png|300]]
![[frostpup-blender-side.png|300]] ![[frostpup-blender-back34.png|300]]
![[frostpup-blender-silhouette-side.png|260]] ![[frostpup-blender-silhouette-front.png|260]]

| Field | Value |
|---|---|
| Source | `MutantPetLab/blender/frostpup_style_anchor.blend` → `Frostpup_StyleAnchor.fbx` → Studio 3D Importer (meshes uploaded as assets, place not published) |
| Meshes | **15 MeshParts**: Body (body + head + muzzle + fur tufts), EarL/R, IceMane (collar + chest bib + back spikes), PaleAccent (crest + inner ears), Tail, TailTip, 4 legs, 4 paws |
| Face | 11 Roblox parts kept from the expressive face system (iris, pupil, glint ×2, nose, mouth ×2, blush ×2), moved onto the new head with 20% larger eyes |
| Triangles | **712** (Body 196, IceMane 272, legs + paws 160, tail 40, accents 32, ears 12) |
| Parts close / medium / far | 27 (+ rarity ring) / 23 / 9 meshes + ring |
| Materials | Fur white (244,249,255) SmoothPlastic, flat-shaded facets · pale-blue (160,214,248) paws, inner ears, crest, tail tip · ice collar (110,214,255) Glass |
| Mutant anatomy | One bold **ice-crystal collar** (2 rings + chest bib) + 3 back spikes, as in the blueprint |
| Roles (animation) | Body: body, ears · Leg: legs, paws · Tail: tail, tail tip (wag) · Accent: ice + pale accents (variants recolour these) · Eye: iris, pupil, glint (blink) |
| LOD | **Close** (< 40 studs): everything. **Medium** (40–90): mouth + blush hidden, eyes stay. **Far** (90–140): silhouette only (body, ears, legs, tail, ice collar = 580 tris); paws, tail tip, crest and face hidden. **Culled** > 140 (unchanged). The engine also reduces MeshPart detail automatically at distance |
| Animation cost (best of 5, 200 steps) | close 25–35 µs per creature per frame (old part-built version: 31.4 µs) · medium 18.6 µs · far 12.5 µs |
| Display scale | `DisplayScale.Frostpup` 1.05 → **1.0**: the mesh is ~6% taller, so the in-world size matches the approved C1 size (≈ 4.7 studs with the Rare scale) |

### In-game validation (2026-10-21, Studio Play, Mock profile)
| Check | Result |
|---|---|
| Real pen + roaming | Pass. Two Frostpups assigned to a placed Containment Pen through the normal Place/Assign requests; they roam and turn to face the player |
| Floor height | Pass. Lowest visible part 0.02 studs below the pen floor (no floating, no sinking) |
| Orientation | Pass. Nose leads the movement and faces the player |
| Clipping | None seen in front, side, back and 3/4 views; eyes nudged 0.035 studs into the head after the first check |
| 30-stud gameplay distance | Pass. Faceted white body, big eyes and the ice collar read clearly |
| Creatures viewer | Pass. Rotate, zoom, trait/wellbeing/favourite intact. The pedestal hides the paws slightly (viewer polish) |
| Index | Pass. Card + detail panel show the new model; NEW tag works |
| Specimen Showcase | Pass. Stands on the pedestal; the nameplate stays |
| Standard vs variant | Standard: cyan Glass ice collar. **Luminous (refined 2026-10-21)**: the ice collar + back spikes glow **vivid cyan** (`LuminousTint` (30,165,255), `LuminousMix` 0.85); the crest / inner ears opt out (`LuminousGlow=false`); paws, tail tip and body stay matte; a pulse + cyan sparkles close up. The first version (warm-white tint) went white, see [[Style Anchor Review 2026-10-21]] |
| Expressions | Blink works (Eye parts squash). The Curious trait head-tilt works. **Happy / sleepy / low-wellbeing faces are not implemented in game code yet**, for any species; they exist only in [[Creature Face Language]]. The face is still separate parts, so they can be added without touching the mesh |

![[frostpup-blender-vs-parts-studio.jpg|420]] ![[frostpup-blender-studio-34.jpg|420]]
![[frostpup-blender-pen-close.jpg|420]] ![[frostpup-blender-pen-30studs.jpg|420]]
![[frostpup-blender-viewer.jpg|420]] ![[frostpup-blender-index.jpg|420]]
![[frostpup-blender-showcase.jpg|420]]
![[sbs-luminous-close.jpg|420]] ![[sbs-side.jpg|420]]

### Known issues
- In the Creatures viewer the pedestal hides the paws slightly (viewer polish).
- The face is a flat-part overlay: at extreme side angles the eyes sit a hair proud of the faceted head.

---
## History: part-built C3 hybrid (archived 2026-10-21)

> [!success] Production status: **Baseline Approved (hybrid finish)** (C3, 2026-10-21)
> The seven body-plan baselines were approved for roster conversion after the C3 review ([[C3 Review 2026-10-21]]).

| Header | Value |
|---|---|
| Species · Body plan | **Frostpup** · Critter |
| Rarity · Habitat | Rare · Cryogenic |
| Descriptor | ARCTIC CANID. *A playful cryogenic pup with glittering breath.* |
| Scale vs avatar | DisplayScale ×1.05 (owner R16 target 0.9× avatar) |
| Parts (close / medium / far) | 30 / 22 / 21 |
| Favourite food · Sample class | Quartzroot · Cryogenic |
| Review flag | none (baseline approved; faceted test = method decision) |

## Production checklist (C3 fields)
| Field | Value |
|---|---|
| **Production status** | Baseline Approved (hybrid finish) (Experimental → Baseline Approved → Final) |
| **Body family** | Critter |
| **Silhouette test** | Pass: canid head + ears, quadruped body, crystal collar + crystal tail tip: unique among the seven. |
| **Gameplay-distance test** | Pass: white body + ice-blue ears/crystals read at 30 studs. |
| **Variant readability** | Luminous: ice crystals + ears glow warm-white and pulse; strongest Luminous read of the seven. |
| **Animation notes** | Critter walk/bob; tail (incl. crystal tip) wags; mane shards are static Accents. |
| **LOD notes** | LOD1 (hidden >40 studs): outer mane shards, ridge, toe beans, inner ears, mouth, blush. Medium ~25 parts. |
| **Estimated part/mesh cost** | 35 parts close / ~25 medium (C1 was 30/22). Crystals are CSG facet gems (1 instance each). |
| **C3 changes** | C3 2026-10-21: HYBRID selected over smooth (A) and fully faceted (B). Soft body/head/face kept; one merged body volume; neck fur bridges head/body; faceted ice mane (5 shards) behind the head; spine ridge (2); faceted crystal tail tip; firmer legs. B rejected: the face disappears and it reads as a rock. Remaining limit: body/legs are still rounded part shapes; a single soft Blender body mesh + these crystals is the next quality step (owner decision). |

## Views
| Front | Side | Back | Silhouette |
|---|---|---|---|
| ![[frostpup-front.jpg|220]] | ![[frostpup-side.jpg|220]] | ![[frostpup-back.jpg|220]] | ![[frostpup-silhouette.jpg|220]] |

## Expression
Approved face language ([[Creature Face Language]]): neutral · happy (closed-eye) · curious (head tilt; Curious trait tilts toward the player) · sleepy · sad/tired (low wellbeing, **never angry**). Blink every 3–6 s near the camera.

## Materials
Soft white fur body, ice-blue ears/tail tips/paw beans. **Faceted finish approved for frost** → target is the owner's R16 faceted low-poly crystal look; current C1 build is smooth ellipsoids.

## Mutant feature
Ice-crystal mane / icy fur tufts + one small frost crystal (R16: crystal mane).

## Glow / accent location
None at Common/Rare; frost crystal tip may glow faintly at Epic+ only.

## Rarity differences
Rare: subtle ground tint. Higher tiers grow more crystal mane and crystal shoulder growths (anatomy), never whole-body glow.

## Variant looks
Luminous: glow organs go Neon + pulse · Chromatic: accent hue drift · Prismatic: glass accents + sparkle. Stronger variant language is candidate C-V1 ([[Variant Visual Language]]).

## Mutation lineage / inheritance
Eggs: Field Research (7.5%), Cryogenic Capsule (40%). Parent in: +Gloamgel → Cryolume · +Embercub → Prismaclaw · +Slimelet → Glacierbit · +Sparkbug → Circuitfin · +Mossbit → Miremoth. **Inheritance cue:** canid ears / icy crystals.

## Known issues / next pass
Side view reads as stacked 'balloons' (see the side capture): this is the C1 Blender/MeshPart candidate. Next: build the R16 faceted Frostpup test (Blender flat-shaded MeshPart vs wedges) and compare.
