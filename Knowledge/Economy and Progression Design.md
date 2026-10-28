---
tags: [knowledge, game-design, economy]
sources: [Mutant Pet Lab, Shift From Hell]
---

# Economy and Progression Design

Back to [[Knowledge/Index|Knowledge]]. Details are in [[ECONOMY_2C]].

## Method
1. **Simulate before you tune.** Build a minute-step model from the *live config* (MPL `EconomySimulation`): income, spending priority, and milestones (first egg, stage N, level N).
2. **Fix only clearly unreasonable values.** MPL's assay payouts of 6/8/6 gave Level 25 in about 35 min; 3/4/1 gave about 158 min of optimal play. Real players are 2–3× slower.
3. **Lock it in with tests:** milestone bounds, a monotonic XP curve with non-shrinking gaps, and "one-time rewards can't reach max level alone".
4. **Unlock map:** something new at every level 1–10, and no stretch over 3 levels without an unlock.

## Sinks
- Ask whether each currency still has a *repeatable, meaningful* use after the level cap before adding anything.
- MPL post-25 answer: Cash goes to eggs for variant and trait hunting; Research goes to every mutation.
- Rebirth, prestige or grind sinks are a design decision for later, not a reflex.
- Record surpluses as constraints for future pricing (MPL: Research accrues about 1.7× faster than Cash).

## Onboarding and assignments
- **A guide of about 18 steps** that credits steps out of order (one feeding can complete "feed" and "favourite food"). It's server-authoritative, persisted and dismissible, with modest rewards.
- **Tiered assignments** (Early / Mid / Late) that are non-grindy, completed by events plus derived values (index count, research count).

## Scoring (SFH)
- Pressure ramps with time and player count.
- S–F rating with a tunable target. A near-perfect bot scores about 5,000 against a 3,000 target, so humans land around A–C.

Related: [[Monetization Principles]]
