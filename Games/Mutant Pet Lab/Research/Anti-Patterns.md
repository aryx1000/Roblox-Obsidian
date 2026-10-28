---
type: research
game: "[[Mutant Pet Lab]]"
research_target: "anti-patterns"
researched_on: 2026-10-15
category: topic · anti-patterns
status: complete
tags:
  - research
  - anti-patterns
---
# Anti-Patterns

Patterns to avoid, each backed by an observed example. "Sentiment" means several independent sources agree.

| # | Anti-pattern | Observed example | Evidence | MPL risk today |
|---|---|---|---|---|
| 1 | **Pay-to-win competition** | [[Pet Simulator 99]] clan battles; [[Steal a Brainrot]] (Polygon: the best items cost cash) | Sentiment + press (S5, S13) | Low: no monetisation ([[Design Decisions#No monetization without explicit approval]]) |
| 2 | **Paid timers or lockout skips** | [[Steal a Brainrot]] Robux to shorten the lockout, called cruel (Kotaku) | Press (S7) | Watch: MPL has incubation timers; never sell skips without explicit approval |
| 3 | **Gambling-style paid hatching** | [[Bubble Gum Simulator Infinity]] paid Triple Hatch, luck potions | OBS (S14) | Low |
| 4 | **Loss of progress as the core tension** | [[Steal a Brainrot]], where one lapse wipes everything; viral clips of upset kids | Press (S5, S7) | None: cozy direction |
| 5 | **Unsafe trading economy** | [[Adopt Me]] trust-trade scams, real-money sales; safeguards added in 2020 | OBS (S12) | None: no trading. If added, safeguards first |
| 6 | **Thin, rushed updates** | [[Grow a Garden]] events called rushed; developer apologised | Sentiment (S11) | Plan fewer, richer updates |
| 7 | **Grind walls with huge numbers** | [[Bee Swarm Simulator]] billions-scale quests; [[Ride A Pet]] 125B rebirth; [[Pet Simulator 99]] | OBS (S13, S16, S28) | Watch: no post-Level-25 sink yet |
| 8 | **Button/counter-cluttered HUD** | DevForum simulator UI critiques | Sentiment (S37) | Low: approved minimal HUD |
| 9 | **Buttons in thumb/joystick zones or the top edge** | DevForum | Sentiment (S37) | Low: nav shifted to clear Jump; recheck after any HUD change |
| 10 | **Shallow content that runs out in minutes** | [[Steal a Brainrot]]: the reviewer had seen it all in about 40 minutes | Press (S7) | Medium: 36 species, but depth depends on how distinct they look and act |
| 11 | **Cheating via auto-collect scripts** | [[Steal a Brainrot]] (Game Rant) | Press (S5) | Server-authoritative validation already in place; keep it |
| 12 | **Low visual polish ("prototype look")** | [[Grow a Garden]] (Kotaku), [[Steal a Brainrot]] (ugly/boring) | Press (S7, S9) | Being addressed by Phase 1 + map overhaul. Note that these games *succeeded anyway*, so polish is not the main driver; the loop is |

## Pass 2: simulator features we should NOT copy
| Anti-pattern | Observed example | Evidence | MPL stance |
|---|---|---|---|
| Auto-play replacing gameplay | Auto-hatch (BGSI, S45); third-party auto-farm scripts for PS99 (S45 search) | OBS | No auto-hatch. Feeders are automation *inside* play |
| Constant purchase popups | Genre convention (not verified this pass) | INF | No monetisation without approval |
| 5+ currencies | Genre convention; BGSI shards/coins/gems (S15, S45) | OBS/INF | MPL has Cash + Research (+ XP). Keep it at 2 spendables |
| Endless egg spam | Paid Triple Hatch, auto-hatch (S14, S45) | OBS | One hatch = one moment |
| Hatch animations that get annoying | Repeated per-egg animations; skip requests (S47); "too fast" also bad (S38) | Sentiment | Rarity-scaled, skippable, short for owned species |
| Excessive wait timers | GaG 8-hour eggs, 1-hour mutation machine with a paid skip (S40, S43) | OBS | Keep 22–120 s incubation; never sell skips |
| AFK farming | Auto-hatch, AFK guides (S45) | OBS | Offline progress OK; AFK *optimal* play not |
| Shallow rebirth loops | Steal a Brainrot, Ride A Pet 7 rebirths up to 125B (S5, S28) | OBS | No rebirth |
| Fake scarcity | Limited-time secrets that leave the game (S45); admin-only events (S44) | OBS | Seasonal content returns |
| Paywalled rare creatures | Robux-only eggs (S14); GaG 49-Robux mutation skip (S43) | OBS | No |
| Pets as pure stat multipliers | PS99 damage multipliers (S48) | OBS | MPL creatures have diet, habitat, traits and care |
| Huge inventory clutter | Auto-delete had to be added (S45) | OBS | Inventory capacity + clear filters; a release flow if needed |
| Value-lowering random outcomes | Royal Jelly can downgrade a Legendary; GaG mutation replacement (S43, S49) | OBS | Mutations never lower value |
| Trading scams | Adopt Me! trust trades (S12) | OBS | No trading now |
| Daily chores that feel mandatory | Genre daily rewards / streaks | INF | No streaks; rotating requests are optional |

## Sources
[[Research Sources]]
