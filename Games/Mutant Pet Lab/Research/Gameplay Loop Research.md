---
type: research
game: "[[Mutant Pet Lab]]"
research_target: "first-session and retention loops"
researched_on: 2026-10-15
category: topic · gameplay loop
status: complete
tags:
  - research
  - gameplay
---
# Gameplay Loop Research

> Authority: REFERENCE-level research. It does not change [[Design Decisions]]. No dark patterns are recommended: no FOMO pricing, paid timers, loss-of-progress pressure or gambling-style hatching.

## The common shape of successful first sessions
| Time | What the hits give the player | Examples |
|---|---|---|
| **0–30 s** | One obvious physical action with an immediate result | Plant a seed ([[Grow a Garden]]); grab an egg ([[Steal An Egg]]); buy from the conveyor ([[Steal a Brainrot]]) |
| **~2 min** | The first *creature* or first payout, seen in the world | A hatched pet in your pen; a character walking to your base; your first harvest sold |
| **~5 min** | A choice and a visible next tier | Which seed or egg to save for; the next biome/island you can see but not enter ([[Fisch]], [[Bee Swarm Simulator]]) |
| **~15 min** | A surprise and a return reason | A mutation on a crop; a rare hatch; restock timing; offline growth |

These observations come from the sources behind each game note. The timings are **INF**.

## Rewards, choices, surprise, goals, anticipation, return
- **Rewards:** Physical and visible: eggs, creatures, crops. Not only numbers.
- **Choices:**
  - Save versus spend (Steal a Brainrot community write-up, S8).
  - Which biome to unlock next.
- **Surprise:** Mutations ([[Grow a Garden]]); rarity on hatch; trait inheritance ([[Dragon Adventures]]).
- **Goals:** Gates you can see; quest-giver NPCs ([[Bee Swarm Simulator]]); index completion.
- **Anticipation:** Incubation and growth timers, best when they are **short early** and longer later.
- **Return:** Offline growth ([[Grow a Garden]]); a shared restock (fair, but watch for FOMO); creatures that need care ([[Adopt Me]]).

## MPL today
From `OnboardingConfig` and [[Economy]]:
- **Step order:**
  1. Claim → inspect creatures → build pen → assign → plant → harvest (~18 s crop) → feed → favourite food → collect sample.
  2. Visit Research → unlock → **mutate** → discover.
  3. Visit Egg Shop → buy egg → incubate → **hatch** (steps 15–17 of 18) → expand at Level 5.
- **Pacing (simulated optimal):** Level 5 ≈ 11 min, Stage 2 ≈ 20 min, Unstable Egg ≈ 40 min.

**Strengths**
- Starter creatures from minute 0. Many hits make you earn your first creature, but MPL gives them free.
- Crops ripen in about 18 s.
- A clear guide with rewards at every step.

**Gaps against the market**
- **The first egg and first hatch arrive very late** (steps 15–17). Hatching is the genre's signature "wow". The hits put it in the first 2 minutes.
- **The first mutation comes before the first hatch.** That asks players to understand two creatures' recipes before they have had a hatch payoff.
- **Many panel steps.** Assign, plant, feed and collect are each a select → panel → button action. The hits use in-world interactions for the core loop.
- **No visible "next place" yet.** The planned biomes ([[Map Overhaul]]) could become that, but they are visual only today.

## Recommended for MPL (candidates only)
1. **Move one egg/hatch moment much earlier.** For example, a free starter egg already incubating on your plot when you claim it, hatching during the first build steps. Needs owner approval; touches [[Economy]]/onboarding.
2. **Fewer menu steps in the core loop.** Proximity prompts on pens and beds for the most common action (collect/harvest), with panels for details.
3. **A visible next goal in the world.** A locked biome or annex shown with a "Research needed" sign.
4. **Offline progress messaging.** On return, show "while you were away" for incubation and crops. Offline incubation already exists ([[Roadmap]], Finish 2A).

## Sources
[[Research Sources]]
