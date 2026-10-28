---
type: research
game: "[[Mutant Pet Lab]]"
research_target: "Steal An Egg"
researched_on: 2026-10-15
category: hit · pet collection · base
status: complete
research_tags:
  - loop
  - creature
  - map
  - anti-pattern
evidence: medium
tags:
  - research
  - competitor
---
# Steal An Egg

> Legend: **OBS** = observed in a cited source · **INF** = my inference · **MPL** = recommendation for MUTANT PET LAB (not a decision). Community sentiment is labelled as such.

## Why this game matters
- **OBS:** #1 on the livecounts.nl Roblox chart on 2026-10-15, about 934K concurrent players, roughly 3× the #2 game ([[Research Sources#Market charts|S1]]).
- **INF:** It is the closest commercial match to MPL's nouns (eggs → pets in your pen → passive income → upgrade base). It shows what the market rewards *right now* in our exact genre.

## First-session loop
- **OBS:** Train speed on a treadmill → run into a biome → grab an egg (press E) → carry it home while others can hit you and take it → place it in your pen → wait for it to hatch → hatched pets produce money every second ([[Research Sources#Steal An Egg|S2, S3]]).
- **OBS:** Every biome has a minimum speed to enter. Spawns reset every 5 minutes and the map closes for 13 s between rounds ([[Research Sources#Steal An Egg|S2]]).
- **INF:** The first 30 s already has a goal (grab an egg), a risk (getting robbed) and a physical reward (an egg in your arms). The first hatch arrives within minutes.

## UI observations
- **INF (not verified on screen this pass):** As in its genre, the HUD is minimal. Most information lives in the world: biome gates, egg models, pens. No source analyses the UI directly.

## Map/environment observations
- **OBS:** Several biomes, each gated by a speed stat ([[Research Sources#Steal An Egg|S2, S4]]).
- **INF:** Biomes act as a visible progression ladder. You can *see* the next biome before you can enter it.

## Creature/pet observations
- **OBS:** Eggs are physical objects you carry. Hatch times vary by rarity, and some rare eggs take hours ([[Research Sources#Steal An Egg|S2]]).
- **OBS:** Guides count about 114 pets, but sources disagree ([[Research Sources#Steal An Egg|S4]]).

## Progression observations
- **OBS:** Money → treadmill/base upgrades → speed → better biome → rarer egg ([[Research Sources#Steal An Egg|S2]]).
- **INF:** One stat (speed) gates everything. That is easy to understand, but shallow.

## Game-feel observations
- **INF:** Carrying the egg home under threat is the tension moment, and the hatch is the payoff. The 5-minute reset adds a short "event" rhythm.

## What works
- An egg is a **physical object in the world**, not a menu line.
- Gates you can see make the next goal obvious.
- The first reward arrives very early.

## What I would avoid
- Stealing from other players is the main hook, which conflicts with MPL's cozy direction ([[Design Decisions#Overall direction: cozy bio-lab ranch with a mutant-lab identity]]).
- Hours-long rare hatch timers. **INF:** In this genre they usually pair with paid skips (see [[Anti-Patterns]]).

## Lessons relevant to MUTANT PET LAB
- **MPL:** Make the first egg *physical* and early. Today MPL's first gameplay egg is onboarding step 15 of 18 ([[Gameplay Loop Research#MPL today]]).
- **MPL:** Use the existing biome-per-gap plan as a *visible* "next place" ladder, but gate it with research, not speed.

## Possible references to save
- Saved: [[Egg Design and Hatch Anticipation]] (egg designs, themed nest).

## Sources
- [[Research Sources#Steal An Egg]]
