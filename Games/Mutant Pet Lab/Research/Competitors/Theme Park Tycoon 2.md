---
type: research
game: "[[Mutant Pet Lab]]"
research_target: "Theme Park Tycoon 2"
researched_on: 2026-10-15
category: tycoon · build mode
status: complete
research_tags:
  - ui
evidence: low
tags:
  - research
  - competitor
---
# Theme Park Tycoon 2

> Legend: **OBS** = observed in a cited source · **INF** = my inference · **MPL** = recommendation for MUTANT PET LAB (not a decision). Community sentiment is labelled as such.

> [!warning] Low evidence
> No source described its build-mode controls in detail. I could not verify the developer this pass. The note relies on one platform announcement and genre comparisons.

## Why this game matters
- **INF:** A long-running Roblox *building* game. It is the main reference for how deep build tools can work on Roblox, which matters for MPL's approved drag-to-place [[Design Decisions#Touch build placement: drag → release → confirm|Build Mode]].

## First-session loop
- **INF:** An empty park plot → place a path → place a ride → guests arrive → money → more rides.

## UI observations
- **OBS:** The Xbox release came with a building system made specifically for controllers ([[Research Sources#Theme Park Tycoon 2|S35]]).
- **OBS (comparable mobile game):** RollerCoaster Tycoon Classic on mobile uses tap-to-place, then a separate build button to confirm ([[Research Sources#Theme Park Tycoon 2|S36]]).
- **INF:** Two-step place-then-confirm is the norm on touch. MPL's approved drag → release → PLACE matches it.

## Map/environment observations
- **INF:** The player builds the map. The environment is the *result* of play.

## Creature/pet observations
- Not applicable.

## Progression observations
- **INF:** Money unlocks more parts, so the toolset itself is the progression.

## Game-feel observations
- **INF:** Guests walking through what you built is the payoff.

## What works
- A **separate build scheme per input device** (controller-specific building).
- Confirm before committing on touch.

## What I would avoid
- **INF:** Deep free-form building with many tools, which overwhelms on phones.

## Lessons relevant to MUTANT PET LAB
- **MPL:** KEEP the approved drag → release → ROTATE/PLACE/CANCEL flow. Consider a controller-specific build path (D-pad nudge plus a snap grid) as a later item; MPL's Build Mode already supports ButtonB to cancel.
- **MPL:** Payoff: creatures should move into or use a new pen right after it is placed.

## Possible references to save
- None.

## Sources
- [[Research Sources#Theme Park Tycoon 2]]
