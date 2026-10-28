---
type: project
game: "[[Mutant Pet Lab]]"
status: open
tags:
  - mutant-pet-lab
  - project
  - issues
updated: 2026-10-15
source: "[[FINISH_3_VALIDATION]], [[PERSISTENCE_ACTIVATION]]"
---
# Known Issues

## Open
| Issue | Impact | Area | Notes |
|---|---|---|---|
| Live leave/rejoin save not yet validated | High until checked | [[Persistence]] | Owner to run with any account |
| Breed / Upgrade / Research remotes not location-gated | Low | [[Architecture#Remotes]] | Costs and gates still apply |
| No sink after Level 25 | Medium (late game) | [[Economy]] | Deliberately deferred |
| Experience still named "Untitled Experience", visibility editors-only | Launch | [[Roadmap]] | Owner decision |
| Studio not saved to Roblox since Checkpoint A (screen locked) | Medium until saved | [[Current State]] | Local snapshots are verified; owner: File → Save to Roblox |
| Emulator screenshots of the new screens not taken (screen locked) | Low | [[QA - Test History]] | Layout verified numerically |
| `BioWetlands/WildBioRidge` ×8 (Ball, 60×30×115) may reach ~10 studs into neighbouring plots' Stage-2/3 wing land if rendered as ellipsoids | Low–Medium (verify) | [[Map Overhaul]] | Found offline in the map audit; check in Studio |
| Unexplained v83 publish (2026-10-14 14:16) during auto-clicker use | Process | [[Current State]] | Not done by Claude |

## Fixed
| Issue | Fixed in |
|---|---|
| Phone text ~7–8 px and 21–22 px buttons | Phase 1 UI migration (all screens ≥12 px text, ≥44 px taps) |
| Phone Build panel covered Jump; arrow-button touch placement | Phase 1 C: Build Mode (drag → PLACE, touch controls hidden while building) |
| Esc is reserved by Roblox's menu, so it can't cancel in-game actions | Phase 1 C uses Q / Backspace / B-button |
| Trait rolls predictable from pet ids | Checkpoint E → [[Traits and Variants]] |
| `ClaimSpecimen` had no distance check | Checkpoint E → [[Economy#Specimen Supply]] |
| 1×1 startup viewport broke UI scale; tablet branches; corner buttons under Jump | Checkpoint E |
| Lost changes during save / overlapping saves / shutdown timing / leave-during-load | Release → [[Persistence]] |
| Pen-upgrade marker crash (`info.Color`) | Finish 2C A |
