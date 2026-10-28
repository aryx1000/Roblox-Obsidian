---
tags: [roblox, game, shift-from-hell]
owner: AYRX Entertainment (group 9350216)
production-universe: 10769997091
status: live (same-universe); v0.15.0 awaiting publish approval
---

# Shift From Hell

Back to [[Home]]. Reusable lessons are in [[Knowledge/Index|Knowledge]].

**SHIFT FROM HELL!** is a co-op (1–6 players) night-shift chaos game set in **HELLO MART** (the "O" flickers). Survive until 6 AM: check out customers, restock, mop spills, cook hot dogs, and handle disasters (power outages, runaway carts, fires, the Customer From Hell). Crews form in a social lobby by standing on matchmaking pads.

## Identity
- **Production experience "Shift From HELL!":** universe **10769997091** (Public).
  - Start place (Lobby) **102226397485981**.
  - Gameplay place **97843982576247**; one reserved server per crew.
- **Legacy "The Shift"** (universe 10769940157, place 134650094572002) was made **Private** on 2026-10-09, after the cutover was verified.
- **Source of truth:** `~/Claude's Personal Workspace/ShiftFromHell/`, a local git repo synced into Studio by `tools/sync.lua`. The active branch is `migration/same-universe`.
- **UI design:** Figma file `HM7OMtadi62rLUdwmg7jfk` (15 screens plus a design system).

## Status (from the repo's [[MASTER_RELEASE_CHECKLIST]], last updated 2026-10-09)
- **Cutover:** live on Lobby v13 and later; every crew is routed to gameplay place 97843982576247.
  - Rollback: restore an earlier Lobby version, or set `GameplayPlaceId = 0` and republish.
- **v0.14.0 / 0.14.1:** party size 1–6, friends-only parties, automatic Spanish localization, and the records-board race fix. The checklist header calls 0.14.1 published as Lobby v19 / Gameplay v9; check that before relying on it.
- **v0.15.0:** persistent global Top 100 leaderboard (OrderedDataStore `SFH_GlobalBest_v1`) with personal rank. **Waiting for owner approval to publish.**
- **Open:**
  - real multiplayer and mobile tests
  - legacy-inbox coin compensation for 2 players, awaiting approval
  - the Tip Jar developer product was never created (hidden in the UI)

## Systems at a glance
- **Server roles:** Lobby / Router / Shift / Combined / Standalone, chosen at runtime from GameId and the server type (see [[ARCHITECTURE]]).
- **Gameplay services:**
  - shift state machine (Idle→Gather→Prep→Active→Results)
  - customers: 7 archetypes, 2 rare, plus the Customer From Hell
  - 8 disasters, each with a timeout fallback
  - scoring and S–F rating, crew awards, replay vote
- **Data:** `DataService` with session lock and retries, store `SFH_PlayerData_v1`. Studio uses throwaway profiles (`StudioUsesLiveData = false`).
- **Monetization (cosmetic only):** 5 game passes in the Lobby (VIP 199, Uniforms 99, MopSkins 75, CheckoutFX 99, NameTags 49 R$). See [[MONETIZATION]].
- **Localization:** English source with a full Spanish table, driven by `LocalizationService.RobloxLocaleId`.
- **UI:** `Theme.lua` tokens (mirroring Figma variables) and `UIKit.lua` components.

## Docs (linked from the repo, so editing here edits the repo)
- **Start here:** [[PROJECT_STATUS]] (stops at 0.12; newer status is in the release checklist).
- **Releases:** [[MASTER_RELEASE_CHECKLIST]], [[CHANGELOG]], [[LAUNCH_CHECKLIST]].
- **Architecture and migration:** [[ARCHITECTURE]], [[MIGRATION]].
- **Testing:** [[TEST_PLAN]], [[LIVE_TEST_PLAN]].
- **Other:** [[MONETIZATION]], [[ASSET_REGISTER]], [[REWARD_BRIDGE_REMEDIATION]], [[SFH_README]].

## Lessons this game taught (see Knowledge)
- [[Server Authority and Anti-Exploit]]: parties and teleport destinations come from the server; client requests are rate-limited.
- [[Persistence and DataStores]]: session locks, the exactly-once inbox, and Studio never touching live data.
- [[Release and Publish Safety]]: creating a place ≠ publishing ≠ cutover, and each step needs its own approval.
- [[Monetization Principles]]: cosmetic only, and Roblox disabled cross-experience pass sales on 2026-05-30.
- [[Localization]]: one strings table per language, plus a translation check script.
- [[Roblox Studio MCP Quirks]]
