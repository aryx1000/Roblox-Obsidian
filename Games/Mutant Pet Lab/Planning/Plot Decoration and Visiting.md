---
type: planning
game: "[[Mutant Pet Lab]]"
area: social
status: candidate
updated: 2026-10-20
tags:
  - mutant-pet-lab
  - planning
  - social
  - plots
---
# Plot Decoration and Visiting

> [!success] Decorations APPROVED as a future direction (owner, 2026-10-20)
> Buildable decoration categories: **paths, lamps, planters, signs, benches, lab props, habitat decorations.** **Not in the next immediate checkpoint.** **Functional structures and decorative structures stay conceptually separate.** [[Design Decisions#Decorations: future design direction (owner, 2026-10-20)]]

> [!info] Visiting presentation: CANDIDATE
> MPL's weakest dimension in the [[Similarity Matrix]] is Social visiting (1/3). **No trading, no gifting, no PvP, no stealing.** Likes / favourites are **candidate only**.

## What exists already (verified)
- All 8 plots share one server, so players can already **walk onto other plots**.
- Visitors **can't** sell, assign, feed, collect, plant, incubate or hatch (`visitors cannot … ` test).
- **Read-only visiting already works; it just isn't presented.**
- The Featured Specimen pedestal (expansion stage 2+) shows one creature.
- Plot gate today: two pillars + lights + "AVAILABLE RESEARCH PROPERTY".

## Visitor experience (target)
1. **Arrive:** walking through another player's **arch gate** ([[Building Art Direction#Player plot entry / gate language]]) shows a small banner: "**Ayrx's Lab · Level 12 · 18/36 discovered**".
2. **Look:** their pens with living creatures ([[Creature World Interaction]]), their Featured Specimen under its dome, their decorations.
3. **Inspect:** tapping a creature opens a **read-only [[Creature Viewer]]** (species, rarity, variant; no actions).
4. **React (candidate):** a single **"❤ Like this lab"** button on the gate banner, once per lab per day. Likes are shown as a count on the owner's gate.
5. **Leave:** HOME (exists) or walk out.

**Travelling to a plot (candidate):** a "Visit" option on a player card in the player list (teleport to that plot's gate), so far-away plots are reachable on phones.

## Showcase value
- **Featured Specimen:** move it to a **display dome by the gate** so visitors see it first. Show its variant clearly ([[Variant Visual Language]]).
- **Discovery plaque (candidate):** a gate-side plaque showing the owner's Index completion and their rarest discovery's silhouette.
- **Species statues (candidate):** a decoration unlocked per *discovered* species: a small statue on a plinth. It turns the Index into plot decoration and rewards discovery without adding power.

## Plot personality: decoration categories (direction approved; not scheduled)
Owner categories: paths · lamps · planters · signs · benches · lab props · habitat decorations. Claude's earlier grouping below maps onto them (Fences/gates and Trophies are Claude additions, still candidate).
| Category | Examples | Unlock |
|---|---|---|
| Paths & floors | Stone path, wooden boardwalk, glowing lab tiles | Cash, level |
| Fences & gates | Picket, hedge, glass-panel lab fence, arch colour | Cash, expansion stage |
| Lights | Bio lantern (exists), mushroom lamps, string lights | Cash, research |
| Plants | Planters, glowing ferns, crystal shrubs (matching the plot's biome) | Cash, crops grown |
| Lab props | Specimen jars, tanks, signposts, a telescope | Research nodes |
| Habitat props | Puddles, rocks, ice blocks, logs (inside pens; also cosmetic habitat dressing) | Habitat unlocks |
| Trophies | Species statues, egg trophies (first hatch of each family) | Discovery milestones |

Decorations use the **existing build placement system** (drag → release → confirm; grid sizes C-R2), but as a **separate decoration category** from functional structures (pens, feeders, crop beds, incubators, lanterns): own build-menu tab, no gameplay stats, no effect on care/economy. Storage is a **save-format consideration** (validator update + tests needed). **Not in the next checkpoint.**

Decoration art follows the approved negative rules: no recolour-only kits, no excessive neon, no copied Roblox-game identity ([[Do Not Copy]]).

## Expansion visuals
Each expansion stage adds **visible land features**, not just more space:
- Stage 1: a lab annex.
- Stage 2: the showcase dome.
- Stage 3: a greenhouse wing.
- Stage 4: an observatory deck.

"STAGE n" signs become small posts; the gate crest gains a star per stage.

## Social comparison without PvP
- **Lab card** (gate banner): level, discoveries, featured creature, likes (candidate). No rankings by default.
- **Optional server board (candidate):** "Labs to visit": the 3 most-liked labs in this server, refreshed per session. **No global leaderboards, no stealing, no competitive loss.**

## Not approved / never
Trading · gifting · stealing · raids · paid decorations (no monetization) · visitor actions on someone else's creatures.
