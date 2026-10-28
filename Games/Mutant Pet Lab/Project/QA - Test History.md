---
type: project
game: "[[Mutant Pet Lab]]"
status: current
tags:
  - mutant-pet-lab
  - project
  - qa
updated: 2026-10-21
source: "FINISH_3_*.md, PLAYTHROUGH_2C_D, PERSISTENCE_ACTIVATION, snapshots/*/manifest.json"
---
# QA - Test History

Unit tests run in a fresh Play server (see [[Architecture#Tests]]). Snapshot checksums are in [[Current State]].

| Date | Checkpoint | Unit tests | Other validation | Doc |
|---|---|---|---|---|
| 2026-10-13 | Finish 2C A | 146/146 | — | [[CLAUDE_PROJECT_STATE]] |
| 2026-10-13 | Finish 2C B | 154/154 | — | [[CLAUDE_PROJECT_STATE]] |
| 2026-10-13 | Finish 2C C | 163/163 | Economy simulation | [[ECONOMY_2C]] |
| 2026-10-13 | Finish 2C D | 163/163 | 30-step new-profile playthrough, Biolume live | [[PLAYTHROUGH_2C_D]] |
| 2026-10-14 | Finish 3 | — | Two-client M1–M9 PASS | [[FINISH_3_MULTIPLAYER]] |
| 2026-10-14 | Checkpoint E | 173/173 | 4-viewport mobile audit, 43-step playthrough, graph test, perf, security audit, MP regression | [[FINISH_3_VALIDATION]] |
| 2026-10-14 | Release v88 | 185/185 | Studio Play loads Mock; no DataStore activity | [[PERSISTENCE_ACTIVATION]] |
| 2026-10-15 | Phase 1 Checkpoint A (UI kit + Build Mode) | 185/185 | 4 viewports (iPhone 7, iPhone 17 Pro, iPad Air, 1366×768) incl. real touch drag via emulator; placement save/load round trip (0/90/270°); 2-player simultaneous placement + forged-request rejection | [[Design Decisions#Validation: targeted during work, full at checkpoints]] |
| 2026-10-15 | Phase 1 Checkpoint B (HUD + Index) | 185/185 | text ≥12 px and close ≥45 px at phone scale; all kit screens fit the 4 viewports (computed — emulator screenshots pending, screen locked); nav, Goals, Index tabs/detail, secret hint, real discovery banner verified in Play | [[Index Collection Screen]] |
| 2026-10-15 | Phase 1 UI migration (all 12 screens) | 185/185 | phone audit: no text <12 px, no tap target <44 px; all kit panels fit the 4 viewports (computed); Egg Shop buy/locked, Mutation Lab mutate + reveal, Research/Upgrades install + locked reasons, Supply claim + cooldown, Creatures detail, Guide advance, Ranch install, My Lab assign/incubate/hatch/eggs/land verified in Play; no client errors | [[UI - Figma TODO]] |
| 2026-10-16 | Map overhaul Checkpoint C | 185/185 | frozen check PASS (8 plots, 6 prompts, exact footprint intrusion test); sight lines PASS 8/8 raycast + geometric; live prompts (Research/Egg Shop/Index/Mutation/Upgrades) open; placement OK, out-of-bounds rejected; 4 viewports via emulator (iPhone 7 667×375, iPhone 17 Pro, iPad Air 5, Average Laptop 1366×768); ranch tick 0.185/0.572 ms vs 0.173/0.583; Studio frame time throttled (15 fps) before and after; 1,949 Workspace instances; 2-player skipped |
| 2026-10-16 | Phase 2 overnight (UI revamp + 2A/2B) | 185/185 | fresh Play suite; UI runtime check (every screen opens and fills, HUD counts, no client errors); computed phone audit 21 panels × 4 viewports (after fixing 21 small labels + Research button); render controller live test with 8 proxies (7 prototypes attach, fallback for Embercub, ground offset ≤ 0.02, follow + cleanup OK); Animator.Step ≈ 14 µs/creature; Studio throttled (screen locked) so FPS not meaningful; 2-player skipped; Save to Roblox blocked (screen locked) | [[PHASE2_IMPLEMENTATION_PLAN]] |
| 2026-10-20 | C2 (screens, creatures, eggs, care state) | 185/185 (twice: before and after the server display-attribute change) | fresh-session C1 integrity (195 scripts / checksum 983670883 matched) before work; every migrated screen opens with live data (Egg Lab, Mutation Lab, Creatures viewer, Ranch with a real pen, Research, My Lab, Upgrades) and no client errors; static phone audit (no text <12 px, no tap target <44 px; 1 fix); 667×375 device-frame fit for Creatures + Egg Lab; animator microbenchmark best-of-5 (Sparkbug 34.8→20.3 µs near, 33.8→18.2 µs medium); 7-body-plan review in a real pen + 30-stud + variants; physical eggs: campus displays/lock/odds card state, incubator egg → Ready → Crack! → existing Hatch → rarity-scaled reveal (NEW DISCOVERY, 22% chance); care attributes replicate; Workspace stays 1,949; 4-viewport emulator captures + Save to Roblox blocked (Mac locked); 2-player skipped (no multiplayer logic changed) | [[C2 Review 2026-10-20]] |
| 2026-10-21 | C3 creature baselines | 185/185 | Guide-tracker safe-area rule checked at 4 viewports (numeric 667/tablet/1366, visual 874/1366); animator best-of-5 (Sparkbug 27.3 µs, Frostpup 31.4, Luminous 35) | [[C3 Review 2026-10-21]] |
| 2026-10-21 | UI art pass (round 1) | 185/185 | Fresh Play, no game errors; reveal fit computed at 4 viewports, seen at phone; panels seen in Play; Ranch slots with creatures NOT seen | [[UI Art Pass 2026-10-21]] |
| 2026-10-21 | Build Mode grid + fixed camera | 185/185 | Snapped placement accepted by the server (10,−32); camera jitter 0 idle / after forced follow-camera / after re-entry mid-exit | [[Design Decisions#Build Mode: compact strip, snap grid, fixed camera]] |
| 2026-10-21 | Blender style anchors (Frostpup + Mossbit) | 185/185 | Pen, roaming, 30 studs, viewer, Index, showcase, Standard + Luminous; floor height, orientation, LOD; animation benchmark; 8 screens open; Build Mode regression; no client/server errors; temp bridge removed | [[Style Anchor Review 2026-10-21]] |

## Standing rules
- Representative viewports only: 667×375, 874×402, one tablet, 1366×768.
- Max 3 Studio processes unless the owner approves more.
- Remove `MPL_TEMP` debug hooks before every snapshot.
- Never report an untested result as passing.

Lessons: [[Testing and Validation]], [[Multiplayer Testing in Studio]], [[Responsive Mobile UI]].
