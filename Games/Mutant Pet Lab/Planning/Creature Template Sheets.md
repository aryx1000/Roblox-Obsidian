---
type: planning
game: "[[Mutant Pet Lab]]"
area: creatures
status: approved
decision_status: approved (owner, 2026-10-20)
updated: 2026-10-20
tags:
  - mutant-pet-lab
  - planning
  - creatures
---
# Creature Template Sheets ("Creature Specimen File")

> [!success] APPROVED (owner, 2026-10-20)
> **Every final creature gets a specimen sheet before production.** The default template language is **the owner's own MPL blueprint** ([[Owner Reference Library#R15 · MPL Creature Specimen File: blank blueprint template (added 2026-10-20)|R15]]), with the filled Frostpup example ([[Owner Reference Library#R16 · Frostpup filled example (added 2026-10-20)|R16]]). **No full production creature is built until its sheet is approved**, unless the build is clearly marked **Experimental**. [[Design Decisions#Creature template sheets required before production (owner, 2026-10-20)]]
>
> **Required minimum:** front · side · back · silhouette · expression · materials · mutant feature · glow/accent location · rarity differences · mutation lineage / inheritance notes.

![[Pasted image 20261020143330.png|420]] ![[Pasted image 20261020143437.png|420]]

## Fields (owner layout + 3 small additions)
| Field | Content | MPL source |
|---|---|---|
| Header | **Species · Body Plan · Rarity · Habitat** (+ the descriptor line under the name, e.g. "ARCTIC CANID") | `SpeciesConfig`, `CreatureVisualConfig.SpeciesPlan` |
| Hero view | Three-quarter construction drawing → final render | Template / Studio render |
| Front · Side · Back · Top | Orthographic views at the same scale | Studio captures (or concept art) |
| Parts | One tile per part, each with its animator **Role** (Ear → Accent, Tail → Tail, …) | Template parts / Role attributes |
| Face | **5 slots** (owner layout shows 4; the example uses 5): Neutral · Happy · Curious/Alert · Sleepy · Sad/tired (low wellbeing; **never angry**) | [[Creature Face Language]] |
| Palette + materials | 5 swatches + a material note (matte / faceted / glass / Neon accent); **faceted only where the material calls for it** (see *Finish*) | Template |
| **Glow / accent location** (required) | Where Neon may appear (organs, elemental accents, rare features); everything else matte | Approved glow rule |
| Add-ons | **Rarity differences** + **variant looks** (Luminous / Chromatic / Prismatic). Radiant is a trait, shown only as a trait cue | [[Variant Visual Language]] |
| Scale | Height vs the 1.8× avatar (Frostpup example: 0.9×) incl. `DisplayScale` | `CreatureVisualConfig.DisplayScale` |
| Assembly | How the parts join (pivot points for the animator) | Template |
| Lineage | **Mutation species:** parent A + parent B → result, with which feature comes from which parent. **Egg species:** the egg families that hatch it | `RecipeConfig`, `EggFamilyConfig`, inheritance table |
| *+ Mutant feature* (added) | One line: the single memorable mutant feature (e.g. "ice-crystal mane") | Approved style rule |
| *+ Silhouette check* (added; the example already has one) | Black outline of the sheet vs the built model | Studio render vs sheet |

## Workflow (adapted from the owner's R12 pipeline)
1. **Sheet first.** Claude fills header, parts, face, palette, add-ons, scale and lineage from MPL data + the approved style rules.
2. **Concept art:**
   - Claude can't generate images directly here. If an image tool is connected, Claude uses it.
   - Otherwise the owner supplies concept art (as with R16), or Claude fills the views with Studio/Blender renders of a first build.
3. **Build** in Studio parts, or Blender for faceted/hero creatures (see *Finish* below).
4. **Silhouette check:** a black render of the build vs the sheet; fix drift.
5. **Review stage:** front, side, back, top, ~30 studs, in a pen, and moving (owner R13).
6. **Owner approves the sheet + build.** Until then the build is marked **Experimental**.
7. Only then, the next species.

## Finish: selective faceting (approved 2026-10-20)
- **Faceted / low-poly crystal treatment where the material calls for it:** frost, crystal, geological, prismatic, and selected Legendary/Mythic designs.
- **Not automatically on** soft mammals, plants, gels/slimes or fluffy creatures: they keep the soft matte C language.
- Each sheet's *materials* row states which regions are faceted.

The owner's Frostpup is **faceted low-poly** (frost qualifies); C1's Frostpup is **smooth ellipsoids**. Three ways to get the faceted look:

| Route | How | Quality | Cost |
|---|---|---|---|
| Wedge parts | Build facets from WedgeParts / CornerWedgeParts | Good for hard shapes (crystals, shells); fur facets get part-heavy | 40–80 parts: over the 18–30 budget |
| **Blender MeshPart** (recommended test) | Model a low-poly body in Blender, flat shading, one MeshPart per body region; face/eyes stay as parts so expressions keep working | Closest to R16 | 5–12 instances per creature; needs the approved "Blender for selected heroes" path widened |
| Hybrid | Smooth body + faceted crystal add-ons (mane, spikes) as wedges | Partial | Within budget |

**Next:** build **Frostpup from the R16 sheet as a faceted test** (Blender MeshPart vs wedges; Blender MCP is available when Blender runs). Compare it side by side with C1 Frostpup in Studio. The result decides the **method** for faceted species only; the method change (MeshPart for a non-hero) still needs the owner's OK at review.

## First sheets to make
The 7 representatives: Frostpup (R16 exists as the target; faceted), Mossbit (soft, plant: not faceted), Sparkbug, Slimelet (gel: not faceted), Pebbletoad, Magmawisp, Rockling (geological: faceted candidate). Then the remaining 29 in body-plan batches.
