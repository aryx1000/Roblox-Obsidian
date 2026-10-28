---
type: specimen-sheet
game: "[[Mutant Pet Lab]]"
species: "[[Slimelet]]"
body_plan: Gel
rarity: Common
habitat: Standard
sheet_status: blender-anchor
production_status: "Blender Anchor (production model), pending the 7-anchor review"
body_family: Gel
review_flag: "none"
updated: 2026-10-22
source: "Studio template ReplicatedStorage.MutantPetLab.Creatures.Species.Slimelet (C1 + C2 refinements)"
tags:
  - mutant-pet-lab
  - specimen-sheet
---
# Slimelet · Specimen Sheet

## Blender production spec (2026-10-21, before modelling)
Approved direction: [[Design Decisions#Production creature style: Frostpup + Mossbit Blender anchors approved]]. Surface treatment for this family: **gel = soft rounded/faceted organic volume**.

| Field | Target |
|---|---|
| Silhouette | Not a ball: a **gel droplet dome** with a **curled droplet tip** on top (leaning back), a wide **puddle skirt** with 5 drip lobes, two short **gel feelers** ending in drops |
| Face | Big glossy eyes (Roblox face parts), blush, small smile; the face sits on the upper front of the dome |
| Mutant feature | A **glowing nucleus** inside the dome + 3 floating gel bubbles (one inside, two on the surface) |
| Materials | Body lime (150,236,150), **slightly translucent (one part, T ≈ 0.12)** so the nucleus shows; skirt/drips dark teal (34,138,118) for contrast on grass; pale belly low on the front (222,255,214); nucleus Neon lime-yellow. No Glass, no stacked transparency |
| Grass readability | The dark teal skirt + pale belly separate it from green floors; the dome stays lighter and warmer than the grass |
| Roles | Body: dome, belly, skirt · Crown: feelers (sway) · Accent: bubbles · Glow: nucleus · Eye: face |
| Luminous | Nucleus + bubbles glow **lime-yellow** (tint (190,255,70), mix 0.7); the skirt and dome stay matte. Enhances the gel identity, never white |
| LOD | Medium: mouth + blush hidden. Far: silhouette (dome, skirt, feelers); bubbles, nucleus and eyes hidden |
| Budget | ≤ 600 triangles, ≤ 10 meshes |


> [!success] Production status: **Baseline Approved** (C3, 2026-10-21)
> The seven body-plan baselines were approved for roster conversion after the C3 review ([[C3 Review 2026-10-21]]).

| Header | Value |
|---|---|
| Species · Body plan | **Slimelet** · Gel |
| Rarity · Habitat | Common · Standard |
| Descriptor | GEL ORGANISM. *A cheerful gel organism that jiggles when excited.* |
| Scale vs avatar | DisplayScale ×1.10 |
| Parts (close / medium / far) | 18 / 11 / 8 |
| Favourite food · Sample class | Gelberry · Organic |
| Review flag | none |

## Blender production model (2026-10-22)
![[slimelet-blender-34.png|420]] ![[slimelet-blender-front.png|300]]
![[slimelet-blender-side.png|300]] ![[slimelet-blender-back34.png|300]]
![[slimelet-blender-silhouette-side.png|260]] ![[slimelet-blender-silhouette-front.png|260]]

| Field | Result |
|---|---|
| Source | `MutantPetLab/blender/slimelet_style_anchor.blend` → `Slimelet_StyleAnchor.fbx` (imported 2026-10-22) |
| Meshes / triangles | **6 MeshParts, 516 tris**: Dome 176, Puddle (+ 4 drips) 180, Bubbles 60, FeelerL/R 40 each, Nucleus 20 |
| Face | The old Slimelet face set kept (Eye, Sheen, Glint, Mouth, Tongue, Blush), reseated onto the new dome, eyes +8% |
| Materials | Dome lime (128,228,108) SmoothPlastic **T 0.22 (the only transparent part)** so the nucleus shows through; puddle, drips and feelers dark teal (34,138,118); nucleus Neon (200,255,90); bubbles (205,255,205) |
| Iterations | v1 read as a cut gem (sharp peak, plinth base, a mustache-like belly band) → v2 softer volume but the dome floated over the puddle (drips looked like legs) → **v3** seated on the puddle, drips flow into it |
| In-game fit | Real pen + roaming pass; faces the player (face · look = 1.00); puddle mean height 1.52 on a 1.50 floor (the ±0.2 swing is the shared bob, as for every species); no clipping |
| 30 studs | Reads: lime gel blob on a dark teal puddle, distinct from the green pen floor and grass |
| Animation | Gel plan bob + feeler sway (Crown) + blink; cost **12.4 µs close · 7.6 medium · 4.1 far** per frame (best of 5), the cheapest anchor so far |
| LOD | Medium: mouth, tongue, blush, sheen hidden. Far: silhouette (dome, puddle, feelers); bubbles, nucleus, eyes, glints hidden |
| Luminous | First test: only the nucleus + bubbles glowed, which was too subtle. **Fix:** new generic `CreatureKit` opt-in `LuminousGlow=true` for non-Accent organs; Slimelet's **feelers glow lime-yellow** (tint (190,255,70), mix 0.7) with the nucleus + bubbles; the dome and puddle stay matte. Clearly different from Standard |
| Viewer / Index | Pass. The viewer rotates and zooms; the Index card + detail show the new model |

![[slimelet-blender-vs-parts-studio.jpg|420]] ![[slimelet-blender-lineup.jpg|420]]
![[slimelet-blender-luminous.jpg|420]] ![[slimelet-blender-pen-30studs.jpg|420]]
![[slimelet-blender-viewer.jpg|420]] ![[slimelet-blender-index.jpg|420]]

Old part-built model: **ARCHIVED / EXPERIMENTAL** in `ServerStorage.MPL_DesignReview.Archive.Slimelet_PartBuilt_C3`.

## History: part-built C3 production checklist (archived 2026-10-22)
| Field | Value |
|---|---|
| **Production status** | Baseline Approved (Experimental → Baseline Approved → Final) |
| **Body family** | Gel |
| **Silhouette test** | Pass: dome + puddle base + twin feelers; reads apart from Pebbletoad (no eye bumps) and Magmawisp (no hover). |
| **Gameplay-distance test** | Pass after C3: dark teal puddle rim + pale belly separate it on grass/pen floors; dark lab floor fine. |
| **Variant readability** | Luminous: drips + nucleus glow, eye glints, close sparkle. Weakest Luminous of the seven (few accent parts) but readable via nucleus. Chromatic/Prismatic: existing rules. |
| **Animation notes** | Gel bob/squash; feelers sway (Crown); no limbs. |
| **LOD notes** | Medium hides blush/sheen; far = body + skirt + eyes. |
| **Estimated part/mesh cost** | 20 parts close (belly added C3), ~12 medium. |
| **C3 changes** | C3 2026-10-21: lime body brightened, skirt + drips dark teal (opaque), new pale Belly part. Images: front + side recaptured; back/silhouette unchanged (silhouette did not change). |

## Views
| Front | Side | Back | Silhouette |
|---|---|---|---|
| ![[slimelet-front.jpg|220]] | ![[slimelet-side.jpg|220]] | ![[slimelet-back.jpg|220]] | ![[slimelet-silhouette.jpg|220]] |

## Expression
Approved face language ([[Creature Face Language]]): neutral · happy (closed-eye) · curious (head tilt; Curious trait tilts toward the player) · sleepy · sad/tired (low wellbeing, **never angry**). Blink every 3–6 s near the camera.

## Materials
Translucent glass-gel body (mint), matte inner nucleus, soft puddle base. **Not faceted** (gel: approved selective-faceting rule).

## Mutant feature
Glowing inner nucleus visible through the gel; drip feelers.

## Glow / accent location
Nucleus only (small Neon core). Body never glows.

## Rarity differences
Common: no ground marker. Higher-rarity gel relatives add drip crowns / multiple nuclei (anatomy, not brightness).

## Variant looks
Luminous: glow organs go Neon + pulse · Chromatic: accent hue drift · Prismatic: glass accents + sparkle. Stronger variant language is candidate C-V1 ([[Variant Visual Language]]).

## Mutation lineage / inheritance
Egg: Field Research (24%). Parent in: Slimelet+Sparkbug → Radisprout · +Mossbit → Gloamgel · +Magmawisp → Fluxaroo · +Frostpup → Glacierbit · +Rockling → Magmawisp. **Inheritance cue:** offspring take Slimelet's translucent gel finish or nucleus.

## Known issues / next pass
Green gel on green ranch floors is low-contrast at distance (seen in the C2 pen review): consider a slightly bluer mint or a darker base ring of the puddle.
