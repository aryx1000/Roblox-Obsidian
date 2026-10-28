---
type: project
game: "[[Mutant Pet Lab]]"
status: current
tags:
  - mutant-pet-lab
  - project
updated: 2026-10-23
source: tools/vault_export.py
generated: true
---
# Current State

Live summary of where [[Mutant Pet Lab]] stands. The authoritative resume file is [[CLAUDE_PROJECT_STATE]] (in the project folder); this note links it with the backups.

- **Phase:** Build B released — v88 with production [[Persistence]] (2026-10-14).
- **Next:** see [[Roadmap]] and [[Known Issues]].
- **Project folder (code, exports, snapshots — never copied into the vault):** `~/Claude's Personal Workspace/MutantPetLab/`
- **Restore:** [[RESTORE]] · **Test history:** [[QA - Test History]]

> [!danger] Owner feedback 2026-10-16 (real-device review)
> **The current 7 creature prototypes are experimental and NOT approved as the final creature style. The current bottom navigation layout is NOT approved.** The HUD is too large and the panels too admin-like. Next: 3 UI directions (side-rail nav, compact HUD) + 3 directions each for Frostpup, Mossbit and Sparkbug, then wait for the owner's selection. Do not build the other 29 species, do not re-migrate panels, do not publish. See [[Design Decisions#Phase 2 correction: visual direction reset (owner, real-device review)]].
>
> **Review ready (2026-10-16):** [[Visual Direction Review 2026-10-16]]: 3 side-rail UI directions (recommended C) + 3 directions each for Frostpup / Mossbit / Sparkbug (recommended C) + [[Creature Face Language]]. Waiting for the owner's selection.
>
> **C1 review stage (2026-10-16):** [[C1 Review Stage 2026-10-16]]: UI-C1 (side rails, status pod, Lab Task Board, Index with 3D previews) and CREATURE-C1 (7 representatives rebuilt). Waiting for owner review; 29 species not built.

> [!danger] 2026-10-23: overnight work NOT in Roblox yet; restore from auto-recovery first
> A Studio update closed the place after the overnight run. All the work is in Studio's auto-recovery file (verified; backup in `MutantPetLab/recovery/`). **Next:** unlock the Mac, accept Studio's recovery prompt (or File → Open the backup .rbxl, then Save to Roblox to place 86236241957181), and verify it against snapshot `2026-10-22_overnight_cp9_campus`. Then the post-overnight brief continues. Checklist: [[Beta Readiness Checklist]].

> [!warning] Overnight run 2026-10-22: built, verified, NOT yet saved to Roblox
> 24/36 species are now Blender models; hatch, mutation and mood presentation; R17 Index rows; interim sounds; campus art layer; sign fix. All verified (185/185, no errors) in local snapshots up to `2026-10-22_overnight_cp9_campus`. **Studio Save to Roblox is pending** (the Mac screen was locked; the last save was 09:06). Studio still holds the work. Report: [[Overnight Work Report 2026-10-22]] · audit: [[Pre-Beta Audit 2026-10-22]] · welcome egg: [[Welcome Egg Implementation Plan]].

> [!success] Blender style anchors (2026-10-21): awaiting owner style review
> Frostpup and Mossbit are now Blender MeshPart creatures in the R16 blueprint style (all pets will follow this; see [[Design Decisions#Creature style: every pet follows the blueprint Frostpup (R16)]]). Side-by-side review: [[Style Anchor Review 2026-10-21]]. Build Mode got a compact bottom strip, a 1/2/4/8 snap grid and a fixed Bloxburg-style camera (shake fixed). Saved to Roblox 15:46, **not published**. Snapshot `2026-10-21_style_anchors`, 185/185. The other 34 species still use part-built or proxy models.

> [!success] C3 + UI art pass (2026-10-21) — awaiting owner visual review
> Seven creature body families locked ([[C3 Review 2026-10-21]], [[Roster Conversion Plan]]). Reference-driven UI art pass round 1: [[UI Art Pass 2026-10-21]] covers panel polish, vector icon system, and a full-screen hatch/discovery reveal. Saved to Roblox 13:32, **not published**. Snapshot `2026-10-21_ui_art_pass`, 185/185. 29 species still not built.

> [!info] Reference library (2026-10-20)
> Your living reference file is now an **active reference source**. Check [[Master Visual and Gameplay References]], [[Owner Reference Library]] and [[Do Not Copy]] before any player-facing design. Similar-game research: [[Similar Games Overview]]. Research only; no Studio or code changes.

> [!todo] When Studio is available
> Follow [[Next Build Brief]] (step 1: verify/save the C1 state and remove the leftover `MPL_PREVIEW_Stage`). Studio was unavailable on 2026-10-20; that day's work was design/research only.

%% BEGIN GENERATED %%
## Verified build (generated from `current/manifest.json`)

- **Snapshot:** `2026-10-22_overnight_cp9_campus` · exported 2026-10-22T17:49:35Z
- **Scripts:** 207 scripts / 1929022 bytes / checksum 640466738 matched Studio
- **Tests:** 185/185 fresh Play; server+client errors none; 59 fps
- **Persistence:** Production on live servers (MPL_PlayerData_PROD_V1 / Production / MPL_PROD_V1_); Studio always Mock
- **Published:** v88, 2026-10-14T19:42:30Z (this checkpoint is saved, not published)

## Local backups (`~/Claude's Personal Workspace/MutantPetLab/snapshots/`)

| Snapshot | Scripts | Checksum | Tests | Checkpoint |
|---|---|---|---|---|
| `2026-10-13_2C_checkpointA` | 171 | 1718600812 | 146/146 passing | Finish 2C checkpoint A: bug fixes + unlock gates + secret-mutation backend |
| `2026-10-13_2C_checkpointB` | 175 | 1236380078 | 154/154 passing | Finish 2C checkpoint B: onboarding guide + 22 assignments (ProgressionService) |
| `2026-10-13_2C_checkpointC` | 178 | 1066601942 | 163/163 | Finish 2C checkpoint C: economy pass (3/4/1 assay payouts), Finish2C_Economy_Test, secret  |
| `2026-10-13_2C_checkpointD` | 178 | 1981936296 | 163/163 | Finish 2C checkpoint D: 30-step new-profile playthrough incl. live Biolume secret; 7 UI fi |
| `2026-10-13_post_recovery` | 169 | 2123999688 | 136/136 passing | Build B Finish 2B complete; Finish 2C partially applied (see CLAUDE_PROJECT_STATE.md) |
| `2026-10-14_checkpointE` | 181 | 770847473 | 173/173 | Build B Checkpoint E: trait RNG (CreatureFactory), Specimen Supply range check (SpecimenSu |
| `2026-10-14_published_baseline` | 178 | 1981936296 | 163/163 | Published multiplayer-validated baseline (M1-M9 PASS), published 2026-10-14 07:23 local; c |
| `2026-10-14_release_persistence` | 183 | 2048056006 | 185/185 | Build B release: production persistence (live servers: MPL_PlayerData_PROD_V1/Production,  |
| `2026-10-15_phase1_checkpointA` | 186 | 26399871 | 185/185 | Phase 1 Checkpoint A: editable UI kit + Build Mode drag-to-place. 4 viewports, placement p |
| `2026-10-15_phase1_checkpointB` | 186 | 1980316468 | 185/185 | Phase 1 Checkpoint B: HUD + nav bar + Goals (1D) and Index redesign (1E) on the editable k |
| `2026-10-15_phase1_ui_migration` | 186 | 830647031 | 185/185 | Phase 1 UI migration complete: all 12 game screens are editable kit screens (Build Mode, H |
| `2026-10-16_creature_c1` | 195 | 983670883 | 185/185 | CREATURE-C1: 7 body-plan templates rebuilt in the approved creature language (Frostpup LEF |
| `2026-10-16_map_overhaul_checkpointC` | 186 | 830647031 | 185/185 | Map overhaul Checkpoint C: Mutation Reactor, Research Terminal at reactor front, plaza/way |
| `2026-10-16_phase2_overnight_final` | 191 | 641703739 | 185/185 | Phase 2 overnight final: UI revamp + phone-audit fixes (21 labels to 15 px, Research actio |
| `2026-10-16_phase2_ui_render_prototypes` | 191 | 641703739 | 185/185 | Phase 2 overnight: simulator-style UI revamp (8 screens + HUD), client creature display la |
| `2026-10-16_ui_c1` | 194 | 644162644 | 185/185 | UI-C1: Direction C production side rails (left Build/MyLab/Creatures/Index, right Goals/Ra |
| `2026-10-16_visual_direction_review` | 193 | 1773091301 | 185/185 | Visual direction correction pass: 3 side-rail UI directions (12 editable mock ScreenGuis)  |
| `2026-10-20_c2_creatures_eggs_care` | 200 | 919650656 | 185/185 | Checkpoints 2-6: Pebbletoad/Magmawisp faces, animator perf (BulkMoveTo, hinged wings, medi |
| `2026-10-20_ui_c2_screens` | 198 | 406807763 | 185/185 | Checkpoint 1: Direction-C migration of Egg Shop, Mutation Lab, Creatures (viewer), Ranch,  |
| `2026-10-21_build_grid_camera` | 202 | 1159520557 | 185/185 | Build Mode (owner R3): compact bottom strip; snap grid 1/2/4/8 studs with drawn grid lines |
| `2026-10-21_c3_creature_baselines` | 200 | 671936518 | 185/185 | C3: guide-tracker notice band + left-rail thumbstick safe area; Frostpup hybrid; Luminous  |
| `2026-10-21_style_anchors` | 202 | 1047681287 | 185/185 | Blender style anchors: Frostpup (15 MeshParts, 712 tris) + Mossbit (11 MeshParts, 594 tris |
| `2026-10-21_ui_art_pass` | 201 | 1944016977 | 185/185 | UI art pass A-L partial: shared panel polish (depth lip, sheen title plates with vector ic |
| `2026-10-22_anchor_pebbletoad` | 202 | 1442844573 | 185/185 | Blender anchor 4/7: Pebbletoad (9 MeshParts, 688 tris; squat hopper body + eye domes, face |
| `2026-10-22_anchor_slimelet` | 202 | 1767855698 | 185/185 | Blender anchor 3/7: Slimelet (6 MeshParts, 516 tris, gel dome T 0.22 with visible nucleus, |
| `2026-10-22_anchors_magmawisp_rockling` | 202 | 1682908664 | 185/185 | Blender anchors 5-6/7: Magmawisp (11 MeshParts, 672 tris, hover wisp, orbit stones, gold L |
| `2026-10-22_overnight_cp1_anchors_batch1` | 204 | 1004797974 | 185/185 | Overnight CP1: Sparkbug Blender anchor (7/7 anchors live) + Batch 1 Gel/Sprout species Glo |
| `2026-10-22_overnight_cp2_hatch_mutation_moods` | 206 | 576541206 | 185/185 | Overnight CP2: HatchSequence (incubator glow/beams/shards/camera push/flash/creature pop,  |
| `2026-10-22_overnight_cp3_batch23_fitted` | 206 | 1314960428 | 185/185 fresh Play; errors none | Overnight CP3: fitted 11 queued Blender species (BrimstoneBloom, Toxibloom, Embercub, Cind |
| `2026-10-22_overnight_cp4_index_audio` | 206 | 1563988935 | 185/185 fresh Play; client/server errors none | Overnight CP4/CP10: R17 Index detail rows (Front/Side/Back views, Variants chips, MUTATES  |
| `2026-10-22_overnight_cp9_campus` | 207 | 640466738 | 185/185 fresh Play; server+client errors none; 59 fps | Overnight CP9: client-local campus art layer (Route B) CampusDecorController - egg greenho |

Restore procedure: [[RESTORE]]. Full resume notes: [[CLAUDE_PROJECT_STATE]].
%% END GENERATED %%

## Notes
