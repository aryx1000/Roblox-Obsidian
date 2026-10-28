---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: onboarding
status: candidate
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - planning
  - phase-2
  - onboarding
---
# Early Game Reorder (exact step moves)

> [!warning] FINALISED PROPOSAL — NOT IMPLEMENTED
> Implements the approved early-game pacing direction ([[Early Game Pacing Spec]]). **Not implemented** because it depends on the welcome egg (checkpoint 2E: schema v4, server grant), which isn't built yet. Changing only the order today would point new players at a Hatch step with no egg. Ships behind `FeatureFlags.Phase2.OnboardingV2`.

## Today (`OnboardingConfig.C.Order`, 18 steps)
ClaimProperty → InspectCreatures → BuildPen → AssignCreature → PlantCrop → HarvestCrop → FeedCreature → FavoriteFood → CollectSample → VisitResearch → UnlockResearch → Mutate → Discover → VisitEggShop → BuyEgg → Incubate → Hatch → Expand

## Proposed (same 18 step ids, no new ids, no save impact)
1. **ClaimProperty** — the server grants the welcome Field egg and starts it in a starter incubator (2E).
2. **BuildPen**
3. **AssignCreature**
4. **Hatch** ← moved from 17. Welcome egg timer ~90 s, so it is ready right after the first pen (target first hatch 1:30–2:00).
5. **Discover** ← moved from 13. Auto-completes with the welcome hatch (guaranteed undiscovered species); steps already complete out of order.
6. **InspectCreatures** ← moved from 2. View-only; now "meet your new creature".
7. PlantCrop · 8. HarvestCrop · 9. FeedCreature · 10. FavoriteFood · 11. CollectSample (unchanged loop)
12. **Mutate** ← moved from 12 to after the core loop but **before** Research (target 5–8 min).
13. **VisitResearch** ← moved from 10.
14. **UnlockResearch** ← moved from 11.
15. VisitEggShop · 16. BuyEgg · 17. **Incubate** (now the player's *second* egg) · 18. Expand

## Exact moves
| Step | Old position | New position |
|---|---|---|
| Hatch | 17 | 4 |
| Discover | 13 | 5 |
| InspectCreatures | 2 | 6 |
| Mutate | 12 | 12 (now precedes VisitResearch/UnlockResearch) |
| VisitResearch | 10 | 13 |
| UnlockResearch | 11 | 14 |
| Incubate | 16 | 17 |
| all others | — | relative order unchanged |

## Hint text changes (Candidate wording)
- **Hatch:** "Your welcome egg is almost ready — select the incubator and HATCH."
- **Discover:** "New species! Find it in the INDEX."
- **InspectCreatures:** "Open CREATURES to meet your new specimen."
- **AssignCreature:** "Assign **Sparkbug** to the pen" — keeps Slimelet + Rockling free for the first mutation (mutation needs unassigned parents).
- **Mutate:** unchanged example (Slimelet + Rockling → Magmawisp).
- **Incubate:** "Build a Basic Incubator for your new egg, then INCUBATE."
Rewards per step unchanged.

## Risks
- The welcome incubator: either a free starter incubator placed at claim (new server object, layout change) or the first incubator the player builds receives the egg. **Decision needed in 2E** (Candidate: free starter incubator, because it makes the first hatch possible at minute 1).
- Existing players: completed steps stay completed (ids unchanged).
- Economy: one extra Field egg at minute 0 → re-run `EconomySimulation` and `Finish2C_Economy_Test`.

## Related
[[Early Game Pacing Spec]] · [[Hatch Storyboard]] · [[PHASE2_IMPLEMENTATION_PLAN]]
