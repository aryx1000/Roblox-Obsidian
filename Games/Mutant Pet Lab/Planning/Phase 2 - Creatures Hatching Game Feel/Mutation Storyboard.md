---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: mutation
status: candidate
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - planning
  - phase-2
  - storyboard
---
# Mutation Storyboard

> [!info] CANDIDATE storyboard (2026-10-16) for checkpoint 2F
> Frame-level version of the approved [[Mutation Reveal Spec]] (decision: *Phase 2: the interaction stays at the Mutation Machine; the Reactor responds*). Discovery notices stay **OFF** (approved). Timings and sound slots are Candidates.

## Timelines (seconds from pressing MUTATE)

### Normal (result seen before) — card at ~3.0 s
| t | Where | Picture | Sound slot |
|---|---|---|---|
| 0.0 | panel | the two parent icons slide together; panel shrinks to the result card frame | `Click` |
| 0.2 | Machine | chamber lights green; client copies of both parents step onto the pads | — |
| 0.4–1.2 | Machine | parents dissolve into light (transparency + rising particles) | `MutationPulse` |
| 1.0–1.6 | Cable1 | a light pulse travels along the cable to the Reactor | — |
| 1.6–2.6 | Reactor | `Core` brightens, `CoreBlend` hue drifts | `ReactorCharge` |
| 2.6 | Machine pad | result appears as a silhouette, colour floods in (0.4 s) | — |
| 3.0 | panel | card: result + **"from A + B"** + trait/variant chips (reveal order Species → Rarity → Trait → Variant) | — |

### First discovery — card at ~5.0 s
Normal, plus: Reactor charge lengthens to 1.5 s with catwalk trims (`DaisTrim1/3`) flickering; a 0.3 s pause before the silhouette; **NEW SPECIES** stamp; `Discovery` jingle; the Index entry glows the next time it opens. Never auto-skipped.

### Secret (mutation-only Mythic) — card at ~7.5 s
First discovery, plus: the cable pulse is purple; all four `TankLiquid1–4` brighten; the `Crown` spins up (2 s); a crown flash and a **3 s sky tint** in the species colour (client ColorCorrection + Atmosphere tint), visible from every plot; `ReactorBeacon`. Only once per player per species. Notices: none (default OFF; hook prepared for secret tier only).

### Failed secret attempt (free)
Reactor **sputters**: core dims, crackle (`ReactorSputter`), crown flickers once (1 s). The card shows the hint as a "Lab note", not an error.

## Skip cleanup
Tap anywhere → card. Cancel tweens; stop sounds; destroy dissolve copies and particles; **restore every reactor and cable part to its exact saved properties** (Color, Material, Transparency, CFrame of the crown); restore ColorCorrection/Atmosphere. Never auto-skip a first discovery or a secret.

## Mobile
Same sequence; tap = skip; HUD hidden (MobileUX major); no shake; camera untouched (the reactor reacts in the world; the player sees it if it is on screen).

## Spawn transition
The result hops off the pad, follows the player for 3 s (cosmetic), then waits at the machine's holding spot until assigned. Inventory truth comes from the server's `state`.

## Several players at once
One full reactor sequence per client view; others shorten to a single pulse (queue, newest last).

## Related
[[Mutation Reveal Spec]] · [[Hatch Storyboard]] · [[Creature Visual Language Spec#Mutation inheritance table]] · [[PHASE2_IMPLEMENTATION_PLAN]]
