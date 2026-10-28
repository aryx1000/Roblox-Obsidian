---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: hatching
status: candidate
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - planning
  - phase-2
  - storyboard
---
# Hatch Storyboard

> [!info] CANDIDATE storyboard (2026-10-16) for checkpoint 2E
> Turns the approved [[Hatch Presentation Spec]] (decision: *Phase 2: hybrid in-world hatch*) into frame-level timelines. Timings, camera numbers and sound slot names are Candidates until built and reviewed. Server facts used: `Species`, `Rarity` (from SpeciesConfig), `Trait`, `Variant`, `NewDiscovery`, `PetId`. The client never decides anything.

## Tiers
- **Normal:** Common/Uncommon, no variant, already discovered.
- **Rare:** Rare/Epic, or any variant.
- **First discovery:** `NewDiscovery == true`.
- **Extreme:** the top egg case: first discovery **and** (Epic **or** a variant). Legendary/Mythic and secrets can't come from eggs (`MutationOnly`), so the strongest moment of the game stays in the [[Mutation Storyboard]].

## Timelines (seconds from pressing HATCH)

### Normal — card at 3.0 s, free at ≤ 5 s
| t | Picture | Camera | Sound slot | VFX |
|---|---|---|---|---|
| 0.0 | HUD + nav fade out (MobileUX "major"); lid lifts 0.5 stud | push FOV −10% over 0.4 s (only if the incubator is on screen) | `HatchCharge` | dome glow green |
| 0.6 | egg wobbles ±8°, twice | — | `HatchWobble` ×2 | — |
| 1.4 | cracks appear (green) | — | `HatchCrack` | crack decal / thin neon lines |
| 2.0 | shell bursts into 6 shards; flash | — | `HatchPop` | 1 PointLight 0.25 s, 6 debris parts ≤ 1.2 s |
| 2.2 | creature (display model) pops up on the pad, lands beside it, looks at the player | FOV back over 0.4 s | — | — |
| 3.0 | card slides up (species → rarity → trait chip) | — | — | — |
| ≤ 5 | player free; card stays until OK/Assign or auto-closes at 7 s | — | — | — |

### Rare — card at 4.5 s
Normal, plus: 3 wobbles; cracks in the **rarity colour**; a vertical neon beam 2.0–3.2 s; slow 8° orbit during the beam; 10 shards + 1 particle burst (≤ 40); the creature does a show-off spin at 3.4 s; card rim in rarity colour. Variant beat: see below.

### First discovery — card at 6.0 s
Rare, plus: a 0.3 s **pause** after the last wobble (2.2 s) while the world dims 15% (client ColorCorrection); the creature appears as a **black silhouette for 0.4 s**, then colour floods in; a 0.8 s camera focus on the creature (≤ 15° rotation), then back; `Discovery` jingle (1.5 s); the **NEW SPECIES** stamp slams onto the card at 6.0 s; "View in Index" is the highlighted button. Never auto-skipped.

### Extreme (egg maximum) — card at ~6.5 s
First discovery, plus: the beam is the variant colour; the ground ring pulse repeats twice; the variant sting plays on its own beat (6.0 s) before the card. Still no sky tint (reserved for secrets).

### Variant beat (any tier)
Last in the reveal order, after the trait chip: the variant effect switches on visibly on the creature (Luminous glow / Chromatic hue drift / Prismatic sparkle), variant sting (`VariantLuminous` / `VariantChromatic` / `VariantPrismatic`), variant chip in its colour. Adds ~0.8 s.

## Skip cleanup checklist
Tap / click / Space / ButtonA anywhere jumps to the card. On skip, in this order:
1. Cancel every running tween (lid, dome, camera, dimming, card).
2. Stop all sounds started by the sequence.
3. Destroy debris, beam, PointLight and particle emitter.
4. Restore the camera CFrame, FOV and CameraType saved at t = 0.
5. Restore ColorCorrection to its saved values.
6. Place the creature at its final landing spot (no half-way pose).
7. Show the card fully (no slide).
A first discovery or variant can be skipped by the player, but never **auto**-shortened.

## Mobile
Same timings. Joystick and Jump hidden for the whole sequence; tap anywhere = skip; card buttons ≥ 56 px; no screen shake, at most a 2 px UI pulse; camera rotation ≤ 15°.

## Spawn transition (creature into the world)
1. Lands beside the incubator, looks at the player (0.6 s), plays one trait idle (1 s).
2. **Assign** (card) → server assignment request; on success the display model walks to the pen gate (cosmetic path), the server proxy appears in the pen and the display layer takes over.
3. **OK** without a pen slot → waits at a holding spot next to the incubator with a "needs a pen" bubble.
4. Nothing moves server-side until the server confirms.

## Related
[[Hatch Presentation Spec]] · [[Mutation Storyboard]] · [[Creature Animation Spec]] · [[PHASE2_IMPLEMENTATION_PLAN]]
