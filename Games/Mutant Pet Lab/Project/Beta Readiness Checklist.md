---
type: project
game: "[[Mutant Pet Lab]]"
status: current
updated: 2026-10-23
tags:
  - mutant-pet-lab
  - project
  - qa
  - release
---
# Beta Readiness Checklist (master)

**Legend:** [x] COMPLETE · [~] IN PROGRESS · [ ] REMAINING · [!] BLOCKED

**Detail sources:**
- [[Pre-Beta Audit 2026-10-22]] · [[Overnight Work Report 2026-10-22]] · [[Known Issues]]
- [[Welcome Egg Migration Proposal]] · [[Remaining 12 Species Production Specs]] · [[Audio Placeholder Audit 2026-10-23]]

## CORE
- [x] Creature collection, traits, variants, pens, care, crops, feeders, samples (Build B)
- [x] Mutation recipes + secret mutations (server)
- [x] Research, upgrades, assignments / Lab Task Board, levels to 25
- [ ] Post-Level-25 sink (deliberately deferred)

## PERSISTENCE
- [x] Versioned schema v3 + migrations, sanitizer, repository, Mock in Studio, production store on live servers (v88)
- [x] 185/185 tests including persistence contract tests
- [!] Schema v4 (welcome egg): proposal written, **needs owner approval** + shutdown-on-publish
- [ ] Live leave/rejoin save validation (owner, any account)

## SECURITY
- [x] All economy/property actions server-validated, request cooldowns, distance checks (Supply, Egg shop)
- [x] Client never authoritative (care, wellbeing, hatch, mutation results are server data; visuals client-only)
- [x] HTTP off; no loadstring; no Marketplace code
- [ ] Location gates for Breed / Upgrade / Research remotes (low risk; costs still apply)

## MAP
- [x] Valley overhaul, Reactor landmark, plots, terraces, biomes (approved 2026-10-16)
- [~] Plot/landscape polish (later); BioWetlands ridge overlap still to verify

## BUILD MODE
- [x] Drag-to-place, 1/2/4/8 grid, fixed overhead camera, turn view, sell confirm
- [x] QA 2026-10-22: place / bounds / overlap / cooldown / move + rotate / sell / exit camera
- [ ] 4-viewport check of the strip (phone thumbs)

## UI
- [x] Side rails + status-pod HUD, Lab Task Board, all screens migrated to Direction C, vector icons, panel polish (round 1)
- [x] Index second pass (R17 rows: views, variants, lineage chips)
- [~] Second pass for HUD, rails, Goals, Egg Lab, Mutation Lab, Creatures, Ranch, Research, My Lab, Upgrades, reveal
- [!] 4-device viewport check (needs Studio open + an unlocked screen)

## CREATURE MODELS
- [x] 7 body-family anchors locked (Blender)
- [x] 24/36 species are production Blender models
- [~] 3 Epic family extensions modelled + queued for import: Prismaclaw, Sporephant, Fluxaroo (→ 27/36 after import + fit)
- [!] 9 species need owner concept review: Auroroot, ObsidianLynx, Tempestrix, Nucleonox, Biolume, Nullmorph (spec ready); FerriteDrake, Quasipod, Chimerax (new family/mechanic flagged)
- [ ] Geodewisp hood fit fix (the Blender source is centred, so it's a Studio fit issue)

## CREATURE ANIMATION
- [x] Procedural animator: idle/walk/blink/look/wings/orbit/tail/crown, LOD 40/90/cull 140, BulkMoveTo
- [x] Moods: eating, favourite food, acknowledge, sleepy, sample-ready, tired/sad (never angry)
- [ ] Mood review across all 7 families (per-family deviations)

## VARIANTS
- [x] Standard / Luminous (species tint) / Chromatic / Prismatic rendering
- [ ] Luminous tint check for the 17 new roster species in game

## HATCHING
- [x] Physical eggs, odds %, chained locked eggs, tap-to-crack, tiered presentation (glow → shake → shards → flash → pop → reveal)
- [~] Final production timing pass (Normal ~2.5–3 s, Rare ~4–4.5 s, Discovery ~5–6 s), continue action
- [!] Welcome egg (schema v4)

## MUTATION
- [x] Machine → cable → Reactor charge; success / secret double ring / sputter; big reveal
- [~] Final pass: parent clarity, result chamber

## ONBOARDING
- [x] 18-step guide with rewards
- [!] OnboardingV2 reorder (waits on the welcome egg)

## BUILDINGS
- [x] Client-local campus layer: egg dome, mutation tubes + cable, upgrade gantry, supply awning, research hex, showcase dome + live rigs; sign orientation fixed
- [~] Polish review (clipping, readability, occlusion) on 4 viewports

## AUDIO
- [x] 16 hooks + interim engine sounds (tagged)
- [~] Audit done; final asset list written
- [ ] Final licensed/original sounds, ambience, creature voices, music (owner sourcing)

## VFX
- [x] Hatch, mutation, discovery, Luminous sparkle, campus bubbles/gear/flag
- [ ] Feeding / harvest / sample-collect micro VFX

## MOBILE
- [x] ≥12 px text, ≥44 px taps, touch Build Mode (Phase 1)
- [!] Re-check on the 4 viewports after round 2
- [ ] Real-phone session (owner)

## PERFORMANCE
- [x] Creature animation 9–37 µs per creature close; 24 mixed = 0.285 ms/frame
- [x] Campus layer 246 client parts, about 59 fps in Studio Play
- [ ] Low-end phone check

## MULTIPLAYER
- [x] Two-client M1–M9 pass (Finish 3)
- [ ] Re-run after the Phase 2 visuals (client layers per player)

## LIVE SAVE / REJOIN
- [ ] Owner leave/rejoin test on live servers

## MONETIZATION
- [ ] Not started by design (Monetization TODO; owner decision)

## STORE ASSETS
- [ ] Name (still "Untitled Experience"), icon, thumbnails, description

## BETA
- [!] Save to Roblox of the overnight work (Studio needs the auto-recovery restored, then the unlocked screen)
- [ ] Owner reviews of Phase 2 visuals
- [ ] Beta publish (owner approval only)

## LAUNCH
- [ ] Visibility, age rating questionnaire, store assets, final audio, monetization decision

**Estimated beta readiness: ~68%** (2026-10-23).
