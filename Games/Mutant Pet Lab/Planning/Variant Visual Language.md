---
type: planning
game: "[[Mutant Pet Lab]]"
area: creatures
status: candidate
updated: 2026-10-20
tags:
  - mutant-pet-lab
  - planning
  - variants
---
# Variant Visual Language

> [!success] Radiant stays a trait (owner, 2026-10-20)
> The game's variants are **Standard, Luminous, Chromatic, Prismatic** (`TraitConfig.Variants`: 8% / 2.5% / 0.6%; sample ×1.12 / ×1.22 / ×1.45). **Radiant is a TRAIT, not a variant, and is not converted** ([[Design Decisions#Radiant stays a trait (owner, 2026-10-20)]]). This note covers the four variants; Radiant appears only as a trait icon/cue.

> [!info] Approved rule
> Variants must be **visible everywhere the creature is shown** (pens, hatch reveal, Index, creature detail, showcase, mutation result) **without constant heavy particles** ([[Design Decisions#Phase 2: rarity, variant and trait readability]]). Today's C1 look is subtle: Luminous = Glow parts go Neon; Chromatic = Accent hue drift; Prismatic = glass accents + sparkle near the camera. This note makes them **unmistakable without becoming recolours**.

## The four looks (4 channels each)
| Variant | Material | Secondary colours | Accent anatomy (added parts / swaps, ≤ 4 parts) | Restrained VFX |
|---|---|---|---|---|
| **Standard** | Species palette (matte / faceted) | Species palette | — | — |
| **Luminous** (8%) | Glow organs become Neon; **a soft inner-light gradient on the belly/face** | Species palette + a warm white-gold glow tint | **Glowing markings**: 2–3 thin Neon stripe/spot decals along the back (the species' own mark shapes) | Glow **pulses** every 3 s; **no particles** |
| **Chromatic** (2.5%) | Satin finish (slight reflectance) | **Two-tone shifted palette**: the species hue rotated (e.g. Frostpup blue → teal/violet split) | **Colour-split accents**: ears/tail tips/crest in the second tone; a **faint iridescent rim** on the head | Slow hue drift on the accents only (exists) |
| **Prismatic** (0.6%) | **Glass/crystal accents** (faceted: matches the approved selective faceted finish) (mane, spikes, wings, shell become clear crystal) | Pale base + rainbow refraction tint on the crystals | **Crystal growths**: a small prism crown or crystal shoulder cluster (species-shaped) | A sparkle emitter ≤ 6/s within 60 studs (exists) + an occasional **prism glint** sweep every ~8 s |

**Rule:** a variant changes **finish + a small anatomy accent**. It never swaps the silhouette and never makes the whole body Neon (approved glow rule).

## Per context
| Context | Standard | Luminous | Chromatic | Prismatic |
|---|---|---|---|---|
| **Pens** | — | Pulsing markings | Two-tone + hue drift | Crystal accents + sparkle (≤ 60 studs) |
| **Hatch reveal** | — | Variant beat: markings light up one by one + warm sting | Colours sweep across the body + shimmer sting | The crystals grow in + a bell sting + a single prism flash |
| **Index card** | Rarity frame | + **gold "L" variant chip** | + **teal "C" chip** | + **pink "P" chip**, card corner shimmer |
| **Creature detail / viewer** | — | A variant toggle shows the look | same | same |
| **Showcase** | — | Dome light tints warm | Dome light shifts slowly | The dome casts a rainbow floor caustic (1 SurfaceLight) |
| **Mutation result** | — | As the hatch reveal, at the machine pad | same | same |

## Variant chip colours (match the UI)
Luminous gold (as in `CreatureDetailController.VARIANT_COLOR`) · Chromatic teal · Prismatic pink.

## Budget
- ≤ 4 extra parts per variant (all in LOD 2, hidden far away, except the markings).
- 1 emitter only for Prismatic.
- No PointLights on creatures.

## Avoid
Same pet + simple recolour · whole-body Neon · excessive neon · constant particle clouds · weather-based variants (not approved) · turning Radiant into a variant.
