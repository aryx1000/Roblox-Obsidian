---
type: planning
game: "[[Mutant Pet Lab]]"
area: release
status: current
updated: 2026-10-22
tags:
  - mutant-pet-lab
  - planning
  - qa
---
# Pre-beta TODO audit (CP14, 2026-10-22)

Snapshot audited: `2026-10-22_overnight_cp9_campus` (207 scripts, 185/185 tests, server and client errors none, Workspace 1,949 instances against the ~2,000 cap).

## Blockers before a beta publish
| # | Item | Owner of the next step | Notes |
|---|---|---|---|
| 1 | **Save to Roblox** of tonight's work | Claude, once the Mac screen is unlocked | Last save 09:06; four local snapshots since then are verified but not in the Roblox place file |
| 2 | **4-device QA** (667×375, ~874×402, tablet, 1366×768) of the new screens and the campus layer | Claude (needs the unlocked screen for the Studio device emulator) | Not run tonight. Nothing claimed |
| 3 | **Owner reviews**: Blender roster batches 1–3, campus art, hatch/mutation presentation, moods, Index R17 rows | Owner | [[Overnight Work Report 2026-10-22]] |
| 4 | **Welcome egg** (schema v4) + onboarding reorder (2G) | Owner approval of schema v4 + publish-time shutdown | [[Welcome Egg Implementation Plan]]. Stopped at the plan by design |
| 5 | **12 species still on part-built / proxy models** | Owner concept review first | Prismaclaw, Fluxaroo, Sporephant, Auroroot, ObsidianLynx, Tempestrix, Nucleonox, FerriteDrake, Biolume, Nullmorph, Quasipod, Chimerax (all flagged for review in [[Roster Conversion Plan]]) |
| 6 | **Final audio** | Owner (licensed or original sounds) | 16 interim Roblox engine sounds tagged `Interim=true` in `UI.Sounds` |
| 7 | **Publish** | Owner explicit approval only | Private game; v88 + the 00:42 playtest publish are the last publishes |

## Should fix before beta (non-blocking)
- **Geodewisp:** the grey geode hood sits off to one side. Recentre it or confirm it is intended.
- **Glacierbit:** inherits Pebbletoad's yellow eyes. Fine for a Hopper, but confirm.
- Embercub, Cinderhorn and Glacierbit animate at about 33–35 µs close range (target ≤ 30; the approved Frostpup anchor is 36.6). Total budget is fine.
- `ServerStorage.MPL_DesignReview.Tools.FitSpecs` in Studio holds only Batch 1. The complete spec file is `MutantPetLab/blender/fit_specs.luau`.
- `MPL_DesignReview` holds four duplicate imports (`*_Model_DuplicateImport`): review-only, server-side, harmless; delete when convenient.
- Campus layer: the egg dome and showcase dome use SmoothPlastic (Glass hides translucent parts behind it). Check the look on a phone.
- Studio playtest note: the root `CorruptedXNightmares` model in Workspace during Play is the Studio player's character, not a stray object.

## Verified tonight (no action needed)
- No `loadstring` / `getfenv` / deprecated `wait`/`spawn`/`delay`, no `print` spam, no Marketplace / monetization code, HTTP disabled, DataStore used only by `PlayerDataRepository` (Studio = Mock).
- 9 remotes. Property requests are server-validated and rate-limited: overlap, bounds and cooldown were all exercised in the Build Mode QA.
- Build Mode: open → overhead camera, place / bounds-reject / overlap-reject / move+rotate / sell (half refund) / exit restores the Custom camera.
- Performance: 11 new species 9–35 µs close; campus layer 246 client parts; ~59 fps in Studio Play.
