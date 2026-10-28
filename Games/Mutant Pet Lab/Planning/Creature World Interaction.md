---
type: planning
game: "[[Mutant Pet Lab]]"
area: creatures
status: approved data contract; behaviours candidate
updated: 2026-10-20
tags:
  - mutant-pet-lab
  - planning
  - creatures
  - animation
---
# Creature World Interaction (care + life)

> [!success] Data contract built 2026-10-20 (C2)
> Server display attributes on creature proxies: `Wellbeing`, `Hungry`, `FavoriteFed`, `HabitatMatch`, `SampleReady`, `FedAt` (no `Resting`: the server has no rest state). Behaviours below are still the candidate spec. [[C2 Review 2026-10-20]]


> [!success] APPROVED (owner, 2026-10-20): read-only care state
> The server exposes the **minimum authoritative care state** as **read-only display data**; client visual systems may react to it. **Clients may NOT calculate, override or author care state.** [[Design Decisions#Care state exposed read-only to clients (owner, 2026-10-20)]] The behaviour list below is the candidate presentation spec.

> [!info] Presentation only
> - **The ranch simulation is unchanged:** feeding, wellbeing (Stable / Content / Thriving), samples, wander, containment and assignment stay authoritative on the server.
> - Everything here is client-side animation driven by **read-only facts the server already knows**.
> - Builds on: approved [[Creature Face Language]], [[Creature Animation Spec]], `CreatureAnimator` (2D slice), research candidates C-S1 / C-S2 / C-S5 ([[Similar Games Overview]]).

## Data the client needs (small, read-only)
Today the creature proxy carries `Species / Rarity / Trait / Variant`, incubators/feeders carry `Status`, and **pens and creatures carry no care state**. **Approved values** (owner list): wellbeing, hunger / feed state, favourite-food success, habitat satisfaction, sleep / rest, sample readiness where useful. Proposed **server-set, display-only attributes** (same pattern as 2A, which added Species/Rarity); names are a proposal:

| Attribute | On | Source | Used for |
|---|---|---|---|
| `Wellbeing` | creature proxy | existing wellbeing calc | happy / content / sad face + idle style |
| `LastMealAt` + `LastMealFavorite` | creature proxy | existing Feed / FavoriteFeed events | eat + favourite-food reactions |
| `SamplesReady` | pen model | existing sample counter | physical vials in the pen |
| `HabitatMatch` | creature proxy | existing preference check | habitat satisfaction reaction |
| `Resting` | creature proxy | server-decided rest state (only if the server tracks one; otherwise the client may *display* sleep from idle time, never author it as state) | sleep / rest pose |

There are no client inputs and no new remotes. **Clients only read; they never compute or write these values.** **Save format: unchanged.**

## Behaviours
| Behaviour | Trigger (server fact) | Presentation | Frequency / budget |
|---|---|---|---|
| **Eating** | `LastMealAt` changes | Walks (cosmetically) to the pen's feeder side, 3 head-dips with a chomp squash; crumbs (≤ 6 particles) | On each meal |
| **Favourite-food reaction** | `LastMealFavorite = true` | After eating: **happy closed-eye face + a hop + 3 small heart sparkles**, then the "×2 samples" floating text | On each favourite meal |
| **Sleeping** | `Resting` (if exposed); otherwise a cosmetic nap when idle > ~40 s and Wellbeing ≥ Content (display only, not care state) | Lies down / curls (per body plan), sleepy face, slow breathing bob, a small "z" every few seconds; wakes when the player comes within 6 studs | ≤ 1 in 3 creatures asleep at once |
| **Reacting to the player** | Player within look range (exists) | Look-at (exists); **Curious tilt** (exists); within 5 studs: a short greet (hop / tail wag / leaf wave) once per approach | Once per approach |
| **Habitat reaction** | `HabitatMatch` | Match: an occasional contented stretch. Mismatch: slight shiver / droop, sad-tired face at times (unless Adaptive / Insulated) | Every ~20–40 s |
| **Low wellbeing (Stable)** | `Wellbeing = Stable` | **Sad/tired face (never angry)**, slower bob, sits more often | Persistent while Stable |
| **Content** | `Wellbeing = Content` | Neutral face, normal idles | — |
| **Happy (Thriving)** | `Wellbeing = Thriving` | Occasional happy closed-eye bounce, livelier idles, a rare tiny sparkle | ≤ 1 bounce / 30 s |
| **Social** | Two creatures within 4 studs in the same pen | Turn to face each other, a mirrored hop or nuzzle (2 s), then resume | ≤ 1 pair at a time per pen |
| **Samples appear physically** | `SamplesReady > 0` | A **glowing bio-assay vial** pops beside the creature (bounce-in), up to 3 per pen; COLLECT (existing action) makes them fly to the HUD | Max 3 vial props per pen |
| **Curiosity / investigation** | A structure placed / changed within 10 studs | Walks to the nearest pen edge facing it, sniffs / tilts, returns | Once per change |
| **Rare idles** (one per body plan) | Random, ~1 per 2–4 min per creature, only within 40 studs | Gel: splits into two blobs and re-merges · Critter: chases its tail · Hopper: a huge hop with a mid-air spin · Flyer: a loop-the-loop · Sprout: stretches leaves to the sun · Wisp: its flame flares + the orbit stones speed up · Shellback: hides in its shell, peeks out | ≤ 2 rare idles playing at once per client |

## Rules
- The server position (wander) stays authoritative. Cosmetic moves (walk to feeder, face each other) **stay within the approved ±0.6 stud offset** or play *at* the server position (head-dips, curls).
- Uses the existing LOD tiers: full behaviours ≤ 40 studs, expressions + simple idles ≤ 90, nothing beyond.
- Trait flavour (exists): Calm sleeps more · Vigorous bigger hops · Curious investigates more · Forager reacts more to food · **Radiant** (a trait, not a variant) may get a subtle research-prestige cue, never a variant look.
- **Welcome hatch** (approved): the first creature appears near the starter incubator on the player's plot, acknowledges the player, then moves toward the starter pen / holding area.

## Tests (when built)
- Each behaviour fires only from its server fact.
- Removing the attributes = today's behaviour (flag `CreatureLife`).
- Perf with 48 creatures: animator ≤ 0.8 ms / frame (current Sparkbug-class worst case).
