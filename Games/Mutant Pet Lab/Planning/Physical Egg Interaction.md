---
type: planning
game: "[[Mutant Pet Lab]]"
area: eggs
status: approved (Open ×3 + egg rack still candidate)
updated: 2026-10-20
tags:
  - mutant-pet-lab
  - planning
  - eggs
  - hatching
---
# Physical Egg Interaction

> [!success] Foundation built 2026-10-20 (C2)
> Egg family models; campus pedestals show real eggs (locked dark + chained), odds card with every species' %, prompt opens the Egg Lab on that family; incubator eggs wobble late and show **Crack!** when Ready (existing Hatch request, never automatic); rarity-scaled reveal with % chance. Not built: Open ×3, egg rack, welcome-egg persistence. [[C2 Review 2026-10-20]]


> [!success] APPROVED (owner, 2026-10-20)
> Physical egg displays, tap-to-crack, the odds popup, the **% chance display**, chained/dark locked eggs and rarity-scaled hatch presentation are **approved** ([[Design Decisions#Egg interaction (owner, 2026-10-20)]]). **Open ×3 is not approved: build the single-hatch experience first.** The egg rack stays a candidate.

> [!info] Scope
> Presentation design over the **existing server flow**: buy egg → owned eggs → incubate (22–120 s) → hatch. Server authority, prices, odds and timers are unchanged. **Monetization policy is unchanged:** no paid eggs, no paid multi-hatch, no luck/speed boosts. Approved hatch rules: [[Hatch Storyboard]], [[Design Decisions#Phase 2: hybrid in-world hatch presentation]].

## Eggs visible in the world
| Where | What the player sees |
|---|---|
| Egg Research Center | The six family eggs on pedestals ([[Egg Research Center Redesign]]) |
| Player plot, incubators | The incubating egg **inside the glass dome**, pulsing; the cracks grow over the last 25% of the timer |
| Player plot, owned eggs | *(Candidate)* An **egg rack** next to the first incubator showing owned, not-yet-incubated eggs, so owned eggs exist physically |
| Featured Specimen | Unchanged (creatures only) |

## Egg family looks
| Family | Look | Tier treatment |
|---|---|---|
| Field Research | Cream with green speckles | Plain |
| Botanical Culture | A shell wrapped in leaves, a sprout on top | Patterned |
| Thermal Core | Dark shell with **glowing lava cracks** (R9) | Elemental |
| Cryogenic Capsule | Frosted glass shell, ice crystals at the base | Elemental |
| Conductive Coil | Copper bands, tiny spark at the tip | Elemental |
| Unstable Mutagen | Violet shards inside a **containment cage + halo + orbit rings** (R10) | Trophy (top) |

## Locked eggs
- Dark matte version + chains + padlock (R8).
- A tap/approach shows **why**: "Level 6", "Needs Thermal Research".
- **No price is shown** until unlocked. Same treatment in the Egg Shop panel.

## Hover / approach / tap
| Input | Behaviour |
|---|---|
| Walk within ~10 studs (all devices) | **The odds card pops** above the egg (BillboardGui, Direction-C style) |
| Desktop hover over the egg | The card highlights; the cursor shows a hand |
| Tap / click the egg or its card | Focuses the card; shows **BUY** (or the lock reason) |
| Walk away | The card closes |

## Odds preview (the card)
- **Title:** family name + tier stars.
- **Grid of possible species:** discovered = 3D render, undiscovered = **dark silhouette + "???"** (R1/R5). **% on every tile** (from `EggFamilyConfig`).
- **Footer:** incubation time · price · **BUY** (one big button) · **"i"** for full info (opens the Egg Shop panel).
- **Owned count** of this family ("×2 owned").

## Welcome hatch (approved 2026-10-20)
The **first hatch happens on the player's own plot**, not at the Egg Research Center:
1. The welcome egg appears in / is delivered to the **starter incubator**.
2. The player interacts with it on their plot → **tap / crack**.
3. **First-discovery reveal.**
4. The creature appears near the incubator, **acknowledges the player**, and moves toward the starter pen / holding area.

The Egg Research Center teaches and sells **later** eggs.

## Single hatch flow (with tap-to-crack, R4)
1. **Shop → owned:** BUY (existing server purchase). The egg pops into a small "+1 egg" toast; if the egg rack exists, it appears there.
2. **Owned → incubator:** at the plot incubator, choose the egg (existing INCUBATE). The egg **drops into the dome** with a soft thump; the timer is shown on the incubator.
3. **Incubating:** the egg glows in its family colour; the cracks spread in the last 25%.
4. **Ready:**
   - The incubator lid lifts slightly and the egg **wobbles on its own**.
   - A **"Tap to crack!"** prompt appears (ProximityPrompt + an on-screen hint when near).
   - **If the player doesn't tap within ~2 s of arriving, it auto-cracks**, so the approved "never block play" rule holds.
5. **Tap:** sends the **existing HATCH request** (no new remote, no new authority). The tiered sequence plays (Normal / Rare / First discovery / Extreme).
6. **Reveal:** the creature lands beside the incubator → **stat card** (rarity word, name, trait chip, variant chip, one-line description, ASSIGN / VIEW IN INDEX / OK) (R9).
   - **Shows the % chance** (approved 2026-10-20) from `EggFamilyConfig`, as a percentage. This replaces the old "never show 1 in N" line of the hatch spec for the card.
7. **Into the world:** the approved "creature enters the world" behaviour.

## Multi-hatch policy
- **Today:** one hatch per incubator; several ready incubators play **one after another, short versions, rarest last** (approved).
- **R5 "Open ×3":**
  - In MPL terms, "×3" can only mean **three ready incubators hatched with one tap**. Each result is still its own server roll and its own card.
  - **Not approved (owner, 2026-10-20): Candidate.** Build and review the single hatch first.
  - **Never paid, never auto, no luck modifiers.**
- **Auto-hatch / auto-roll:** not approved ([[Do Not Copy]]).

## Transition summary
`Egg Research Center pedestal → odds card → BUY → (egg rack) → incubator → glow/cracks → Tap to crack → tiered reveal → stat card → creature walks to its pen`

## Budget
- Odds cards: one at a time per player.
- Egg models are client-side.
- Crack VFX within the approved hatch budget (≤ 10 shards, 1 PointLight, ≤ 40 particles, cleaned up in ≤ 1.5 s).
