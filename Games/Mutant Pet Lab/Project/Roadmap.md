---
type: project
game: "[[Mutant Pet Lab]]"
status: active
tags:
  - mutant-pet-lab
  - project
  - roadmap
updated: 2026-10-21
source: "[[CLAUDE_PROJECT_STATE]], owner briefs"
---
# Roadmap

## Done (Build B)
- [x] Egg migration M1–M3 (owned eggs, EggId incubation)
- [x] Finish 2A — six-family Cash [[Egg Families|Egg Shop]], hatch reveal, offline incubation
- [x] Finish 2B — 4-stage property expansion, Featured Specimen
- [x] Finish 2C — onboarding, assignments, [[Economy]] pass, secret [[Mutation Recipes|mutations]]
- [x] Finish 3 — two-client multiplayer M1–M9
- [x] Checkpoint E — server [[Traits and Variants|trait RNG]], Specimen Supply range, responsive UI
- [x] Release — production [[Persistence]], published v88 (2026-10-14)

## Next (needs owner)
- [ ] Live leave/rejoin save check ([[Known Issues]])
- [ ] Decide experience visibility and name (still "Untitled Experience")

## Phase 1: Visual foundation (approved 2026-10-15, in progress)
Direction and rules: [[Design Decisions]]. Validation is targeted per step, full at checkpoints.
- [x] A. Record approved decisions
- [x] B. Shared editable-in-Studio UI kit (2026-10-15)
- [x] C. Build Mode drag-to-place (+ overhead build camera) (2026-10-15)
- [x] **Checkpoint A** — passed 2026-10-15, snapshot `2026-10-15_phase1_checkpointA`
- [x] D. HUD simplification (2026-10-15): status cluster + 7-tile nav bar + Goals panel
- [x] E. Index redesign (2026-10-15): Species / Eggs / Mutations tabs, cards, detail, discovery banner
- [x] **Checkpoint B** — passed 2026-10-15, snapshot `2026-10-15_phase1_checkpointB` (Roblox save pending: screen was locked)
- [x] Migrate remaining screens to the kit (owner request 2026-10-15): Egg Shop, Mutation Lab, Creatures, My Lab + hatch reveal, Ranch, Research, Upgrades, Supply, Guide — snapshot `2026-10-15_phase1_ui_migration`
- [x] Save to Roblox — 2026-10-15 23:47 Studio reported the UI-migration build was already stored ("No changes … Did not save"); map overhaul saved 2026-10-16 00:11:59 (not published)
- [ ] Owner: review the screens and the new map on a real phone
- [x] F. Map/environment overhaul (2026-10-16): lighting, Mutation Reactor, Research Terminal at the reactor front, plaza + wayfinding, Specimen Showcase, commons berms, plot surrounds, 8 biomes, outer terraces, decor flag pass, Baseplate retired — [[Map Overhaul#Applied 2026-10-16]]
- [x] **Checkpoint C** — passed 2026-10-16, snapshot `2026-10-16_map_overhaul_checkpointC` (185/185, frozen + sight lines PASS, 4 viewports, performance unchanged; 2-player skipped — no multiplayer logic changed). Saved to Roblox, not published

## Phase 2: Creature + Hatching + Game-Feel Overhaul (direction APPROVED 2026-10-16; plan revised to 2A–2H)
- [x] Design/specification pass — [[Phase 2 Spec]]. Owner decisions: 12 *Phase 2:* entries in [[Design Decisions]]
- [x] Implementation plan: [[PHASE2_IMPLEMENTATION_PLAN]] (revision 2: checkpoints 2A–2H)
- [x] **Simulator-style UI revamp** (overnight 2026-10-16, Experimental): 8 screens + HUD, references recorded in [[UI - Figma TODO#Simulator-style UI revamp (2026-10-16, overnight) — Experimental / Candidate]]
- [x] **2A** creature render architecture — built, Play-verified (Experimental)
- [x] **2B** 7 body-plan prototypes — built: [[Creature Prototypes]] (Experimental)
- [x] Owner real-device review (2026-10-16): **prototypes and bottom nav NOT approved** → visual correction pass
- [x] Visual correction pass: 3 UI directions + 3 creature directions × 3 species — [[Visual Direction Review 2026-10-16]]
- [x] Owner chose UI **C** + creature **C** (Frostpup LEFT, Mossbit/Sparkbug RIGHT) — 2026-10-16
- [x] **UI-C1**: production side rails + status-pod HUD + Lab Task Board + Index redesign (snapshot `2026-10-16_ui_c1`)
- [x] **CREATURE-C1**: 7 body-plan representatives rebuilt (snapshot `2026-10-16_creature_c1`) — [[C1 Review Stage 2026-10-16]]
- [ ] **Owner review of the C1 stage** (gate)
- [x] Offline design pass (2026-10-20): [[MPL Visual Fingerprint]], building/egg/care/variant/viewer/visiting specs (candidates), owner blueprint template filed. **Execution order when Studio is back: [[Next Build Brief]]**
- [x] Owner decisions (2026-10-20): template sheets required · faceted finish selective · building route B · physical eggs, tap-to-crack, odds popup, % chance, chained locked eggs, rarity-scaled hatch (Open ×3 still candidate) · read-only care state · welcome hatch on own plot · Radiant stays a trait · decorations = future direction · negative visual rules. [[Design Decisions]]
- [x] Specimen sheets for the 7 representatives (2026-10-20, [[Specimen Sheets]]; Experimental until the owner signs off)
- [x] Faceted method test: Frostpup hybrid (faceted mane on a soft body) chosen in C3 (2026-10-21)
- [x] Read-only care state attributes (2026-10-20: Wellbeing/Hungry/FavoriteFed/HabitatMatch/SampleReady/FedAt on creature proxies)
- [x] Single-hatch physical egg foundation (2026-10-20: campus displays + odds %, incubator eggs, Crack! → existing Hatch, rarity-scaled reveal). Welcome-egg persistence still pending a reviewed schema change
- [x] Migrate remaining screens to C (2026-10-20): Egg Lab, Mutation Lab, Creatures viewer, Ranch, Research hex board, My Lab restyle, Upgrades chrome. [[C2 Review 2026-10-20]]
- [x] C2 creature refinements (Pebbletoad/Magmawisp faces, animator perf −42%, subtler rarity marker) + 7-body-plan in-context review captured
- [ ] **Owner review of C2** (gate before the other 29 species)
- [x] Save to Roblox of C2 + C3 + UI art pass (2026-10-21 13:32; not published)
- [x] Save to Roblox of the overnight build (covered by the 2026-10-21 save) — **not published**
- [x] **C3** seven body families locked + [[Roster Conversion Plan]] (2026-10-21) — [[C3 Review 2026-10-21]]
- [x] **Reference-driven UI art pass**, round 1 (2026-10-21): panel polish, vector icons, reveal redesign — [[UI Art Pass 2026-10-21]]
- [ ] **Owner visual review of the UI art pass** (gate), then round 2: Creatures chips, Research hex hierarchy, Index art, Mutation Lab, HUD
- [x] **Build Mode (owner R3):** compact strip, 1/2/4/8 snap grid, fixed overhead camera, shake fix (2026-10-21)
- [x] **Blender style anchors:** Frostpup + Mossbit live in game (2026-10-21) — [[Style Anchor Review 2026-10-21]]
- [ ] **Owner style review of the anchors** (gate), + decide R17 (plush) vs R16 (faceted) finish question
- [x] Convert the 5 remaining baseline species to Blender: all 7 anchors live, locked as production (2026-10-22)
- [~] **2C** all 36 species models: **24/36 Blender** (2026-10-22 overnight, batches 1–3). 12 review species remain (concept review first). [[Roster Conversion Plan]]
- [~] **2D** procedural animation: first slice + moods (eating, sad/low-wellbeing, happy, acknowledge, sleepy, sample-ready) 2026-10-22
- [~] **2E** hatching + welcome egg: tiered hatch presentation built (2026-10-22). Welcome egg = plan only, needs schema v4 approval: [[Welcome Egg Implementation Plan]]
- [x] **2F** mutation reveal + Reactor (2026-10-22: charge → pulse → reveal; secret; sputter). Awaiting owner review
- [ ] **2G** onboarding reorder — [[Early Game Reorder]] (exact moves finalised, waits for 2E)
- [~] **2H** audio, VFX, polish: 16 interim engine sounds + hooks; campus art layer (2026-10-22); final sounds pending

## Later (not yet scoped — no decisions recorded)
- [ ] Deeper gameplay / game-feel overhaul (after Phase 1)
- [ ] [[Creature Overhaul]]
- [ ] Post-Level-25 sink / monetization → [[Monetization TODO]]
- [ ] Player decorations (paths, lamps, planters, signs, benches, lab props, habitat decorations): direction approved 2026-10-20, **not scheduled** → [[Plot Decoration and Visiting]]
