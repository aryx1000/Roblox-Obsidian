---
type: planning
game: "[[Mutant Pet Lab]]"
area: buildings
status: candidate
updated: 2026-10-20
tags:
  - mutant-pet-lab
  - planning
  - buildings
  - eggs
---
# Egg Research Center Redesign

> [!info] CANDIDATE design (2026-10-20). Not built; Studio is untouched.
> **Built on:**
> - The owner's egg references: R4 tap-to-open, R5 proximity odds, R6 odds card, R8 chained locked eggs, R9 escalation, R10 trophy eggs ([[Owner Reference Library]]).
> - [[Building Art Direction]] and [[Physical Egg Interaction]].
>
> **Frozen:** the building's footprint position and the `OpenEggShopPrompt` interaction point. The 40-stud server range check for purchases stays.

## Today (snapshot `2026-10-16_creature_c1`)
- The same booth as four other buildings: a 36×28 floor, back wall, side wings, flat canopy, a 31×7 "EGG RESEARCH CENTER" sign, two light strips.
- A 14×4×3 counter with the prompt.
- **Six 3-stud glass/ForceField balls on 3-stud cube pedestals** with flat labels ("FIELD RESEARCH", "CRYOGENIC CAPSULE", …).
- **46 instances.**
- Problems:
  - From the plaza it reads as "a stall".
  - The eggs are too small to see from the path.
  - Locked vs unlocked isn't shown in the world.

## Target: "the hatchery greenhouse"
### Exterior silhouette
- A **round hall under an egg-shaped glass dome**: the roof itself is a giant translucent egg (tall oval, pale cream glass with a faint green → purple glow seam).
- It reads as "eggs" from **any plot path**, even without the sign. **This is the building's one signature shape.**
- A low **wooden ring wall** (cozy) carries the dome; **lab ribs** (pale panels, dark teal frame) run up the dome like a greenhouse.
- The entrance faces the plaza under a short **canopy shaped like a cracked eggshell top** (two jagged halves) over the counter.

### Physical egg displays (the main event)
- **Six family pedestals in a semicircle** inside the dome, ordered by tier left → right, at **eye height on stepped plinths**. Each egg is **6–8 studs tall**, not 3.
- **Unlocked egg:**
  - The family's look: [[Physical Egg Interaction#Egg family looks|family egg design]] (Field = speckled cream, Botanical = leafy shell, Thermal = lava cracks (R9), Cryogenic = frosted glass, Conductive = coiled copper bands, Unstable = violet shards in a containment cage).
  - A slow rotation on the plinth.
  - A **price plate** in Cash.
- **Locked egg:** the same egg in **dark matte**, wrapped in **chains with a padlock** (R8), a placard "🔒 Lv 6 · Thermal Research" and no glow.
- **Top tier (Unstable):** gets the trophy treatment (R10): a **containment cage + halo ring + small orbit rings** on an altar plinth. **Only the top tier**, so escalation stays meaningful.

### Counter + research equipment
- **Counter:** a curved wooden desk with a pale lab top, an incubator-lamp row and a clipboard screen.
  - The counter is still where the panel opens (the existing prompt).
  - The proximity cards (below) show odds without opening anything.
- **Behind the counter:** an **incubation research rig**: two heat-lamp incubators with test eggs pulsing, a candling lamp, a shelf of labelled egg cartons, a growth chart on the wall.

### Signage
- **Roof:** "EGG RESEARCH CENTER" + an egg pictogram on the dome base, outlined chunky lettering.
- **Floor at the entrance:** the painted word **"EGGS"** (R5/R6 pattern).
- **Per pedestal:** family name + tier stars + price / lock (SurfaceGui, ≥ 15 px at phone distance).

### Family / rarity display
- Rarity is shown by the **egg design tier** (plain → patterned → elemental → caged trophy), not by brightness.
- Each pedestal's **plinth trim** uses the family colour from the UI (consistent with the Egg Shop cards).

### Lighting
- **Daylight:** the dome glows softly from within (SurfaceLight on the dome base).
- **1 PointLight** above the Unstable altar; Neon only for the family trims and the dome seam.

### Where the hatch happens
- **At the player's own incubator on their plot** (approved hybrid hatch). The centre sells and displays eggs; it doesn't run hatches.
- ~~**Exception (Candidate):** welcome hatch at a "hatchery stage" in the centre~~ → **Rejected 2026-10-20:** the welcome hatch happens on the **player's own property** (starter incubator). The Egg Research Center **teaches and sells later eggs**.

### Approach + interaction
1. From the plot path, the dome is visible; from the plaza, the six eggs are visible through the glass.
2. Walking within ~10 studs of a pedestal **pops its odds card** (R5): contents as silhouettes / renders with %, and **BUY** (unlocked) or the lock reason (locked). See [[Physical Egg Interaction]].
3. **BUY** = the existing server purchase (`BuyShopEgg {FamilyId}`, Cash, range-checked). Nothing about authority changes.
4. The counter opens the full Egg Shop panel (Direction C) for comparing all families.

### From the plot paths
The dome's silhouette and its glow seam must read at 120+ studs: tall, rounded, the only egg-shaped roof on the map.

### UI tie-in
- The Egg Shop panel hero shows the **same egg models** (ViewportFrame of the pedestal egg).
- Locked families use the same chained look in the panel.
- The odds card shares the Direction-C card style (outlined title, rarity-framed tiles).

## Budget
| Layer | Count |
|---|---|
| Server shell (dome ribs, ring wall, counter, plinths, signs, prompt) | **≤ 46** (today's count) |
| Client detail layer (egg models, chains, rig, props) | ≤ 120 parts, culled beyond 120 studs |
| Lights | 1 PointLight + SurfaceLights |
| Option | If the owner allows MeshParts, the dome becomes 1 mesh (big saving) |

## Not to copy
- Robux egg shops, countdown "limited" eggs.
- The exact R8/R10 art.
- A generic white sci-fi hatchery.
- Conveyor-belt egg treadmills (Build a Zoo).

## Mobile
At 667×375, from the plaza, the dome + the six eggs must be distinguishable. Odds cards use ≥ 15 px text and fit beside the side rails.
