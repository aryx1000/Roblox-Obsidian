---
type: specimen-sheet
game: "[[Mutant Pet Lab]]"
species: "[[Sparkbug]]"
body_plan: Flyer
rarity: Uncommon
habitat: Conductive
sheet_status: baseline-approved
production_status: "Baseline Approved"
body_family: Flyer
review_flag: "none"
updated: 2026-10-21
source: "Studio template ReplicatedStorage.MutantPetLab.Creatures.Species.Sparkbug (C1 + C2 refinements)"
tags:
  - mutant-pet-lab
  - specimen-sheet
---
# Sparkbug · Specimen Sheet

## Blender production spec (2026-10-22, before modelling)
Approved direction: [[Design Decisions#Production creature style: Frostpup + Mossbit Blender anchors approved]]. Surface: **insect = clean segmented planes** (crisper than the plant/gel, softer than rock).

| Field | Target |
|---|---|
| Silhouette | Cute bee-beetle first: **big round navy head** (≈ 45% of the body), short yellow thorax, **3-segment striped abdomen** tapering to a glowing charge cell, two pairs of **big rounded translucent wings** angled up and back, two antennae ending in **lightning-bolt tips**, 4 short stubby legs. Avoid realistic insect anatomy: no mandibles, no hairy legs, no compound-eye texture |
| Face | Big glossy cyan eyes (Roblox face parts), blush, small smile on the navy head |
| Mutant feature | Lightning antennae + the **charge cell** at the abdomen tip (cyan Neon spark inside) |
| Materials | Head + stripes navy (56,70,132); thorax/abdomen yellow (255,206,64); wings pale cyan Glass, T ≈ 0.3 (one mesh per side); bolts yellow; charge cell pale cyan + Neon spark (140,230,255) |
| Roles | Body: head, thorax, abdomen, stripes · Wing: one mesh per side (front + back wing together → one hinge per side, preserving the optimised flap path) · Accent: bolts, charge cell · Glow: spark · Leg: legs · Eye: face |
| Animation | Unchanged Flyer plan: hover 1.6, 14 Hz flap at 30° (medium LOD 30%/60%); the wing count drops from 6 parts to 2 meshes, so per-frame cost should fall |
| Luminous | Bolts + charge cell glow **electric cyan** (tint (90,220,255), mix 0.75); body stays matte yellow/navy |
| LOD | Medium: mouth + blush hidden. Far: silhouette (head, body, wings, antennae); legs, spark, eyes hidden |
| Budget | ≤ 650 tris, ≤ 12 meshes |


> [!success] Production status: **Baseline Approved** (C3, 2026-10-21)
> The seven body-plan baselines were approved for roster conversion after the C3 review ([[C3 Review 2026-10-21]]).

| Header | Value |
|---|---|
| Species · Body plan | **Sparkbug** · Flyer |
| Rarity · Habitat | Uncommon · Conductive |
| Descriptor | CHARGED INSECTOID. *A bright insectoid that crackles with harmless charge.* |
| Scale vs avatar | DisplayScale ×1.18 |
| Parts (close / medium / far) | 30 / 24 / 21 |
| Favourite food · Sample class | Gelberry · Electro |
| Review flag | none |

## Production checklist (C3 fields)
| Field | Value |
|---|---|
| **Production status** | Baseline Approved (Experimental → Baseline Approved → Final) |
| **Body family** | Flyer |
| **Silhouette test** | Pass: round head + segmented abdomen + wings + bolt antennae. |
| **Gameplay-distance test** | Pass: blue/yellow banding reads at 30 studs. |
| **Variant readability** | Luminous: bands + charge cell + bolts glow. |
| **Animation notes** | Hinged wing flap (slower at medium LOD); hover; ground marker stays on the ground. |
| **LOD notes** | Medium: slower smaller flap, no blinks. |
| **Estimated part/mesh cost** | 30 parts close. |
| **C3 changes** | No model change in C3. |

## Views
| Front | Side | Back | Silhouette |
|---|---|---|---|
| ![[sparkbug-front.jpg|220]] | ![[sparkbug-side.jpg|220]] | ![[sparkbug-back.jpg|220]] | ![[sparkbug-silhouette.jpg|220]] |

## Expression
Approved face language ([[Creature Face Language]]): neutral · happy (closed-eye) · curious (head tilt; Curious trait tilts toward the player) · sleepy · sad/tired (low wellbeing, **never angry**). Blink every 3–6 s near the camera.

## Materials
Glossy blue head/thorax, yellow segmented abdomen with blue bands, glass wings with veins. Not faceted.

## Mutant feature
Lightning-bolt antennae + glass charge cell at the abdomen tip.

## Glow / accent location
Charge cell only (small, soft cyan).

## Rarity differences
Uncommon: ground tint stays on the ground under the hovering body. Higher tiers: larger wings, a second bolt pair.

## Variant looks
Luminous: glow organs go Neon + pulse · Chromatic: accent hue drift · Prismatic: glass accents + sparkle. Stronger variant language is candidate C-V1 ([[Variant Visual Language]]).

## Mutation lineage / inheritance
Eggs: Field Research (15%), Conductive Coil (40%). Parent in: +Rockling → Tidegill · +Mossbit → Bloomtail · +Embercub → Fungloom · +Slimelet → Radisprout · +Circuitfin → Voltusk · +Frostpup → Circuitfin. **Inheritance cue:** bolt antennae / wing veins.

## Known issues / next pass
C2 perf pass: one batched move per step, hinged wing sides, slower flap at medium LOD: 34.8→20.3 µs/step (near), 33.8→18.2 µs (medium). Real wing meshes remain a later quality upgrade.
