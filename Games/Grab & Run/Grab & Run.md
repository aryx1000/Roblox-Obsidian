---
tags: [roblox, game, grab-and-run]
owner: AYRX Entertainment (group 9350216)
place-id: 114881871837749
universe: 10769869587
status: live; hands-off for Claude
---

# Grab & Run

Back to [[Home]]. Reusable lessons are in [[Knowledge/Index|Knowledge]].

**GRAB N RUN!** is a live AYRX Entertainment heist game (themes: "Crowned Heist", "Golden Vault Heist"). The loop is presumably grabbing loot (e.g. the Golden Toilet) and carrying it out. That's inferred from the art docs' `LootService`/`CarryService` references, not confirmed.

## Identity
- Universe **10769869587**, place **114881871837749**. Public; it appears in the group's games list.
- **⚠️ Standing rule: Claude never opens, edits, saves or publishes GRAB N RUN!** This note records knowledge only.

## What exists locally
- **Art pipeline:** `~/Documents/GRAB_AND_RUN_Art/` (`blender/`, `textures/`, `exports/`, `renders/`, `docs/`).
  - Shared material library: `blender/library/GR_MaterialLibrary.blend`.
  - Pipeline test asset: `blender/loot/GR_Loot_GoldenToilet.blend` (4,310 tris; textures uploaded to Roblox).
- **Key art:** `~/Crowned Heist_ Grab & Run.png` and `~/Grab & Run_ Golden Vault Heist.png`.
- **Game code:** not on disk here; it lives only in the Roblox place. Systems referenced by the art docs include `LootService`, `CarryService` and `LootData`.

## Docs
[[GR_AssetStandards]]: scale, axes, naming, triangle budgets, the gold material recipe and the loot override contract. This is the reference for **any** AYRX Blender→Roblox asset; see [[Asset Pipeline (Blender to Roblox)]].

## Unknowns (fill in when the owner shares them)
- Current version, player counts and monetization.
- Gameplay loop details beyond loot carrying.
