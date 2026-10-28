---
type: research
game: "[[Mutant Pet Lab]]"
research_target: "Roblox market / UI / gameplay"
researched_on: 2026-10-15
category: hub · synthesis
status: complete
tags:
  - research
  - synthesis
---
# Roblox Market Research

Research pass from 2026-10-15: **research only**. No Studio or game-code changes.

> [!important] Authority
> Research sits **below** approved [[Design Decisions]], curated references and current project state ([[Claude Workflow#Authority order]]). It **never overrides an approved decision by itself**. New directions are listed under [[Design Decisions#Candidates to confirm (not approved decisions)]].

## Sample (14 games)
Selected for current relevance (live chart, 2026-10-15, [[Research Sources#Market charts|S1]]) plus genre fit. I stopped when the patterns started repeating.

| Game | Category | Why chosen | Evidence |
|---|---|---|---|
| [[Steal An Egg]] | Hit · pets · base | #1 live (~934K); MPL's exact nouns | medium |
| [[Steal a Brainrot]] | Hit · collection | Concurrency record holder; central conveyor + bases | high |
| [[Grow a Garden]] | Hit · farming | Farming + mutations loop; 21M+ peak | high |
| [[Adopt Me]] | Pet raising · social | #3 live; longest-lived pet game; growth + Neon | high |
| [[Pet Simulator 99]] | Simulator | Genre archetype; HUD and grind complaints | low |
| [[Bubble Gum Simulator Infinity]] | Simulator · hatching | 2025 hatching hit | low |
| [[Bee Swarm Simulator]] | Creature sim · quests · map | Fields with roles; quest NPCs; creatures as engine | medium |
| [[99 Nights in the Forest]] | Hit · co-op · atmosphere | Central landmark organises map and loop | medium |
| [[Fisch]] | Collection · skill · islands | Forgiving skill moment; visible next islands | medium |
| [[Ride A Pet]] | Pets · traversal | Creature stats felt in play; social stations | medium |
| [[Dragon Adventures]] | Creature breeding · worlds | Breeding, inheritance, themed worlds, map award | medium |
| [[Creatures of Sonaria]] | Creature growth | Creature design as identity; growth stages | low |
| [[Theme Park Tycoon 2]] | Tycoon · build mode | Deep building on Roblox; controller-specific | low |
| [[Sol's RNG]] (pass 2) | RNG · rarity reveal | Reference for reveal escalation and skip thresholds | medium |

Not included:
- **Brookhaven RP** and **Dress To Impress**: social/UI games, evidence not gathered.
- **Blox Fruits**: map, out of genre.

Topic notes:
- [[Simulator UI Research]]
- [[Gameplay Loop Research]]
- [[Creature Presentation Research]]
- [[Map and Environment Research]]
- [[Game Feel Research]]
- [[Anti-Patterns]]
- [[Research Sources]]

Browse: [[Roblox Research.base]]

> [!warning] Evidence limits
> - No first-hand play and no screenshots.
> - UI points are mostly inference.
> - Community sentiment was found for Steal a Brainrot, Grow a Garden, Adopt Me!, Pet Simulator 99 and DevForum UI threads. Several Reddit-style searches returned only SEO filler, which was excluded.

## TOP 10: UI
1. Show state **in the world** first (crops, eggs, creatures, pens), panels second.
2. One compact status cluster. No counter per system.
3. Nothing at the top edge or in thumb/joystick zones on mobile (S37).
4. One major panel at a time.
5. Icons that say what they do; icon + label for primary actions.
6. Shop as a place (an in-world counter or display), with the panel as detail.
7. Index grid: silhouettes for unknowns, rarity colour, completion count.
8. Place, then confirm, for touch building.
9. A separate input scheme per device (touch / mouse / controller).
10. Split big menus into focused tabs (avoids cognitive overload).

## TOP 10: Gameplay / retention
1. A physical action in the first 30 s.
2. A creature or payoff by about 2 minutes.
3. A visible next tier by about 5 minutes.
4. Surprise (rarity, mutation) by about 15 minutes.
5. Mutations that change both **look and value**.
6. Offline progress, with a "while you were away" moment.
7. Small, clear next goals (needs, quests) from characters.
8. Gates you can *see* before you can pass them.
9. Short timers early, longer later.
10. Fewer, richer updates that plug into the existing loop.

## TOP 10: Map / environment
1. A central landmark with a gameplay role.
2. Zones with one strong theme each.
3. Zones with a *function*.
4. See the next area before you can reach it.
5. Plots visible to each other.
6. Light as wayfinding.
7. Elevation and enclosure, not flat ground.
8. Social features as physical stations.
9. A showcase of rare things in a public place.
10. Avoid long lists of zones that read as menus.

## TOP 10: Creature presentation
1. Silhouette identity before colour.
2. Variants readable from far away (glow/particles).
3. Visible growth or prestige tiers.
4. Inheritance you can see in bred/mutated results.
5. The hatch as an in-world event.
6. A delivery walk from incubator to pen.
7. Creatures reacting to care.
8. Creature traits that matter in play.
9. A favourite creature following you.
10. Depth over breadth: 36 great species beat 200 bland ones.

## TOP 10: Things to avoid
See [[Anti-Patterns]].
1. Pay-to-win.
2. Paid timer skips.
3. Gambling-style paid hatching.
4. Loss-of-progress tension.
5. Unsafe trading.
6. Rushed thin updates.
7. Billions-scale grind walls.
8. Cluttered HUD.
9. Buttons in thumb zones.
10. Content that runs out in 40 minutes.

## MPL comparison: KEEP / IMPROVE / RETHINK
Compared with current plans and state ([[Roadmap]], [[Design Decisions]], `OnboardingConfig`). **Labels are recommendations, not decisions.**

| Area | Verdict | Reason |
|---|---|---|
| **HUD** (status cluster + 7-tile nav + Goals) | **KEEP** | Matches every UI best practice found (TOP 10 UI #2–4). |
| **Build Mode** (drag → release → ROTATE/PLACE/CANCEL, overhead camera) | **KEEP** | Matches touch norms (S36). IMPROVE later: controller nudge/snap (S35). |
| **Index** (tabs, cards, discovery banner) | **KEEP** | Matches the collection pattern. IMPROVE: per-family completion rewards (candidate). |
| **Egg Shop** (six families, campus counter) | **IMPROVE** | Show eggs physically at the counter; keep it soft-currency only. |
| **Mutation Lab** | **IMPROVE** | Make results show both parents visibly; link the reactor pulse to a completed mutation. |
| **Research** | **IMPROVE** | Each node should preview the *world* change it unlocks; consider a voiced NPC. |
| **Ranch** (pens, crops, feeding) | **IMPROVE** | Too many select → panel → button steps for the core loop; add direct in-world actions for the most common action. |
| **My Lab** (land, hatch reveal) | **KEEP** | Clear; the hatch reveal should become an in-world moment (see Hatching). |
| **Onboarding** (18 steps; first egg at steps 15–17; mutation before first hatch) | **RETHINK** | The genre's signature payoff (hatch) arrives last. Hits put it in the first 2 minutes. |
| **Map** (approved overhaul) | **KEEP** | Matches landmark/zone/elevation/light patterns. IMPROVE: give biomes a function later (candidate). |
| **Creatures** (colour + material only) | **RETHINK** | Silhouette identity and far-readable variants are the biggest gap versus creature games. |
| **Hatching** (panel reveal) | **IMPROVE** | Add an in-world crack-and-walk moment; keep the panel as a summary. |
| **Mutation** (secret recipes, variants) | **KEEP** | Already the strongest unique hook; Grow a Garden proves "mutation = look + value" works. IMPROVE visibility. |
| **Progression** (L5 ≈ 11 min … L25 ≈ 158 min; no post-25 sink) | **IMPROVE** | Healthy early pace. Needs a visible next goal in the world, and later a non-grind long-term goal (index completion, showcase). |

## Pass 2: hatching and simulator systems (2026-10-15)
New notes:
- [[Egg Hatching Research]]: answers A–G and the **recommended MPL hatch flow**.
- [[Mutation Reveal Research]]: how the Mutation Reactor could take part in reveals.
- [[Simulator Feature Research]]: 30 features judged on fit, fun, complexity, retention, generic risk, pay-to-win risk and grind risk, plus a world-vs-menu split.
- [[Early Game Research]]: first-10-minute comparison and a proposed order.
- [[Social Systems Research]]
- [[Rare and Secret Content Research]]

Visual references saved, with owner permission: [[Egg Design and Hatch Anticipation]] · [[Rarity Reveal Escalation]] · [[Creature Silhouette and Personality]] · [[Reward Burst and Wild Encounters]] · [[Bioluminescent Habitat and Visible Goals]].

**Headline findings:**
1. MPL's hatch is a panel popup, and the creature goes straight into the inventory. Every strong example puts anticipation and arrival **in the world**.
2. MPL's incubation (22–120 s) and its "top rarities only via mutation" rule are **already healthier** than the genre (no hour timers, no luck-only Mythics).
3. **First hatch at step 17 and first mutation at step 12** are the biggest early-game gaps. A Field egg is affordable from minute 0.
4. The **Mutation Reactor** can become the stage for mutation and secret reveals using visual-only hooks.

## Simulator feature priority matrix
Top 10 to consider **after** the current map / creature / game-feel work. Fit: HIGH/MEDIUM/LOW. Dev cost: LOW/MEDIUM/HIGH. **Nothing here is approved.**

| # | Feature | Fit with MPL | Player value | Dev cost | Risk | Recommendation |
|---|---|---|---|---|---|---|
| 1 | Hybrid in-world hatch (incubator crack → creature walks to pen → compact card; rarity-scaled; skip for owned species) | HIGH | High | MEDIUM | Low: must stay ≤ 5 s normal | **YES** |
| 2 | Reactor-staged mutation reveal (pads, charge-up, beacon on first discovery, fizzle + hint on failure) | HIGH | High | MEDIUM | Low: moving the interaction needs an approved move | **YES** |
| 3 | Onboarding reorder: starter egg incubating at claim, hatch by ~2 min, first mutation by ~8 min | HIGH | High | MEDIUM | Medium: touches economy + tests | **YES** |
| 4 | Creature idle-life and reactions (sleep, eat, bounce, look at player) | HIGH | High | MEDIUM | Low | **YES** |
| 5 | Direct in-world actions for harvest / collect (panels remain for choices) | HIGH | Medium | LOW | Low | **YES** |
| 6 | Visit-a-lab, read-only (pet creatures, one "Impressed"), Specimen Showcase of server rarities | HIGH | Medium | MEDIUM | Medium: griefing, must be non-interfering | **YES** |
| 7 | Rotating lab requests / contracts built on the existing assignment system | HIGH | Medium | LOW | Medium: grind if too many | **YES** |
| 8 | Per-family Index milestones → cosmetic lab decor | HIGH | Medium | LOW | Low | **YES** |
| 9 | Progressive secret hints + Index silhouettes + variant pity | HIGH | Medium | LOW | Low | **YES** |
| 10 | Valley weather / scheduled reactor surges biasing traits or variants | HIGH | High | HIGH | Medium: FOMO if time-limited | **MAYBE** |

Also assessed: lineage display (MAYBE), roaming wild specimens (MAYBE), expeditions via the dormant arch (MAYBE), bond meter (MAYBE). **NO:** rebirth, trading, gifting, daily-login chores, PvP, wealth leaderboards, paid multi-hatch, auto-hatch.

## Candidates added
See [[Design Decisions#Candidates to confirm (not approved decisions)]]. All are **unapproved**.

## Sources
[[Research Sources]]
