---
type: planning
game: "[[Mutant Pet Lab]]"
area: roadmap
status: active
updated: 2026-10-20
tags:
  - mutant-pet-lab
  - planning
  - brief
---
# Next Build Brief (for when Studio is available)

> [!success] Progress 2026-10-20 (C2)
> Done: step 1 (verify + clean + save), step 2 (Direction-C migration), step 3 refinements + review captures, step 4 (flyer perf), step 5 + 5b (physical egg foundation, read-only care state). See [[C2 Review 2026-10-20]]. **Next: owner review → Frostpup faceted test (3b) → Egg Research Center art pass (6) → 29 species in batches (7).**

> [!success] Owner decisions 2026-10-20
> Approved: template sheets required · selective faceted finish · building route B · physical eggs + tap-to-crack + odds popup + % chance + chained locked eggs + rarity-scaled hatch · read-only care state · welcome hatch on the player's own plot · Radiant stays a trait · decorations as a future direction · negative visual rules ([[Do Not Copy]]). **Still candidate:** Open ×3, egg rack, visiting/likes. [[Design Decisions]]

> [!important] Read first
> [[Current State]] · [[Design Decisions]] · [[MPL Visual Fingerprint]] · [[Do Not Copy]] · [[C1 Review Stage 2026-10-16]].
>
> **Always:**
> - Verify PlaceId 86236241957181 / Group 9350216 / AYRX before any change.
> - Studio stays on Mock; HTTP off; ≤ 3 Studio processes.
> - **Never publish** without explicit approval.
> - After every checkpoint: Save to Roblox → snapshot → vault → git.

## Must not change (any step)
- Persistence, the production DataStore config and the schema (v3).
- Economy numbers, mutation recipes, egg odds.
- Server ownership / authority, the ranch simulation.
- Map geometry positions (plot origins/bounds, station interaction points).
- Build Mode behaviour; monetization (none).

## Steps in priority order
| # | Step | Approved? | Depends on | Needs owner review | Notes |
|---|---|---|---|---|---|
| 1 | **Save / verify the C1 state** | Approved | Studio open | — | Check the script count/checksum = snapshot `2026-10-16_creature_c1` (195 / 983670883). **Remove `MPL_PREVIEW_Stage` and any `MPL_PREVIEW_*`** left by the interrupted 2026-10-16 portrait task. Restore StarterGui enabled states. Save to Roblox; snapshot |
| 2 | **Finish the Direction-C UI migration** (Egg Shop, Mutation Lab, Creatures, Ranch, Research, My Lab; plus Upgrades/Supply/Guide styling) | **Approved** (Direction C) | 1 | Yes: a review after migration | Each screen keeps its own composition (no recoloured clones). Fix the leftover phone sizes (badge digits/bar labels ≥ 15 px) |
| 3 | **Finalize the 7-creature review** | Approved direction; looks in review | 1 | **Yes** (the gate before more species) | **Write a specimen sheet for each of the 7 first** (approved requirement); until a sheet is approved the C1 model stays **Experimental**. Make the R16 Frostpup sheet the target; ring subtlety; DisplayScale values |
| 3b | **Faceted test** (frost/crystal/geological species only) | Finish **approved as selective**; method in test | 3; Blender running | **Yes** (method) | Frostpup from R16 as a Blender flat-shaded MeshPart (+ part face) vs wedges; side by side. Decides the **method** for faceted species. Soft mammals, plants, gels and fluffy creatures are **not** faceted |
| 4 | **Optimise flyer animation** | Approved (perf budget) | 1 | — | Sparkbug-class ~35 µs/step: lower the wing-flap rate at mid distance, merge wing+vein updates; target the 24-animated worst case ≤ 0.5 ms |
| 5 | **Physical egg / single-hatch implementation prep** | **Approved** (physical eggs, tap-to-crack, odds popup, % chance, chained locked eggs, rarity-scaled hatch). Open ×3 and egg rack: candidate | 2, 3 | Review after build | Read [[Physical Egg Interaction]]. **Single hatch only.** Prep = egg family models (client-side) + incubator crack states; the tiered hatch itself is 2E |
| 5b | **Read-only care state attributes** | **Approved** | 1 | Review of the attribute list | Server sets display-only attributes ([[Creature World Interaction]]); clients only read. Re-run the ranch/persistence tests; save format unchanged |
| 6 | **Egg Research Center art pass** | Design candidate; **budget route B approved** | 5 | **Yes** | [[Egg Research Center Redesign]]: egg-dome roof, 6 pedestals, chained locked eggs, odds cards. Shell server-side, detail client-local; no cap increase |
| 7 | **Remaining 29 species in controlled batches** | Approved direction (C); selective faceting approved | 3, 3b, **an approved [[Creature Template Sheets]] sheet per species** (required) | Yes: a review after each body-plan batch | Sheet → build → silhouette check → review stage → next batch. Order: Gel → Critter → Hopper → Flyer → Sprout → Wisp → Shellback → Chimerax |
| 8 | **Hatch / mutation presentation** (2E / 2F) | Approved direction; storyboards candidate | 5, 7 (templates for reveals) | Yes: timing review | **Welcome hatch on the player's own plot** (starter incubator → tap/crack → first-discovery reveal → creature acknowledges player → walks to starter pen). Welcome egg = **schema v4** (forward-only; publish must shut down old servers: owner approval). Reactor reveal per [[Mutation Storyboard]] |
| 9 | **Onboarding reorder** (2G) | Direction approved; exact moves candidate | 8 (welcome egg) | Yes | [[Early Game Reorder]] |
| 10 | **Broader game-feel / audio pass** (2H) | Approved process (sound review gate) | 2, 5b, 8 | **Yes: every sound pick** | [[Creature World Interaction]] behaviours; [[Variant Visual Language]]; [[Creature Viewer]] (candidates). **Decorations are NOT in this or the next checkpoint** (approved as a future direction only) |

## Open owner decisions (blocking specific steps)
| Decision | Blocks |
|---|---|
| MeshPart method for faceted non-hero species (after the 3b test) | 7 |
| Open ×3 / multi-hatch (after the single hatch ships) | — |
| Egg rack for owned eggs | 5 (optional part) |
| Each specimen sheet | 3, 7 |
| R14 trail shop: what you liked (kept needs-review; not inferred) | — |

## Still candidate (don't build without approval)
Remaining candidates in [[Design Decisions#Candidates to confirm (not approved decisions)]]: C-R1 family completion rewards, C-R2 grid sizes + undo, C-R4 Open ×3, C-R5 hex research board, C-R8 egg designs, C-R9/C-U1 viewer, C-S1…C-S9 (care reactions, physical samples, visiting/likes, stronger variants, follow-me pet, ambient sounds…), C-B2 building designs, C-V1 variant looks, C-P1 visiting.
