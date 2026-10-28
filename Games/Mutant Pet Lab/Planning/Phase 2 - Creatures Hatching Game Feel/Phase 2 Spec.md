---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: hub
status: approved-direction
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - planning
  - phase-2
---
# Phase 2 Spec — Creature + Hatching + Game-Feel Overhaul

> [!danger] OWNER FEEDBACK 2026-10-16 (real-device review) — visual direction correction
> **CURRENT 7 CREATURE PROTOTYPES ARE EXPERIMENTAL AND NOT APPROVED AS THE FINAL CREATURE STYLE.**
> **CURRENT BOTTOM NAVIGATION LAYOUT IS NOT APPROVED.**
> Observed problems: creatures still look like primitive Roblox parts assembled together and not like polished collectible pets; the UI is colourful but bland and developer-like; the large bottom nav takes too much of the phone screen; the HUD is too large; panels read as admin/card lists; the saved references must be used much more strongly.
> The owner wants: stronger simulator-style presentation, better use of the saved references, navigation moved to the sides (no large bottom bar), and creatures that look like actual pets/organisms.
> **Do not build the remaining 29 species. Do not migrate every panel again. Do not publish.** Next step: 3 UI directions + 3 directions each for Frostpup, Mossbit, Sparkbug, then wait for the owner's choice.
>
> **Review ready (2026-10-16):** [[Visual Direction Review 2026-10-16]]: 3 side-rail UI directions (recommended C) + 3 directions each for Frostpup / Mossbit / Sparkbug (recommended C) + [[Creature Face Language]]. Waiting for the owner's selection.
>
> **C1 review stage (2026-10-16):** [[C1 Review Stage 2026-10-16]]: UI-C1 (side rails, status pod, Lab Task Board, Index with 3D previews) and CREATURE-C1 (7 representatives rebuilt). Waiting for owner review; 29 species not built.


> [!success] APPROVED DIRECTION (owner, 2026-10-16) — partly implemented (2026-10-16 overnight: UI revamp, 2A render architecture, 2B 7 prototypes — all Experimental, unsaved to Roblox, not published)
> Binding decisions: the *Phase 2:* entries in [[Design Decisions]]. Where this spec and a decision differ, the decision wins. Implementation follows [[PHASE2_IMPLEMENTATION_PLAN]] after the owner reviews it.
> - Built so far: [[Creature Prototypes]], storyboards [[Hatch Storyboard]] / [[Mutation Storyboard]], exact onboarding moves [[Early Game Reorder]]. Snapshot `2026-10-16_phase2_ui_render_prototypes`.
> - Last build saved to Roblox: Checkpoint C (`2026-10-16_map_overhaul_checkpointC`). The overnight build lives in the open Studio session until saved. **Not published.**
> - Nothing here binds until the owner approves entries in [[Design Decisions]]. The proposals are listed under *Candidates to confirm*.


## Inputs (vault-first)
- **Decisions:** [[Design Decisions]] (cozy bio-lab ranch; lab-skin UI; editable-in-Studio UI; the Mutation Reactor; no monetisation; no creature visual direction approved yet).
- **Research:**
  - [[Roblox Market Research]]
  - [[Egg Hatching Research]], [[Mutation Reveal Research]]
  - [[Creature Presentation Research]], [[Game Feel Research]]
  - [[Early Game Research]], [[Simulator Feature Research]], [[Rare and Secret Content Research]]
  - [[Anti-Patterns]]
- **References:** [[Egg Design and Hatch Anticipation]], [[Rarity Reveal Escalation]], [[Creature Silhouette and Personality]], [[Reward Burst and Wild Encounters]].
- **Current code facts:**
  - Creatures are a 3-part ball (all species identical in shape).
  - Hatch reveal is a 7 s panel; mutation reveal is a panel card.
  - The UI kit sounds are empty.
  - Starting state is 150 Cash / 100 Research; the first recipe costs 25 Research.

## The six specs
1. [[Hatch Presentation Spec]]: hybrid in-world hatch, tiers, camera, timing, VFX, sound, skip, trait/variant order, creature entering the world.
2. [[Mutation Reveal Spec]]: the machine decides, the reactor reveals; cable pulse, charge, result, beacon/sky tint for secrets; failed secret attempt as a "lab note".
3. [[Creature Visual Language Spec]]: 7 body plans + hybrid, proportions, rarity/trait/variant readability, the 30-recipe inheritance table, client display models.
4. [[Creature Animation Spec]]: procedural client-side animation set per body plan, with a budget and LOD.
5. [[Early Game Pacing Spec]]: welcome egg + guaranteed first discovery; first hatch ~2 min, first mutation ~5–8 min.
6. [[Simulator Feature Matrix]]: YES / MAYBE / NO, filtered for fit.

## Recommended build order (if approved)
1. **Foundations:**
   - Fill the UI kit `Sounds` (needs a sourcing decision).
   - Client creature display system with the ball fallback.
   - One shared animation scheduler.
2. **Prototype the 7 body-plan templates** on the starter/early species → **owner look review** (Checkpoint D-1).
3. **Hatch presentation** + creature entering the world.
4. **Mutation reveal** with the reactor.
5. **Early-game pacing** (welcome egg, guide order) + economy re-simulation.
6. **Remaining species templates** by plan; Mythics last.
7. **Checkpoint D (full validation):**
   - Full suite.
   - 4 viewports.
   - Performance on a real phone: frame time with 48 creatures, which can't be judged in throttled Studio.
   - Hatch/mutation flows, frozen check + sight lines unchanged.

## Constraints carried forward
- **Server authority and persistence are unchanged.** Species ids, saved data and tests stay as they are. Presentation is client-only.
- **Object budget:**
  - Static Workspace is 1,949 / ~2,000, so creatures must not add static parts.
  - Display models are client-side and runtime, with LOD and culling.
- **No monetisation, no publish without approval, Studio stays on Mock,** ≤ 3 Studio processes.
- **No MeshParts/imported models by default** (open question below).

## Owner decisions (2026-10-16)
All five questions are answered in [[Design Decisions]]:
1. Parts-based creatures first; Blender only for selected heroes later.
2. Sounds through a review gate.
3. The Machine stays and the Reactor responds.
4. Discovery notices default OFF.
5. Welcome egg approved.

Still **not approved:** trading, gifting, rebirth, new offline features, growth stages, expeditions, bond, weather, wild sightings, seasonal-only secrets, paid speed/luck, auto-hatch, AFK farming.

### Original open questions (answered)
1. **Creature build method:**
   - (A) parts-built stylised creatures, editable in Studio (recommended first), or
   - (B) Blender meshes via [[Asset Pipeline (Blender to Roblox)]] for hero species later.
2. **Sound sourcing:** Roblox Creator Store audio licensed for use, or custom-made. Who picks and approves?
3. **Should the mutation interaction move to the Reactor dais** (a frozen-object change), or stay at the MutationMachine with the reactor responding remotely (the spec default)?
4. **Optional server-wide discovery notices:** on by default (opt-out) or off by default?
5. **Welcome egg guaranteed discovery:** approve the one-time server rule?
