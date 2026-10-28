---
type: research
game: "[[Mutant Pet Lab]]"
research_target: "first 10 minutes"
researched_on: 2026-10-15
category: topic · onboarding
status: complete
tags:
  - research
  - onboarding
---
# Early Game Research

> [!success] Decision outcome
> Owner decision 2026-10-16: **pacing direction approved.** First hatch in the first few minutes, an early first discovery, first mutation ~5–8 min. **Welcome egg approved:** one-time, a guaranteed undiscovered species from the early pool, persisted, server-authoritative. Exact guide order is settled in Checkpoint F of [[PHASE2_IMPLEMENTATION_PLAN]].

> Authority: REFERENCE-level research. **Do not rewrite onboarding yet.** Builds on [[Gameplay Loop Research]]. Labels: OBS / INF / MPL.

## How strong games structure the first 10 minutes
| Moment | [[Pet Simulator 99]] | [[Grow a Garden]] | [[Adopt Me]] | [[Steal An Egg]] | [[Bee Swarm Simulator]] |
|---|---|---|---|---|---|
| First egg appears | Within the first minute; the starter egg is cheap. Guides disagree on free vs 90 coins (S48) | Pet eggs are a later purchase; *seeds* are the first "egg" (official desc.) | Starter egg at the start, dog or cat only (S12) | Immediately: you grab one (S2) | First bee/egg from the start (INF) |
| First hatch | Minutes (OBS: "hatch as soon as you can afford it") | Seed sprouts within seconds | After egg tasks, short (S41) | After carrying home; hatch time by rarity | Early |
| First creature choice | Which egg / which pets to equip (S48) | Which seed | Which egg to buy next | Which biome to raid | Which bee egg |
| First upgrade | A damage upgrade early; guides call it as important as hatching (S48) | Better seeds | Home items | Treadmill speed | Bag/tool |
| First rare/surprise | Rare hatch odds from the first egg | Mutation on a crop (weather) | Rare pet from an egg | Rarer egg in the next biome | Gifted bee chance on any egg (S49) |
| Long-term goal visible | The next zone gate (S48) | Rare seeds in the shared shop | Neon/legendary pets | Faster biomes | Mountain fields (official desc.) |
| Uniqueness understood | Pets break things for coins | Plant, grow, mutate | Raise a pet | Steal + hatch | Bees gather pollen |

**Shared rule (INF):** the *signature verb* of the game happens in the first minute, and its rare version is possible from that first minute.

## MPL today
Order: claim (1) → inspect (2) → build pen (3) → assign (4) → plant (5) → harvest (6) → feed (7) → favourite food (8) → collect sample (9) → visit Research (10) → research (11) → **mutate (12)** → discover (13) → visit Egg Shop (14) → buy egg (15) → incubate (16) → **hatch (17)** → expand (18).
- New profile: 3 starters, 150 Cash, **no egg**. A Field Egg costs 60 Cash and incubates in **22 s**, so hatching early is *already affordable*. Only the guide order puts it last.
- **MPL's signature verb is MUTATE** (it's in the name). It comes at step 12, after the full farm loop.

## Evaluation: should the order change?
**Yes, likely (recommendation; not to be implemented now).** Suggested order to discuss:
1. Claim the lab → **a Field Egg is already in a starter incubator** (0:00–0:30). The anticipation runs while you build.
2. Build a pen; the starters move in (1–2 min).
3. **Hatch** (~2 min). The first in-world reveal; the new creature walks to the pen.
4. Plant → harvest → feed → collect (2–6 min). Same as today; consider direct prompts.
5. **First mutation at the Reactor** (~6–8 min) with a guaranteed starter recipe (Slimelet + Rockling → Magmawisp, already the guide example). This is the *uniqueness* moment.
6. Research, then the Egg Shop, then expansion (8–15 min). The long-term goal is shown as the Index completion count + the locked annex.

| Moment | MPL today | Proposed (to discuss) |
|---|---|---|
| First egg | Step 15 (~after the farm + research loop) | 0:00 |
| First hatch | Step 17 | ~2 min |
| First creature choice | Step 4 (which to assign) | Same + which egg family to buy next |
| First upgrade | Expand at Level 5 (~11 min) | Same; maybe a cheap pen upgrade earlier |
| First rare/surprise | Variant chance on hatch (late) | Variant chance on the first hatch (~2 min) |
| Long-term goal visible | Index / Goals panel | Index count + locked annex/biome in the world |
| Uniqueness understood | Mutation at step 12 | ~6–8 min, at the Reactor |

**Constraint notes:** this touches [[Economy]] (a free starter egg) and `OnboardingConfig`, and needs the Studio save/test rules. **Owner decision required.**

## Sources
[[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)]]
