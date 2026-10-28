---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: onboarding
status: approved-direction
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - planning
  - phase-2
  - onboarding
---
# Early Game Pacing Spec

> [!success] APPROVED DIRECTION (owner, 2026-10-16) — not implemented yet
> Binding decisions: the *Phase 2:* entries in [[Design Decisions]]. Where this spec and a decision differ, the decision wins. Implementation follows [[PHASE2_IMPLEMENTATION_PLAN]] after the owner reviews it.
> Touches `OnboardingConfig`, the profile defaults and possibly the economy simulation. Needs owner approval and a re-run of the economy tests.
>
> **Built on:** [[Early Game Research]], [[Gameplay Loop Research#MPL today]], [[Economy]].


## Facts (verified in `current/source`)
- **New profile:** 150 Cash, **100 Research**, 3 starters (Slimelet, Rockling, Sparkbug, all already discovered). No egg.
- **Field Research Egg:** 60 Cash (or 50 Research), 22 s incubation. Its table is Slimelet/Rockling/Sparkbug/Mossbit/Frostpup/Embercub.
  - **Half of the results are the starters,** so the first hatch is often *not* a discovery.
  - The `Welcome` acquisition is listed for the egg, but no code grants it.
- **First recipe** (guide example) Slimelet + Rockling → **Magmawisp (Epic)** costs **25 Research**. It's affordable at minute 0 and consumes 2 of the 3 starters.
- **Guide order today:**
  1. Claim → inspect → build pen → assign → plant → harvest → feed → favourite food → collect sample.
  2. Visit Research → unlock → **mutate (12)** → discover → Egg Shop → buy egg → incubate → **hatch (17)**.
  3. Expand at Level 5.
- **Simulated optimal pacing** (lower bounds): Level 5 ≈ 11 min, Stage 2 ≈ 20 min, Unstable Egg ≈ 40 min.

## Targets

| Moment | Today (guide order) | Target |
|---|---|---|
| First egg | step 15 | **0:00–0:30** (already in a starter incubator when the plot is claimed) |
| First hatch | step 17 | **~1:30–2:00** |
| First discovery | step 13 (via mutation) | **~2:00** (the first hatch is guaranteed to be an undiscovered species) |
| First creature choice | step 4 (assign) | ~1:00 (which starter goes in the first pen) |
| First mutation | step 12 | **~5–8 min**, at the Mutation Lab, with the Reactor reveal |
| First rare/surprise moment | late | first hatch has a normal variant chance; first mutation always gives an Epic (Magmawisp) |
| First upgrade | Level 5 expansion (~11 min) | unchanged; consider a cheap pen upgrade prompt at ~6 min |
| Long-term goal visible | Goals panel | ~3 min: Index completion count + locked annex sign + visible biomes |
| "What makes this game unique" | mutation at step 12 | first mutation ~5–8 min, staged at the Reactor |

## Proposed order (rewrite later; not now)
1. **Claim your lab.** A **Welcome Field Egg** is already incubating in a starter incubator on the plot (server grant; uses the existing `Welcome` acquisition).
2. **Build a pen** (Build Mode, the existing step). The starters move in, and you choose which one first.
3. **Hatch the welcome egg** (~2 min) → full first-discovery reveal ([[Hatch Presentation Spec]]).
   - The **welcome egg rolls only from Field-egg species you haven't discovered:** Mossbit / Frostpup / Embercub, with the normal weights renormalised. Server-side, one time.
4. **Plant → harvest → feed → favourite food → collect sample** (the core loop as today; direct in-world actions are a candidate).
5. **Visit the Mutation Lab** → mutate Slimelet + Rockling → **Magmawisp** with the Reactor reveal.
   - Optional: guide the player to keep one starter by suggesting a recipe that uses the hatched creature (e.g. Mossbit + Slimelet → Gloamgel).
6. **Research Terminal** (now at the Reactor front) → first program.
7. **Egg Shop** → buy and incubate a second egg (a choice between families as they unlock).
8. **Expand** at Level 5.

## Economy guardrails
- The welcome egg is a **one-time** grant. It doesn't change prices or rewards. Re-run `EconomySimulation` and the `Finish2C_Economy_Test` milestones afterwards.
- Level 25 must still need repeatable play (the existing test).
- No paid skips, no streaks, no timers longer than today's 22–120 s.
- Migration: existing players already past these steps are untouched. Only new profiles get the welcome egg (v1→v2-migrated profiles already received one).

## Risks
- Consuming 2 starters early leaves fewer creatures for pens. The guide should place the mutation **after** the first pen loop (as proposed), or suggest the hatched creature as a parent.
- A guaranteed discovery reduces surprise on the first hatch. Keep the variant roll normal, so a lucky Luminous still happens.
