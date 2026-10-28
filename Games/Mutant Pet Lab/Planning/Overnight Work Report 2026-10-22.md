---
type: report
game: "[[Mutant Pet Lab]]"
status: awaiting-owner-review
date: 2026-10-22
tags:
  - mutant-pet-lab
  - report
  - overnight
---
# Overnight Work Report 2026-10-22

> [!warning] Read first
> Everything below is built and verified in Studio, but **the last Save to Roblox is 09:06**. Later the Mac screen locked, and macOS blocks the computer-use File menu while it is locked. Studio still holds all the work (`2026-10-22_overnight_cp9_campus`); local snapshots + git hold verified copies. **Nothing was published.** No monetization, schema, permission, visibility or HTTP changes. No other game touched.

## A. Completed (numbered)
1. **CP1:** Sparkbug fitted, so all **7 Blender body-family anchors** are live. Decision recorded: *SEVEN BLENDER BODY-FAMILY ANCHORS APPROVED FOR PRODUCTION*.
2. **CP2:** final 29-species manifest by family, with tris/mesh targets, Luminous tints and review flags: [[Roster Conversion Plan]].
3. **CP3 Batch 1** (Gel + Sprout): Gloamgel, Tidegill, Aquaflux, Bloomtail, Thornling, Radisprout, BrimstoneBloom, Toxibloom. Modelled, imported, fitted.
4. **CP3 Batches 2–3** (Critter / Hopper / Flyer / Wisp): Embercub (no longer the fallback ball), Cinderhorn, Voltusk, Glacierbit, Circuitfin, Miremoth, Fungloom, Cryolume, Geodewisp. Modelled, imported by you, fitted, lineup-checked. **24/36 species are now Blender models.**
5. Pipeline tools:
   - `blender/mpl_kit.py` (modelling kit)
   - `add_spec.py`
   - `fit_specs.json` / `.luau`
   - Studio `CreatureFitter` (one call fits a species: roles, LOD, Luminous, face re-seat, archive)
6. **CP5 hatch presentation** (`HatchSequence`):
   - glow, ring, beams, sparkles, camera push, shell shards, flash, then the creature pops toward the camera;
   - pre-reveal tiers Normal 1.1 s / Rare 1.8 / Extreme 2.2 / Discovery 2.6, followed by the reveal card (totals about 3 / 4.5 / 5–6 s);
   - egg shake ramps up until the flash.
7. **CP6 mutation presentation** (`MutationSequence`):
   - Machine → cable pulses → Reactor charge;
   - success shock rings; **secret** gold/violet double ring + burst; failed **sputter** + smoke;
   - results use the big reveal ("NEW MUTATION!", "SECRET MUTATION!");
   - no recipe or odds changes.
8. **CP7 creature emotions:**
   - blink, curious;
   - eating hop (favourite-food squint);
   - **sad/low wellbeing = droopy eyes, lowered head, slow bob (never angry)**;
   - sleepy when idle and alone;
   - acknowledgement hop when you approach;
   - sample-ready bounce; thriving squint.
   All read-only from server care attributes; the client never decides wellbeing.
9. **CP4 Index:** R17-style detail rows: Front/Side/Back 3D views, Variants chips, "MUTATES INTO" lineage chips (undiscovered results show "???"; secrets hidden).
10. **CP4 Creatures viewer:** reviewed. It already had the live rig, view/zoom/mode tabs and icon rows; fixed the broken 🐾 glyph in the count pill ("SPECIMENS 3/6").
11. **CP10 audio/VFX hooks:** 16 interim sounds (Roblox built-in engine sounds, tagged `Interim=true`) wired to click/open/close/place/error/hatch crack/pop/discovery/success/mutate charge/success/sputter/reactor/research unlock.
12. **CP8 Welcome Egg:** implementation plan written; **stopped** because it needs schema v4: [[Welcome Egg Implementation Plan]].
13. **CP9 campus art pass** (Route B, client-local, **0 new Workspace instances**). Each facility now has its own silhouette:
    - **Egg Research Center:** egg-shaped greenhouse dome with ribs, glow seam, wood ring wall, "EGGS".
    - **Mutation Lab:** violet vault, **twin bubbling specimen tubes**, pipe crown arcing to the Reactor, "MUTATE".
    - **Upgrades:** gold gantry crane + hanging crate, turning gear sign, tool pegboard, "UPGRADES".
    - **Specimen Supply:** striped greenhouse-cart awning, crates, glowing canisters, lantern, flag, "SUPPLY".
    - **Research (Reactor front):** hex holo panels, observatory desk, antenna dish, "RESEARCH".
    - **Specimen Showcase:** display dome + gold halo; the **old prototype balls are replaced (client-side) by the live Blender Slimelet/Frostpup/Embercub/Rockling/Mossbit/Sparkbug rigs**.
14. **Bug fix:** 4 facility signs (Supply, Mutation Lab, Museum, Upgrades) had their text on the face pointing **into** the booth, so they read blank from the plaza. All now face the plaza. The Upgrades booth sign said "RESEARCH CENTER" and now reads **"UPGRADE WORKSHOP"**.
15. **CP11 Build Mode QA:** pass.
16. **CP13 technical audit:** clean.
17. **CP14 pre-beta audit:** [[Pre-Beta Audit 2026-10-22]].
18. Earlier in the session (before the overnight run): Slimelet/Pebbletoad/Magmawisp/Rockling anchors, an owner-requested publish at 00:42, the performance check.

| Before (booths) | After |
|---|---|
| ![[campus-before.jpg]] | ![[campus-after.jpg]] |
| ![[campus-egg-dome.jpg]] | ![[campus-mutation-lab.jpg]] |
| ![[campus-supply.jpg]] | ![[campus-after-upgrades.jpg]] |
| ![[campus-showcase-rigs.jpg]] | ![[index-grid-blender.jpg]] |
| ![[batch23-lineup-a.jpg]] | ![[batch23-lineup-b.jpg]] |

## B. Files
**Studio (new or changed):**
- `ReplicatedStorage.MutantPetLab.Creatures.Species.*`: 22 Blender templates added 2026-10-22 (5 anchors: Slimelet, Pebbletoad, Magmawisp, Rockling, Sparkbug + 17 roster species); with Frostpup + Mossbit = 24.
- `Creatures.HatchSequence` (new), `Creatures.MutationSequence` (new), `CreatureAnimator` (moods).
- `PropertyController`, `EggWorldController`, `BreedingController`, `CreatureRenderController` (moods, mesh preload), `ResearchController`, `IndexController`, `CreatureDetailController`.
- `StarterPlayerScripts…Controllers.CampusDecorController` (new).
- `UI.Sounds` (16 sounds); StarterGui Index detail rows.
- `Workspace.MutantWorld.Campus.*.FacilitySign` SurfaceGui faces + the Upgrades sign text.
- `ServerStorage.MPL_DesignReview` (tools, archive, 4 duplicate imports).

**Local (`~/Claude's Personal Workspace/MutantPetLab/`):**
- `blender/*_Model.fbx` + `.blend` (20 species), `mpl_kit.py`, `add_spec.py`, `fit_specs.*`, `IMPORT_QUEUE.md`
- `design_review/CreatureFitter.luau`, `design_review/CampusDecorController.luau`
- `CLAUDE_PROJECT_STATE.md`

**Vault:** this report; [[Welcome Egg Implementation Plan]]; [[Pre-Beta Audit 2026-10-22]]; [[Roster Conversion Plan]]; `Planning/Assets/Overnight 2026-10-22/`; [[Design Decisions]] (anchors locked); Roadmap; Current State; Log 2026-10-22.

## C. Import queue
**Empty: all 20 rows DONE.** You imported all of them, including four that were already fitted. Those duplicates are parked in `ServerStorage.MPL_DesignReview` as `*_Model_DuplicateImport` and can be deleted. Paths, for the record: `~/Claude's Personal Workspace/MutantPetLab/blender/<Species>_Model.fbx` (Sparkbug/Magmawisp/Rockling: `<Species>_StyleAnchor.fbx`).

## D. Tests
| Test | Result |
|---|---|
| Unit tests (fresh Play server), after every checkpoint | **185/185**, server errors none |
| Client error log after CP3/CP4/CP9 | none (one CP9 parse error found by this check and fixed before the snapshot) |
| Animation cost, 11 new species (Play client, close) | 9.3–35.4 µs (Frostpup anchor 36.6) |
| Hatch timing | Normal reveal ≈ 1.4 s after crack; egg holds until the flash |
| Real mutation Slimelet + Rockling → Magmawisp | charge → NEW MUTATION reveal |
| Moods | hungry Frostpup droops; Mossbit favourite-food squint |
| Build Mode | open, place, out-of-bounds reject, overlap reject, rate-limit, move + rotate 90°, sell (half refund), exit restores the camera |
| Campus layer | 246 client parts, ~59 fps Studio Play, no errors |
| **Not tested** | **4-device viewports** (needs the unlocked screen); real phone |

## E. Saves, snapshots, commits
| Checkpoint | Snapshot | Commit | Roblox save |
|---|---|---|---|
| CP1 anchors + batch 1 | `2026-10-22_overnight_cp1_anchors_batch1` | a9336e1 | 08:40 |
| CP2 hatch/mutation/moods | `2026-10-22_overnight_cp2_hatch_mutation_moods` | 194dd8c | **09:06 (last)** |
| CP4/CP10 Index + audio | `2026-10-22_overnight_cp4_index_audio` | 84dcf6a | pending |
| CP3 batches 2–3 fitted | `2026-10-22_overnight_cp3_batch23_fitted` | c8ac031 | pending |
| CP9 campus | `2026-10-22_overnight_cp9_campus` | 01a6658 (+51c3c06 source) | pending |

Blender model commits: 82745da, 4299329. State: the CLAUDE_PROJECT_STATE commit. **Publish: none tonight.**

## F. Blockers
**Needs you:**
1. **Unlock the Mac** so Claude can Save to Roblox (or do File → Save to Roblox yourself; Studio already holds everything).
2. **Welcome egg:** approve schema v4 + the publish-time server shutdown, and confirm the welcome egg *replaces* the free starter egg.
3. Reviews: roster batches 1–3, campus art, hatch/mutation timing, moods.
4. The 12 review species need concept direction (Legendary/Mythic/new anatomy).
5. Final audio source (licensed or original).

**Future work (Claude):** 4-device QA; CP4 round 2 screens; Geodewisp hood centring; resync Studio FitSpecs; delete duplicate imports.

## G. Master checklist
- [x] CP1 7 anchors locked
- [x] CP2 29-species manifest
- [~] CP3 roster: 17/29 remodelled (all non-review species); 12 review species pending concepts
- [~] CP4 UI pass: Hatch reveal ✓, Index ✓, Creatures viewer ✓ (minor); HUD / rails / Goals / Egg Lab / Mutation Lab / Ranch / Research / My Lab / Upgrades only have round 1 (2026-10-21)
- [x] CP5 hatch/discovery presentation
- [x] CP6 mutation reveal
- [x] CP7 creature emotions (core set; habitat/social optional ones not done)
- [!] CP8 welcome egg: plan only, needs schema approval
- [x] CP9 campus art pass (awaiting your review)
- [~] CP10 audio/VFX hooks: interim sounds only
- [x] CP11 Build Mode QA
- [!] CP12 4-device QA: blocked (screen locked)
- [x] CP13 technical QA
- [x] CP14 pre-beta audit
- [!] Save to Roblox of CP3/CP4/CP9 work: blocked (screen locked)

## H. Completion estimates
| Area | Estimate |
|---|---|
| Creature roster art | ~67% of species (24/36); ~80% of effort (the review species are the hardest) |
| Hatch / mutation / emotion feel | ~85% (final audio + owner timing review left) |
| UI art | ~65% |
| Campus / world art | ~60% (buildings done; plots/paths/landscape polish later) |
| Onboarding + welcome egg | ~30% (plan ready, schema gated) |
| Pre-beta readiness overall | **~65–70%** |

## I. Next steps
- **NEXT USER ACTION:** unlock the Mac (or Save to Roblox yourself), then review this report and answer the welcome-egg schema v4 question.
- **NEXT CLAUDE ACTION:** Save to Roblox → 4-device QA of the new screens and the campus → CP4 round 2 screens.
- **OVERALL PROJECT STATUS:** Phase 2 is well past the midpoint. 24/36 creatures are production Blender models; the hatch/mutation/emotion presentation is built; the campus now has distinct buildings; tests stay green. Gated on owner reviews, schema v4 approval and the missing Roblox save.
