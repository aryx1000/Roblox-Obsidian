---
type: decisions
game: "[[Mutant Pet Lab]]"
status: active
updated: 2026-10-20
source: "owner instructions in Claude sessions"
tags:
  - mutant-pet-lab
  - decisions
---
# Design Decisions

Decisions the owner has **actually approved**. These outrank references, inspiration and Claude's own proposals (see [[Claude Workflow#Authority order]]). Add new entries at the end. Never delete one: when a decision changes, set the old entry to **Superseded**, name its replacement, and add the new entry.

Status values: **Approved** · **Superseded** · **Experimental** (being tried, not final).

> [!note] Visual direction
> Approved 2026-10-15: overall direction, UI skin, editable-in-Studio UI, build placement, build camera, Mutation Reactor landmark and map composition (entries below). **Creature visual direction approved 2026-10-16** (*Phase 2: creature visual language*). References remain guidance unless an entry here makes them binding. **Creature visual direction approved 2026-10-16** (*Phase 2: creature visual language*).

## Vault is the primary project memory

**Status:** Approved

**Decision:** The Obsidian vault is the primary human-readable source of truth for context, decisions, visual references and design intent. Claude reads it first and follows the authority order in [[Claude Workflow]].

**Reason:** Keep decisions and intent stable across sessions instead of re-deriving them.

**References:** [[Claude Workflow]], [[Reference Library]]

**Affected systems:** All

**Date:** 2026-10-15

## Production saving on live servers; Studio always Mock

**Status:** Approved

**Decision:** Live servers save to `MPL_PlayerData_PROD_V1` / scope `Production` / keys `MPL_PROD_V1_<UserId>`. Studio is always forced to the in-memory Mock store. No Studio API access, no reading or editing production player data, no admin grants, no forced migrations.

**Reason:** Protect real player data while allowing safe testing.

**References:** [[PERSISTENCE_ACTIVATION]]

**Affected systems:** [[Persistence]], [[Architecture]]

**Date:** 2026-10-14

## No monetization without explicit approval

**Status:** Approved

**Decision:** No Robux, Developer Products, Game Passes or Marketplace changes unless the owner explicitly approves them.

**Reason:** Owner controls monetization.

**References:** [[Monetization TODO]]

**Affected systems:** [[Economy]]

**Date:** standing rule, recorded by 2026-10-14

## Publishing needs explicit owner approval

**Status:** Approved

**Decision:** Claude never publishes, changes visibility, group roles or Marketplace settings without explicit approval for that publish.

**Reason:** Release safety.

**References:** [[Release and Publish Safety]]

**Affected systems:** Release process

**Date:** standing rule, recorded by 2026-10-14

## Four representative test viewports

**Status:** Approved

**Decision:** UI testing uses only 667×375, 874×402, one tablet and 1366×768; no exhaustive device sweeps.

**Reason:** Exhaustive device testing cost too much time for little gain.

**References:** [[FINISH_3_VALIDATION]], [[Responsive Mobile UI]]

**Affected systems:** [[UI - Figma TODO]], [[QA - Test History]]

**Date:** 2026-10-14

## Studio is the source of truth; at most 3 Studio processes

**Status:** Approved

**Decision:** Roblox Studio is the authoritative working copy (the project folder is a verified export). Never run more than 3 Studio processes (the Edit window counts) without approval; return to one Edit window afterwards.

**Reason:** Machine resources and avoiding conflicting edits.

**References:** [[CLAUDE_PROJECT_STATE]]

**Affected systems:** Workflow

**Date:** recorded by 2026-10-14

## Graphify stays local and code-only

**Status:** Approved

**Decision:** The code graph is built offline (sandboxed, no network), code-only, with no external AI or model integration. No source, vault notes or project files are sent to any external service.

**Reason:** Keep project code and notes on this machine.

**References:** [[Mutant Pet Lab#Code Graph]]

**Affected systems:** Code Graph

**Date:** 2026-10-15

## Overall direction: cozy bio-lab ranch with a mutant-lab identity

**Status:** Approved

**Decision:** The game's look and tone is a **cozy bio-lab ranch**, but **not generic cozy farming**. It must still feel like MUTANT PET LAB: strange biological experiments, research equipment, glowing mutation energy, unusual habitats, a slightly mysterious/scientific tone, and cute creatures living inside that world. The cozy side makes it welcoming; the mutant-lab side makes it distinctive.

**Reason:** Welcoming to new players while staying distinctive.

**References:** Owner approval in chat, 2026-10-15

**Affected systems:** [[UI - Figma TODO]], [[Map Overhaul]], [[Creature Overhaul]]

**Date:** 2026-10-15

## UI skin: friendly research device (lab skin, reference structure)

**Status:** Approved

**Decision:** The interface uses a **lab skin** with the *structure* of the [[Index Collection Screen]] reference: rounded light lab panels, thick dark outlines, chunky readable typography, large visual cards, clear rarity/status colours, a **green → purple mutation accent**, strong silhouette/readability on phones. The UI should feel like a friendly research device. **Not** the warm wooden-cartoon skin as the main UI identity (the world itself may use wood and natural materials). Do not copy the reference literally.

**Reason:** Lab identity; readability on phones.

**References:** [[Index Collection Screen]], [[Shop Storefront Layout]] (layout only)

**Affected systems:** [[UI - Figma TODO]], all client UI

**Date:** 2026-10-15

## UI is editable in Studio (hybrid architecture)

**Status:** Approved

**Decision:** Major screens exist as **editable Roblox UI instances/templates in Studio**: layout, colours, spacing, images, text styles and hierarchy can be changed visually without rewriting Lua. **Static visual structure → editable in Studio; dynamic content → populated by code.** Code supplies data and behaviour and must not procedurally build the whole visual hierarchy each time, except for genuinely repeating/data-driven components. Reusable components are fine. Do **not** rewrite every existing UI in one pass: migrate screens as they are redesigned.

**Reason:** Owner wants to adjust UI visually in Studio.

**References:** Owner comment on [[These are some cool UI referenses]]; confirmed in chat 2026-10-15

**Affected systems:** [[UI - Figma TODO]], [[Architecture#Client controllers]]

**Date:** 2026-10-15

## Touch build placement: drag → release → confirm

**Status:** Approved

**Decision:** On touch: choose a structure → drag the ghost directly around the plot → release → the preview **stays where released** → show **ROTATE / PLACE / CANCEL**; **PLACE** sends the actual request. **Never place automatically on finger release.** The preview sits slightly offset from the finger so it stays visible. The current arrow-button placement is to be **removed** from the touch flow. Server validation stays authoritative.

**Reason:** Safer; avoids accidental purchases/placements.

**References:** Owner approval in chat, 2026-10-15

**Affected systems:** Build Mode (`PropertyController`), [[Economy]]

**Date:** 2026-10-15

## Build camera: smooth angled overhead

**Status:** Superseded in part 2026-10-21 (camera is now fixed, Bloxburg-style; see *Build Mode: compact strip, snap grid, fixed camera*)

**Decision:** Build Mode uses an **angled overhead camera** reached by a **smooth transition** (no teleport into a different-feeling game). The player sees most of the usable property, the camera stays connected to their plot, touch dragging is easy, zoom limits suit phones, and exiting Build Mode smoothly restores the normal camera. Mild orbit/zoom while building if practical.

**Reason:** Placement needs a clear view without breaking immersion.

**References:** Owner approval in chat, 2026-10-15

**Affected systems:** Build Mode

**Date:** 2026-10-15

## Map landmark: the Mutation Reactor

**Status:** Approved

**Decision:** The central landmark is a **Mutation Reactor** (not a giant incubator): the visual symbol of MUTANT PET LAB. Visible from every property, glowing green/purple energy, chunky readable silhouette, pipes/tanks/research machinery around its base, animated energy core later; the central campus is built around it. It must **not** be so large that it obstructs the map.

**Reason:** Mutation is the game's identity; incubation is one subsystem.

**References:** Owner approval in chat, 2026-10-15

**Affected systems:** [[Map Overhaul]], [[Mutation Recipes]]

**Date:** 2026-10-15

## Map composition: research ranch in a mutant valley, not flat

**Status:** Approved

**Decision:** The map overhaul must change the **composition**, not just add props: elevation differences, terraces, slopes, raised/lowered campus sections, rock formations, vegetation masses, retaining structures, better sight lines, terrain surrounding plots. Player build areas stay **usable and predictable**. Goal: *a research ranch built into an interesting mutant valley*, not *flat grass with more decorations*.

**Reason:** The current map feels too flat.

**References:** Owner approval in chat, 2026-10-15

**Affected systems:** [[Map Overhaul]]

**Date:** 2026-10-15

## Validation: targeted during work, full at checkpoints

**Status:** Approved

**Decision:** During implementation use **targeted validation** for the change at hand (e.g. UI kit → affected viewport(s) + behaviour; Build Mode → phone + desktop placement, server validation, persistence once; map → plots/stations/bounds unchanged + performance sanity). Run the **full set only at checkpoints**: **A** (UI kit + Build Mode): full suite, 4 viewports, placement persistence, targeted multiplayer placement. **B** (HUD + Index): full suite only if code behaviour changed, 4 viewports, affected flows. **C** (map): full suite, 4 viewports, plot/bounds/station validation, 2-player spot check, performance benchmark, save/rejoin sanity. Representative viewports only (see *Four representative test viewports*); minor cosmetic differences belong to final polish.

**Reason:** Full validation after every small step wastes development time.

**References:** Owner approval in chat, 2026-10-15

**Affected systems:** [[QA - Test History]], all Phase 1 work

**Date:** 2026-10-15

## Phase 1 scope and order

**Status:** Approved

**Decision:** Phase 1 order: **A** record decisions → **B** shared editable-in-Studio UI kit → **C** Build Mode drag-to-place → **D** HUD simplification → **E** Index redesign → **F** map/environment (terrain/elevation, Mutation Reactor, campus plaza, paths, plot surroundings, biome edges, lighting). **Not** the creature model overhaul yet. Improve interaction feel where natural (placement feedback, transitions, clearer discoveries, less menu friction, more world visibility, stronger landmark) but **no large new gameplay systems** — the deeper gameplay/game-feel overhaul comes after the UI/map foundation.

**Reason:** Owner feedback: gameplay currently feels boring; build the foundation first.

**References:** Owner approval in chat, 2026-10-15

**Affected systems:** [[Roadmap]]

**Date:** 2026-10-15

## Map: parts-based environment (no Terrain this phase)

**Status:** Approved

**Decision:** Build the environment overhaul with **Parts/WedgeParts/CornerWedgeParts** (and static Unions where useful), **not Roblox Terrain**, for this phase. Terrain can be reconsidered later.

**Reason:** Easier to version, restore, compare against snapshots and audit for plot/build-area safety (the backup pipeline captures parts, not voxels).

**References:** [[MAP_OVERHAUL_PLAN]]

**Affected systems:** [[Map Overhaul]]

**Date:** 2026-10-15

## Map: Research Terminal moves to the Mutation Reactor

**Status:** Approved

**Decision:** Move the Research Terminal from the exact campus centre to the **front of the Mutation Reactor**. Preserve all interaction/range logic and server authority (the prompt keeps its name; research stays server-validated).

**Reason:** The reactor is the heart of the research campus, so Research belongs there.

**References:** [[MAP_OVERHAUL_PLAN]]

**Affected systems:** [[Research Tree]], [[Map Overhaul]]

**Date:** 2026-10-15

## Map: one habitat biome per plot gap, organic transitions

**Status:** Approved

**Decision:** Keep the gameplay mapping one-to-one (Botanical 01–02, Humid wetlands 02–03, Conductive 03–04, Thermal vents 04–05, Unstable rift 05–06, Cryogenic shelf 06–07, Geological spires 07–08, Experimental 08–01), but **do not** make 8 equal theme-park wedges: uneven boundaries, overlapping vegetation, rocks/retaining walls, terrain blending and soft transitions between neighbouring habitats.

**Reason:** Teach habitats visually while keeping the valley natural.

**References:** [[MAP_OVERHAUL_PLAN]]

**Affected systems:** [[Map Overhaul]], [[Species]]

**Date:** 2026-10-15

## Map: CreatureDisplayArea becomes the Specimen Showcase

**Status:** Approved

**Decision:** **Do not retire** `CreatureDisplayArea`. Preserve it and visually integrate it into the new campus as the **Specimen Showcase / Discovery Display** — a place for rare, featured or recently discovered creatures. **No new gameplay logic yet.**

**Reason:** Supports clearer discoveries later without new systems now.

**References:** [[MAP_OVERHAUL_PLAN]]

**Affected systems:** [[Map Overhaul]], [[Mutation Recipes]]

**Date:** 2026-10-15

## Map: Baseplate retirement is conditional

**Status:** Approved

**Decision:** Retire `Workspace/Baseplate` **only after Studio confirms**: it is not needed for world support, no script references it, removing it creates no holes or falling-through, and SpawnLocation plus all plot/build surfaces remain valid. **If any doubt remains, leave it in place, hidden and non-interactive.**

**Reason:** Avoid invisible world-support regressions.

**References:** [[MAP_STUDIO_CHECKLIST]]

**Affected systems:** [[Map Overhaul]]

**Date:** 2026-10-15

## Map: Mutation Reactor approved as the central landmark

**Status:** Approved

**Decision:** Approved: green-to-purple mutation core, chunky readable silhouette, visible from all 8 plots, pipes/tanks/catwalks, research equipment around the base, **not so tall or wide that it dominates the world** (planned core y 50, crown y 56, 32-stud dais). Later animation/VFX may make the core pulse/react.

**Reason:** Mutation is the game's identity (see *Map landmark: the Mutation Reactor*).

**References:** [[MAP_OVERHAUL_PLAN]]

**Affected systems:** [[Map Overhaul]]

**Date:** 2026-10-15

## Map: performance and frozen-geometry constraints

**Status:** Approved

**Decision:** Stay near the current object count with a **hard target below ~2,000 Workspace objects** this phase; **no imported 3D models**; decorative geometry anchored; collision/touch/query off where not needed; limited lights; keep the phone-performance target. **Unchanged:** plot origins, plot bounds, expansion land, station interaction positions (except the approved Research Terminal move) and saved placement coordinates.

**Reason:** Phone performance and player-save safety.

**References:** [[MAP_STUDIO_CHECKLIST]]

**Affected systems:** [[Map Overhaul]], [[Persistence]]

**Date:** 2026-10-15

## Map overhaul plan approved (Studio work gated)

**Status:** Approved

**Decision:** The map overhaul plan ([[MAP_OVERHAUL_PLAN]]) is approved with the decisions above. Goal remains *a research ranch built into an interesting mutant valley*, not flat grass with more decorations. **Nothing is applied in Studio until the Mac is unlocked and the owner explicitly says to proceed.**

**Reason:** Owner approval, 2026-10-15.

**References:** [[MAP_STUDIO_CHECKLIST]]

**Affected systems:** [[Map Overhaul]], [[Roadmap]]

**Date:** 2026-10-15

## Map overhaul implementation (approved implementation notes)

**Status:** Approved (owner, 2026-10-16). Previously recorded as Experimental after Checkpoint C.

**Decision:** The map overhaul as built in Checkpoint C is approved, including these implementation adjustments to the approved plan:
1. **Round reactor base:** cylinder tiers, not an octagon.
2. **Two outer terrace tiers instead of three:** the existing ValleyRim forms the top step. This keeps the map under the ~2,000-object budget.
3. **Commons berms beside the lanes,** not a ring: radial ridges at r ~135–185, one per gap, alternating sides. Wetland pools sit at r 117–183 and plot front fences at r ≈ 200.
4. **Plot surround walls slightly farther out:** local |X| 80–83, Z 110–113, past the plot fences at |X| 74.5.
5. **Centred biome ridges** on each gap axis. Organic variety comes from lengths, heights, props and seam rocks.
6. **Lighting `Technology` left unchanged.** MCP cannot read or set it.
7. **Wetland basin not lowered.**
8. **Reactor partly hidden from two counters:** the Supply and Upgrades counters sit inside south-facing buildings, but the reactor is visible from the plaza.
9. **Two-player map spot-check skipped.** No multiplayer or gameplay-authority code changed.

Also part of the applied build:
- The Research Terminal sits at (0, 3, 21).
- The Baseplate was retired to `ServerStorage/MapOverhaul_Backup` after every approved condition passed.
- Pedestal rings in CreatureDisplayArea use rarity colours (visual only).

**Reason:** Real Studio constraints and the object budget. The approved map decisions are unchanged.

**References:** [[Map Overhaul#Applied 2026-10-16]], [[MAP_OVERHAUL_PLAN]]

**Affected systems:** [[Map Overhaul]]

**Date:** 2026-10-16 (applied and approved)

**Build status:** The saved Checkpoint C build (`2026-10-16_map_overhaul_checkpointC`) is the current development build. **Not published.**

## Phase 2: creature build method — part-based Studio models first

**Status:** Approved

**Decision:** Build all 36 creature visuals as **lightweight, part-based Roblox Studio models**, editable in Studio. They use **reusable body-plan components** where appropriate, have **distinct silhouettes**, and keep each species' identity. **No dependency on external Blender assets** for the initial overhaul. Selected hero species may later be upgraded to Blender meshes if parts can't reach the desired quality. Never make all 36 depend on Blender before the game can move forward.

**Reason:** Fast iteration in Studio; consistent with the parts-based map and the editable-in-Studio principle.

**References:** [[Phase 2 Spec]], [[Creature Visual Language Spec]]

**Affected systems:** [[Creature Overhaul]], [[Species]]

**Date:** 2026-10-16

## Phase 2: sound sourcing — with owner review gate

**Status:** Approved

**Decision:** Sounds may come from **Roblox Creator Store audio or custom audio**. **No sound is installed automatically.** Candidate sounds are **recorded first** (name, asset id/source, licence, intended slot), and the **owner approves the final choices before they become binding**. No copyrighted music or effects from external games. Audio stays **coherent** across UI, hatch, mutation and discovery moments.

**Reason:** Quality and licensing control.

**References:** [[Phase 2 Spec]], [[Hatch Presentation Spec#Sound]]

**Affected systems:** UI kit `Sounds`, hatch, mutation, discovery

**Date:** 2026-10-16

## Phase 2: mutation interaction stays at the Mutation Machine; Reactor responds

**Status:** Approved

**Decision:** The mutation interaction **stays at the existing Mutation Machine**. The central Mutation Reactor **responds**: Mutation Machine → cable/energy pulse → Reactor reacts → result reveal. The station does **not** move to the Reactor in this phase.

**Reason:** Keeps existing gameplay, frozen prompts and server logic, while making the map feel connected.

**References:** [[Mutation Reveal Spec]]

**Affected systems:** Mutation Lab (`BreedingController`), [[Map Overhaul|Mutation Reactor]]

**Date:** 2026-10-16

## Phase 2: discovery notices default OFF

**Status:** Approved

**Decision:** **No server-wide discovery announcements by default.** Prepare the system so it can later become **optional, configurable, and limited to very rare/secret discoveries**. No noisy global notices during the initial overhaul.

**Reason:** Avoid noise; keep the option for later.

**References:** [[Mutation Reveal Spec]]

**Affected systems:** Mutation reveal, discovery feedback

**Date:** 2026-10-16

## Phase 2: welcome egg

**Status:** Approved

**Decision:** New players receive a **one-time Field egg tied to onboarding**. The first hatch happens within the first few minutes, and it is **guaranteed to be a species the player hasn't discovered**, drawn from the existing early-game pool. No premium requirement. Rewarded **only once**. **Fully persisted and server-authoritative.** Re-run the progression/economy tests when implemented.

**Reason:** The signature payoff arrives early.

**References:** [[Early Game Pacing Spec]]

**Affected systems:** [[Economy]], [[Egg Families]], onboarding, [[Persistence]]

**Date:** 2026-10-16

## Phase 2: hybrid in-world hatch presentation

**Status:** Approved

**Decision:** Use the **hybrid in-world hatch**:

| Tier | What happens | Duration |
|---|---|---|
| **Normal** | incubator shakes/glows, short crack/reveal, species appears in-world, brief result card | ~3 s |
| **Rare** | stronger glow, rarity-coloured beam/effect, stronger sound | ~4–5 s |
| **First discovery** | silhouette beat, reveal, NEW SPECIES / NEW DISCOVERY moment, Index update | ~5–6 s |
| **Secret / extreme** | strongest effect; the Reactor may react if appropriate; stronger audio/lighting; only for genuinely exceptional discoveries | — |

**Reveal order:** Species → Rarity → Trait → Variant. Repeated/common hatches use a **shorter version**. **Skipping is allowed** and must cancel and clean up local VFX/audio safely.

**Reason:** Approved direction from the Phase 2 design pass.

**References:** [[Hatch Presentation Spec]]

**Affected systems:** `PropertyController` hatch reveal, incubators

**Date:** 2026-10-16

## Phase 2: creature entering the world

**Status:** Approved

**Decision:** After a hatch the creature appears **physically near the incubator**, **acknowledges the player**, and **walks cosmetically** toward its pen or holding area where practical. **Presentation only:** server authority and assignment rules don't change.

**Reason:** Pet, not inventory line.

**References:** [[Hatch Presentation Spec#Creature entering the world]]

**Affected systems:** Hatch flow, pens

**Date:** 2026-10-16

## Phase 2: creature visual language (first approved creature direction)

**Status:** Approved

**Decision:** Core rule: **a species is identifiable from its silhouette before reading its name.** Use distinct body shapes, readable proportions, **large expressive eyes**, **one strong mutant accent**, one signature glowing/biological feature where appropriate, **family resemblance** for related creatures, and mutation offspring that **visibly inherit meaningful traits from both parents**. **Colour/material alone must NOT define species identity.**

**Reason:** The biggest gap versus successful creature games.

**References:** [[Creature Visual Language Spec]], [[Creature Silhouette and Personality]]

**Affected systems:** [[Creature Overhaul]], [[Species]], [[Mutation Recipes]]

**Date:** 2026-10-16

## Phase 2: rarity, variant and trait readability

**Status:** Approved

**Decision:** **Rarity** reads through multiple channels: silhouette/detail, subtle scale/detail escalation, a world indicator, and the nameplate/UI. **Variants are visible everywhere the creature is shown:** pens, hatch reveal, showcase, creature detail, mutation result. **Traits** have a UI icon and an occasional behaviour cue where appropriate. **Don't overdo constant particle effects.**

**Reason:** Readable status without clutter.

**References:** [[Creature Visual Language Spec#Rarity readability]]

**Affected systems:** [[Traits and Variants]], nameplates, Index, showcase

**Date:** 2026-10-16

## Phase 2: client display model architecture

**Status:** Approved

**Decision:** Keep the authoritative server creature logic simple. **Clients render the higher-detail creature locally from editable Studio templates.** **Fallback:** if a template is missing, use the current simple creature. Requirements: the **server owns identity/state**; the **client can't choose species/trait/variant**; the visual layer is **cosmetic**; distance culling; an animation budget; mobile-safe.

**Reason:** Detail without server cost or trust risk.

**References:** [[Creature Visual Language Spec#Technical approach (proposal)]]

**Affected systems:** `PropertyVisuals`, new client creature renderer

**Date:** 2026-10-16

## Phase 2: procedural client-side animation

**Status:** Approved

**Decision:** Initial set: **idle, walk/run, blink/look, investigate, eat, sleep, social reaction, hatch emergence, mutation reaction**. Client-side procedural animation first. **No 36 separate uploaded animation sets.**

**Reason:** Works with part-based models at low cost.

**References:** [[Creature Animation Spec]]

**Affected systems:** New client animation scheduler

**Date:** 2026-10-16

## Phase 2: early-game pacing direction

**Status:** Approved

**Decision:** Targets: property/starter interaction immediately, the first egg early, the **first hatch in the first few minutes**, an early first discovery, and the **first mutation around 5–8 minutes**. Don't delay the core fantasy behind every supporting system.

**Reason:** Market research: the signature verb belongs in the first minutes.

**References:** [[Early Game Pacing Spec]], [[Early Game Research]]

**Affected systems:** `OnboardingConfig`, onboarding, [[Economy]]

**Date:** 2026-10-16

## Phase 2: explicitly NOT approved (later / separate decisions)

**Status:** Approved

**Decision:** Not approved automatically, and needing separate owner decisions:
- Trading, gifting, rebirth.
- **New** offline-progression features (the existing offline incubation stays as it is).
- Growth stages, expeditions, the bond system.
- Weather events, wild specimen sightings, seasonal-only secrets.
- Paid hatch speed, luck boosts, auto-hatch, AFK farming.

**Reason:** Avoid generic simulator bloat and pay-to-win.

**References:** [[Simulator Feature Matrix]], [[Anti-Patterns]]

**Affected systems:** —

**Date:** 2026-10-16

## Visual direction APPROVED: UI Direction C, side rails, status-pod HUD, C creature language (owner, 2026-10-16)
**Status:** Approved
**Date:** 2026-10-16
**Source:** owner messages after [[Visual Direction Review 2026-10-16]] ("VISUAL DIRECTION APPROVED" + creature selections)
**Decision:**
- **UI = Direction C (Balanced)** is the primary UI language:
  - chunky simulator readability, a dark bio-lab rail/dock structure, strong framed panels with depth;
  - overlapping title plates, a strong X, gold/select accents, mint/light inner content areas;
  - rarity-framed cards, icon-first navigation, minimal copy;
  - one focal element per screen; each screen keeps its own purpose and composition (no identical recoloured layouts).
  - **Never revert to:** flat white admin panels, giant coloured rectangles, permanent bottom navigation, text-row walls.
- **Navigation = side rails.** The large bottom nav is removed from production.
  - Left rail: Build, My Lab, Creatures, Index. Right rail: Goals, Ranch, Home + one contextual/notification slot.
  - Rails stay clear of the thumbstick/jump zones and collapse when a large panel opens.
  - Badges supported; a strong selected state.
  - Icons on phones, labels allowed on tablet/desktop. One system for every device.
- **HUD = compact status pod** (about 222×46 design px): Level, XP, Cash, Research. Readable phone text, strong currency icons, progression feedback.
- **Goals = Lab Task Board.** The same panel language applies to Index, Egg Shop, Mutation Lab, Creatures, Research, Ranch and My Lab.
- **Creature style rule (LOCKED): "Cute collectible organism first, mutant biology second."**
  - Direction C is the base. From A: blush, paw pads, softer/chunkier proportions. From B: growths, crystals and segmentation, mainly for higher rarity, mutations and elemental specialisation.
  - Never: glow everywhere, the same eyes, the same body, the same proportions, a sphere with accessories.
- **Approved creature-direction references:**
  - **Frostpup:** the LEFT (A) prototype is the production base, a chunky quadruped. Refinements:
    - a cleaner muzzle, softer paws, canine (not rabbit) ears;
    - head/back ice reads as icy fur/crystals rather than spikes;
    - C-style iris eyes;
    - B-style crystals only as restrained rarity/mutation detail.
    - Not the thin middle body, not the upright right body. *(Interpretation: the owner's explicit selection, LEFT base, wins over the general "Frostpup base C" line; C's face language is applied to it.)*
  - **Mossbit:** the RIGHT (C) prototype is the base. Softer/chunkier root feet; keep the leaf hood and the flower bud; never a humanoid plant NPC.
  - **Sparkbug:** the RIGHT (C) prototype is the base. Slightly larger, more readable wings; clearer abdomen segmentation; a cute face; not as realistic as B.
- **Face language approved** ([[Creature Face Language]]): neutral, happy, curious, sleepy and low-wellbeing expressions.
  - Low wellbeing reads **sad/tired, not angry**.
  - Curious adds a **head tilt/asymmetry**.
  - Eye shapes vary by species/family: round, oval, narrower, different iris proportions. Tiny dot eyes are never the default.
- **Glow rule:** no whole-body glow. Matte, soft surfaces; Neon only for mutant organs, elemental accents, rare biological features and mutation detail.
- **Display scale:** test +10–20% visual-only scale for the smallest species. Gameplay and collision authority are unchanged.
- **Part budget (production):**
  - Normal creature: about 18–30 visible parts. Higher-rarity/complex creatures may exceed that when justified.
  - Distance LOD: close = full detail; medium = drop tiny face/accessory parts; far = simplified; culled past the existing threshold.
  - Keep the 24-animated cap unless profiling supports more. Never ruin a silhouette to hit a number.
- **Blender/MeshPart:** not required now. Flag anatomy that parts can't bring to the quality bar (likely the Frostpup fur contour, complex insects, hero Legendary/Mythic creatures).
- **Order:** UI-C1 (rails + HUD, then Goals and Index; validate before other screens) → CREATURE-C1 (rebuild the 7 body-plan prototypes, then a review stage). **No other species before another review. Never publish.**
- **Preserved:** persistence, DataStore config, economy, recipes, egg odds, server ownership, ranch authority, map geometry, Build Mode.
**Supersedes:** [[#Phase 2 correction: visual direction reset (owner, real-device review)]] (it is fulfilled); the Phase 1 "7-tile nav bar" HUD; the overnight per-screen-accent candidates where they conflict.

## Phase 2 correction: visual direction reset (owner, real-device review)
**Status:** Approved (owner instruction)
**Date:** 2026-10-16
**Decision:**
- The 7 overnight creature prototypes are **experimental architecture tests, NOT the final creature style.** Do not scale them to 36 species.
- The **large 7-button bottom navigation is NOT approved** as the final direction. Navigation moves to **side rails** (left: Build, My Lab, Creatures, Index; right/context: Goals, Ranch, Home, notifications — grouping can be refined). Compact, icon-first, thumb-reachable, clear of Roblox controls, collapses when a modal opens, strong selected state, badge support. One architecture across devices (desktop/tablet may expand the rails).
- The **HUD must shrink** (compact level, compact XP bar, smaller Cash/Research pills, less padding, stronger icons) without losing readability.
- **Panels must stop looking like admin card lists:** layered panels, strong title shapes, depth, careful gradients, icon tabs, rarity-framed cards, illustrations/silhouettes, less text, strong focal actions, playful shapes. Goals becomes a mission journal / lab-task board.
- **Creatures must look like pets/organisms,** not assembled primitives: real anatomy (head, body, limbs, paws, tail, ears/fins/wings/leaves/shells, facial structure), expressive faces. Parts are still allowed if the construction is disguised; species that can't reach pet quality with parts are flagged for a later MeshPart/Blender model.
- **Glow is a special mutant accent,** not the creature. Mostly soft matte materials; Neon reserved for mutations, organs, rare features and energy.
- **Rarity adds silhouette/anatomy detail, accent features and subtle high-tier VFX,** not "the same creature but brighter". Commons must still look polished.
- **Process:** first 3 UI directions (clean lab / playful cartoon / balanced) as editable Studio mockups and 3 directions each for Frostpup, Mossbit and Sparkbug; then STOP for the owner's selection. Backend, persistence, security, server calls and Build Mode behaviour are preserved.
- Test only the 4 viewports (667×375, ~874×402, one tablet, 1366×768). Never publish.
**Supersedes:** the "UI screen identity / NEW badges / 7 prototype looks / part budget" items in *Phase 2 overnight candidates* below (still candidates, now explicitly not final), and the bottom-bar part of the approved Phase 1 HUD ("7-tile nav bar").
**Source:** owner message 2026-10-16 ("VISUAL DIRECTION CORRECTION PASS").

## Negative visual rules (owner, 2026-10-20)
**Status:** Approved
**Date:** 2026-10-20
**Source:** owner message 2026-10-20 (resolving the offline-pass questions)
**Decision:** MPL must never use:
- blocky / prototype-looking **final** art;
- giant flat coloured UI rectangles;
- excessive neon;
- a generic sci-fi lab look;
- gritty realism;
- an overly babyish / toddler aesthetic;
- a permanently cluttered HUD;
- identical face / body language across all creatures;
- recolour-only species;
- repeated booth-shaped buildings;
- "polish" that is only gradients / colours;
- a close copy of any single Roblox game's art or UI identity.

Full list with sources: [[Do Not Copy]].
**Affected systems:** all player-facing art, UI, buildings, creatures

## Creature template sheets required before production (owner, 2026-10-20)
**Status:** Approved
**Date:** 2026-10-20
**Decision:**
- **Every final creature gets a specimen / template sheet before production.** The owner's R15/R16 format is the default template language ([[Creature Template Sheets]]).
- **Minimum content:** front · side · back · silhouette · expression · materials · mutant feature · glow/accent location · rarity differences · mutation lineage / inheritance notes.
- **Do not build the full production creature until its sheet is approved**, or the build is clearly marked **Experimental**.
**Resolves:** candidates C-R10, C-R12.

## Faceted finish: selective, not universal (owner, 2026-10-20)
**Status:** Approved
**Date:** 2026-10-20
**Decision:**
- Use the faceted / low-poly crystal treatment **where the material calls for it:** frost, crystal, geological, prismatic, and selected Legendary/Mythic designs.
- **Do not apply it automatically to** soft mammals, plants, gels/slimes or fluffy creatures.
- The build method per species is chosen on its template sheet; parts-first remains the default, and Blender stays reserved for flagged anatomy and heroes.
**Resolves:** candidate C-R11 (as selective). Inspiration C-S8 stays inspiration.

## Building budget: Route B (owner, 2026-10-20)
**Status:** Approved
**Date:** 2026-10-20
**Decision:**
- **Server / shared geometry** for gameplay-relevant architecture (silhouettes, floors, interaction points, anything collidable or shared).
- **Client-local visual detail** for decorative, non-interactive polish where appropriate (spawned from templates, distance-culled, like the creature display layer).
- **Do not raise the global part budget casually** (the ~2,000 Workspace cap stands).
**Resolves:** candidate C-B1 (route B). [[Building Art Direction]]

## Egg interaction (owner, 2026-10-20)
**Status:** Approved (Open ×3 stays Candidate)
**Date:** 2026-10-20
**Decision:** Approved:
- **physical egg displays**;
- **tap-to-crack** (inside the approved hybrid hatch; it still must not block play);
- the **odds popup** at the egg;
- the **percentage chance display**;
- **locked eggs visually chained / dark**;
- **rarity-scaled hatch presentation**.

**Not approved yet:** Open ×3 / multi-hatch. **Build the single-hatch experience first.** Auto-hatch, paid hatch, luck and speed boosts stay not approved.
**Note:** the % display supersedes the "never show 1 in N" line in [[Hatch Presentation Spec]] for the odds popup and the hatch card; the escalation itself is still carried by light, colour and space.
**Resolves:** C-R3, C-R6, C-R7, C-E1 (except the egg rack, still candidate), and C-R4 minus ×3. [[Physical Egg Interaction]]

## Care state exposed read-only to clients (owner, 2026-10-20)
**Status:** Approved
**Date:** 2026-10-20
**Decision:**
- The server exposes the **minimum authoritative care state** to clients as **read-only display data**. Possible values: wellbeing, hunger / feed state, favourite-food success, habitat satisfaction, sleep / rest, and sample readiness where useful.
- Client visual systems may react to these values.
- **Clients may NOT calculate, override or author care state.** The ranch simulation stays server-authoritative.
**Resolves:** candidate C-L1. [[Creature World Interaction]]

## Decorations: future design direction (owner, 2026-10-20)
**Status:** Approved as direction (not scheduled)
**Date:** 2026-10-20
**Decision:**
- Buildable decoration categories to plan for: paths, lamps, planters, signs, benches, lab props, habitat decorations.
- **Not in the next immediate checkpoint.**
- **Functional structures and decorative structures stay conceptually separate.**
**Partly resolves:** C-P1 (decorations). Visiting presentation and likes stay candidate. [[Plot Decoration and Visiting]]

## Welcome hatch happens on the player's own property (owner, 2026-10-20)
**Status:** Approved
**Date:** 2026-10-20
**Decision:** Target first-session flow:
1. The welcome egg appears in, or is delivered to, the **starter incubator**.
2. The player interacts with it **on their own plot**.
3. Tap / crack sequence.
4. First-discovery reveal.
5. The creature appears physically near the incubator.
6. The creature acknowledges the player.
7. The creature moves toward the starter pen / holding area.

The Egg Research Center **teaches and sells later eggs**; the first hatch should feel personal.
**Refines:** *Phase 2: welcome egg*. Drops the "hatchery stage" exception in [[Egg Research Center Redesign]].

## Radiant stays a trait (owner, 2026-10-20)
**Status:** Approved
**Date:** 2026-10-20
**Decision:** **Radiant is a TRAIT, not a variant.** Do not convert it. Variants remain Standard / Luminous / Chromatic / Prismatic.

## R14 trail shop stays needs-review (owner, 2026-10-20)
**Status:** Approved (process)
**Date:** 2026-10-20
**Decision:** Keep R14 as **needs-review**. Claude must **not infer** what the owner liked about it.

## Candidates to confirm (not approved decisions)

These were decided during Claude-run checkpoints. They are recorded in project docs but the owner has not explicitly approved them as lasting design decisions. Treat as **current state**, not hard requirements, until confirmed here.
- **Reference-library + similar-game candidates (2026-10-20, Claude, NOT approved)**. **Resolved by the owner on 2026-10-20:** C-R3, C-R6, C-R7, C-R10, C-R11 (selective), C-R12, C-B1 (route B), C-E1, C-L1 → approved entries above; C-R4 approved except Open ×3 (still candidate); C-P1 decorations approved as a future direction only. The rest stay candidates. Sources: [[Owner Reference Library]], [[Similar Games Overview]].
  - **C-R1 Index family pages + completion rewards** (CLAIM per egg family when every species in it is discovered). Owner R1.
  - ~~**C-R2**~~ → **Approved 2026-10-21 (owner request in chat): snap grid with 4 sizes (1/2/4/8 studs), rotate / cancel / confirm, compact bottom strip.** Undo not requested yet. See *Build Mode: compact strip, snap grid, fixed camera*. Owner R3.
  - ~~**C-R3**~~ → **Approved 2026-10-20.** **Tap-to-crack beat** in the approved hybrid hatch (the egg waits for a tap, auto-cracks after ~2 s; never blocks). Owner R4.
  - **C-R4** → odds popup **approved 2026-10-20**; **Open ×3 still candidate.** **Proximity egg odds card at each physical egg + Open ×1 / ×3** (×3 multi-open is new; auto-hatch stays not approved). Owner R5/R6.
  - **C-R5 Research (and/or lab upgrades) as a hex board** (adjacency = prerequisite, locked = dark "???" hex). Owner R7. Layout only: paid speed/luck nodes stay banned.
  - ~~**C-R6**~~ → **Approved 2026-10-20.** **Physical egg display in the Egg Facility** (all six family eggs on pedestals; locked = dark + chained + "🔒 Lv N"). Owner R8.
  - ~~**C-R7**~~ → **Approved 2026-10-20** (% chance shown). **Hatch stat card + darkened backdrop for high tiers**; open question: show the "% chance" on the card or not (the current spec says no). Owner R9.
  - **C-R8 Rarity-tiered egg design language** (top families get a cage / halo / wings / orbit rings / altar). Owner R10.
  - **C-R9 Creature viewer** in the Index/Creatures detail (turntable + Idle / Move / Action tabs). Owner R11/R13.
  - ~~**C-R10**~~ → **Approved 2026-10-20.** **Creature Template Sheet per species + silhouette check** (front/side/back/top/¾, parts with Roles, face + expressions, palette, rarity add-ons, scale vs avatar) as a production step before building any species. Owner R12: **"you should do the same"**, so this is **likely approved; please confirm**.
  - **C-S1 Visible care reactions** (eat, happy, sleep, sad) using the approved face language. Adopt Me, Slime Rancher.
  - **C-S2 Bio-assay samples drop as physical vials in the pen** before collection. Slime Rancher plorts.
  - **C-S3 Plot visiting with likes/ratings + a plot decoration layer.** MSM, Grow a Garden, Adopt Me (MPL's weakest dimension).
  - **C-S4 Stronger variant readability** (Luminous / Chromatic / Prismatic currently subtle). Adopt Me Neon, Build a Zoo mutations.
  - **C-S5 Species-themed pen props / habitat preference reactions.** DragonVale, Viva Piñata.
  - **C-S6 "Favourite creature follows you"** (cosmetic). Adopt Me, Bee Swarm.
  - **C-S7 Ambient creature sounds** so a full ranch sounds alive (through the approved sound review gate). My Singing Monsters.
  - **C-S8 Voxel/faceted finish as an optional material route** to hide part construction. Build a Zoo, Raise Animals 2 (inspiration only; the C creature language stays approved).
  - **C-S9 Name-collision check** before choosing MPL's public title: a Roblox game named "🧬 MUTANT HATCHERY!" exists.
  - ~~**C-R11**~~ → **Approved 2026-10-20 as selective** (frost/crystal/geological/prismatic/selected heroes). **Faceted / low-poly creature finish** (crystal-faceted surfaces like owner R16; R11, R10 support it). Test on Frostpup (Blender flat-shaded MeshPart vs wedges) before choosing the finish for all 36. Would widen the approved "parts first, Blender for heroes" method.
  - ~~**C-R12**~~ → **Approved 2026-10-20.** **Owner blueprint = the standard Creature Specimen File** (R15) with 3 additions (5th face slot, mutant-feature line, silhouette check). Strengthens C-R10.
  - ~~**C-B1**~~ → **Route B approved 2026-10-20.** **Building budget route:** (A) rebuild inside the ~2,000 Workspace cap (1,947 used), (B) client-side decorative detail layer (recommended), or (C) raise the cap / allow MeshParts for hero buildings. Blocks any building art pass. [[Building Art Direction]]
  - **C-B2 Building art direction + Egg Research Center redesign** (egg-dome hatchery greenhouse). [[Building Art Direction]], [[Egg Research Center Redesign]]
  - ~~**C-E1**~~ → **Approved 2026-10-20** (egg rack still candidate). **Physical egg flow** (egg family looks, chained locked eggs, proximity odds cards, egg rack, tap-to-crack with a 2 s auto-crack). [[Physical Egg Interaction]]
  - ~~**C-L1**~~ → **Read-only care state approved 2026-10-20** (behaviours themselves still candidate). **Creature-life behaviours + read-only display attributes** (Wellbeing, LastMealAt, SamplesReady, HabitatMatch). [[Creature World Interaction]]
  - **C-V1 Variant visual language** (finish + small anatomy accent per variant). Radiant stays a trait (**approved 2026-10-20**). [[Variant Visual Language]]
  - **C-P1** → decorations **approved as a future direction 2026-10-20**; visiting presentation + likes still candidate. **Visiting presentation + decoration categories** (gate banner, read-only viewer, likes candidate, species statues). [[Plot Decoration and Visiting]]
- **UI toolkit candidate (2026-10-20, Claude, NOT approved).** Source: [[Figma to Roblox UI (ui-figma-roblox skill)]].
  - **C-U1 Selective stud/halftone texture + Kek-style button finish inside Direction C** (faint tiled texture on title plates and primary buttons only, rim + bottom lip + sheen on primary actions, hard text shadows). Direction C stays the approved identity; the full stud-shop look is not proposed. Needs a 2–3 direction mockup and owner pick; any shipped texture must be our own bake or rights-confirmed.
  - **C-U1 Creature Viewer.** [[Creature Viewer]]
- ~~**Visual correction candidates (2026-10-16)**~~ → **Approved 2026-10-16** as *Visual direction APPROVED* above (UI C, creature C with hero refinements). Original: — [[Visual Direction Review 2026-10-16]]:
  - UI direction **A Clean Lab / B Playful Cartoon / C Balanced** (recommended C): side rails (left Build/My Lab/Creatures/Index, right Goals/Ranch/Home + context slot), one status-pod HUD (−69% area), framed panels with overlapping title plate + mint page + one focal hero; Goals as a "Lab Task Board".
  - Creature direction **A cute/chunky / B biological / C balanced** (recommended C, with A's blush/paw pads and B's growths as rarity detail).
  - [[Creature Face Language]] (eye sizes, layered iris + 2 glints, 5 expressions).
  - Part budget 24–47 per creature; face micro-parts LOD beyond 40 studs; Frostpup fur body as a Blender/MeshPart candidate.
- **Phase 2 overnight candidates (2026-10-16, Claude, NOT approved)** — built as Experimental in Studio, need an owner verdict:
  - **UI screen identity:** an accent colour per screen (Index purple, Egg Shop orange, Mutation violet, Creatures pink, Research teal, Ranch green, My Lab blue, Goals gold); emoji icons as placeholders. [[UI - Figma TODO]]
  - **NEW badges** on the Index and Creatures nav tiles (cleared when the screen opens).
  - **Creature part budget ≤ 22** (incl. eyes, pupils, shines, rarity ring) instead of ≤ 8/10/12 in the plan; prototypes measured 13–21 + ring.
  - **The 7 prototype looks** (Slimelet, Frostpup, Pebbletoad, Sparkbug, Mossbit, Magmawisp, Rockling). [[Creature Prototypes]]
  - **Wisp without a shadow disc;** shrink-blink for Ball eyes.
  - **Hatch/mutation storyboard timings** and the "Extreme" egg tier definition. [[Hatch Storyboard]], [[Mutation Storyboard]]
  - **Exact onboarding order** and hint wording; a free starter incubator for the welcome egg. [[Early Game Reorder]]
- Bio-assay payout 3 Cash / 4 Research / 1 XP (was 6/8/6) — [[ECONOMY_2C]].
- No post-Level-25 sink in Build B — [[FINISH_3_VALIDATION]] section 3.
- ~~**UI must be fully customizable in Studio**~~ → **Approved 2026-10-15**, see [[#UI is editable in Studio (hybrid architecture)]]. Original candidate text: — owner comment on 2026-10-15 UI references ("but whenever making a ui make it fully customizable in Studio"). Likely meaning: screens exist as editable Studio UI (StarterGui instances a designer can adjust) and code only fills in data and behaviour. **Discrepancy with current code:** `StarterGui` is empty in the 2026-10-14 export and 11 of 12 client controllers build their `ScreenGui` at runtime ([[Architecture#Client controllers]]). Confirm the meaning before it becomes an Approved decision. Sources: [[Index Collection Screen]], [[Shop Storefront Layout]].
- ~~**Map overhaul (proposed 2026-10-15)**~~ → **Approved 2026-10-15** with changes (display area kept, baseplate conditional, organic biomes); see the *Map:* entries above. Original candidate text: (1) parts-based elevation instead of Roblox Terrain (backup captures parts, not voxels); (2) move the Research Terminal from the exact centre to the reactor's south console; (3) one habitat biome per plot gap; (4) keep / integrate / retire `CreatureDisplayArea`; (5) retire the invisible non-collidable `Baseplate`. See [[MAP_OVERHAUL_PLAN]].
- Visual + Game Feel Overhaul agent plan (2026-10-15 chat) — proposed only, not approved or executed.
- **Market research candidates (2026-10-15, [[Roblox Market Research]])**: research only, **none approved**. Each needs an explicit owner decision before it becomes binding.
  - **Onboarding: earlier first hatch.** Move one egg/hatch payoff into the first ~2 minutes (e.g. a starter egg already incubating on claim), before the first mutation. Today the first hatch is step 15–17 of 18. See [[Gameplay Loop Research#MPL today]].
  - **Creatures: silhouette-first identity.** Group species into distinct body plans, and make variants readable from ~30 studs (glow/particles). See [[Creature Presentation Research]]. Prerequisite: a creature visual direction decision.
  - **Hatch as an in-world moment.** Egg wobble → crack → creature walks to its pen; the panel stays as a summary.
  - **Mutation results show both parents.** One visible feature from each parent.
  - **Ranch: fewer menu steps.** Direct in-world actions (prompt/tap) for the most common pen/bed action; panels for details.
  - **Biomes with a function.** A light gameplay tie-in per biome (e.g. habitat-match bonus) after the visual map work. See [[Map and Environment Research]].
  - **Reactor reacts.** Visual-only pulse on mutation/discovery events after map step F.
  - **Game-feel quick wins.** Fill the UI kit `Sounds` slots; short pop/arc feedback on plant/harvest/collect. See [[Game Feel Research]].
  - **Research shows world changes.** Each node previews what it unlocks in the world.
  - **Never adopt:** paid timer skips, paid hatch multipliers/luck, loss-of-progress mechanics, unsafe trading. See [[Anti-Patterns]]. (Already covered by the monetization decision; restated for research.)
- **Hatching & simulator research candidates (2026-10-15, [[Egg Hatching Research]], [[Roblox Market Research#Simulator feature priority matrix]])**: research only, **none approved**.
  - **Hybrid in-world hatch flow.** Incubator crack → creature walks to its pen → compact card. Rarity-scaled: normal ~3 s, rare ~4.5 s, first discovery ~6 s, secret ~8 s. Tap to skip; short version for already-owned species; never auto-skip first discoveries. Full table: [[Egg Hatching Research#Recommended MPL hatch flow]].
  - **Reactor-staged mutation reveal.** Specimen pads at the Mutation Reactor, charge-up, result on the dais, discovery beacon, fizzle + hint on a failed secret. Would need an approved move of the Mutation Lab interaction (frozen prompt today). See [[Mutation Reveal Research]].
  - **Onboarding reorder (detailed).** Starter Field egg incubating at claim → hatch by ~2 min → first mutation at the Reactor by ~8 min. See [[Early Game Research]]. Supersedes nothing yet; refines the earlier "earlier first hatch" candidate.
  - **Creature idle-life and reactions** (sleep, eat, bounce, look at player).
  - **Visit-a-lab, read-only** (pet creatures, one "Impressed" per visitor per day) + Specimen Showcase of server rarities. Visitors never affect owner progress. See [[Social Systems Research]].
  - **Rotating lab requests** on the existing assignment system (optional, no streaks).
  - **Per-family Index milestones → cosmetic lab decor.**
  - **Progressive secret hints + Index silhouettes + variant pity.** See [[Rare and Secret Content Research]].
  - **Valley weather / scheduled reactor surges** biasing traits or variants (MAYBE; no FOMO, no admin-only randomness).
  - **Never adopt:** rebirth, trading/gifting (for now), daily-login chores/streaks, PvP, wealth leaderboards, paid or multi-hatch, auto-hatch, value-lowering random outcomes. See [[Anti-Patterns#Pass 2: simulator features we should NOT copy]].
- ~~**Phase 2 design-pass candidates**~~ → **Approved 2026-10-16** (with owner adjustments) as the *Phase 2:* entries above. C2-1/C2-2 → hatch + entering world; C2-3 → Machine stays, Reactor responds; C2-4 → notices **default OFF**; C2-5–C2-8 → visual language + readability; C2-9 → client display models; C2-10 → procedural animation; C2-11/C2-12 → welcome egg + pacing direction (exact guide order is settled in Checkpoint F); C2-13 hatch setting → part of the skip behaviour; C2-14 → parts first; C2-15 → sound review gate. Original candidate text kept below for history (2026-10-16, [[Phase 2 Spec]]):
  - **C2-1 Hybrid hatch presentation.** In-world incubator sequence + compact lab-skin card. Tiers: Normal ~3 s / Rare ~4.5 s / First discovery ~6 s. Tap to skip; auto-short for owned species; never auto-skip a discovery or a variant. Spec: [[Hatch Presentation Spec]].
  - **C2-2 Creature enters the world after hatching.** Look at the player → personality idle → walk to the pen (Assign) or a holding spot. Cosmetic; assignment stays a server request.
  - **C2-3 Reactor-staged mutation reveal.** Choose at the MutationMachine; cable pulse → reactor charge → result at the pad. Secrets get the beacon + sky tint. A failed secret attempt is shown as a "Lab note" with the reactor sputtering. Spec: [[Mutation Reveal Spec]].
  - **C2-4 Optional server notices** for first discoveries/secrets (opt-out toggle).
  - **C2-5 Creature visual language:** 7 body plans + hybrid, silhouette first, one mutant accent per species, big readable eyes, glow organ = biology, rarity scale 1.0–1.35. Spec: [[Creature Visual Language Spec]]. Would become the first **creature visual direction**.
  - **C2-6 Mutation inheritance authored into the 30 results:** form from parent A, finish/glow from parent B; the result card names both.
  - **C2-7 Variants visible everywhere** (pens, holding, showcase, hatch, Index): Luminous pulse, Chromatic hue drift, Prismatic sparkle.
  - **C2-8 Traits as behaviour + icon** (e.g. Curious investigates, Calm slow blink, Volatile fizz).
  - **C2-9 Client display models** from editable Studio templates (`ReplicatedStorage/MutantPetLab/Creatures`), following the unchanged server proxy, with LOD and culling. Ball fallback if a template is missing.
  - **C2-10 Procedural client-side animation set:** idle, walk/run, eat, sleep, investigate, social, hatch emergence, mutation reaction; look-at + blink. Spec: [[Creature Animation Spec]].
  - **C2-11 Welcome Field Egg** already incubating at claim, plus a one-time guaranteed undiscovered species (Mossbit/Frostpup/Embercub). Target: first hatch + first discovery at ~2 min. Spec: [[Early Game Pacing Spec]].
  - **C2-12 Guide reorder:** pen → welcome hatch → core loop → first mutation at ~5–8 min → research → egg shop → expand. Re-run the economy simulation and tests.
  - **C2-13 Hatch-animation setting** ("Full / New only").
  - **C2-14 Build method:** parts-built creatures first (recommended); Blender meshes later for heroes — owner choice.
  - **C2-15 Sound sourcing** for the empty UI kit `Sounds` slots — owner choice.

## Build Mode: compact strip, snap grid, fixed camera

**Status:** Approved

**Decision:**
- **Menu:** Build Mode uses a **compact strip along the bottom** (small item cards, GRID and TURN VIEW buttons, a small X).
- **Grid:** a **snap grid in 4 sizes (1/2/4/8 studs)** drawn on the unlocked land. All sizes are whole studs, so the server's one-stud rule is unchanged.
- **Placement:** touch placement shows **ROTATE / ✔ confirm** with an item card (name, price, CANCEL) at the bottom right.
- **Camera:** the camera is **fixed** like Bloxburg. It's angled overhead from the plot entrance and frames the land. There's no free orbit. The player can pan (drag the ground / right-drag / WASD), zoom (pinch / wheel) and turn the view in quarter turns. Build Mode owns the camera while open, so nothing else can fight it (that caused a shake).

**Reason:** Owner request 2026-10-21 + reference R3 (Bloxburg build screenshots).

**References:** [[Owner Reference Library#R3 · Grid build placement]]

**Affected systems:** Build Mode (`BuildModeController`, `StarterGui.MPL_BuildMode`)

**Date:** 2026-10-21

## Creature style: every pet follows the blueprint Frostpup (R16)

**Status:** Approved

**Decision:**
- **Scope:** **All pets** use the owner's blueprint Frostpup style ([[Owner Reference Library#R16 · Frostpup filled example (added 2026-10-20)|R16]]).
  - Chunky chibi proportions, about 0.9× avatar height.
  - **Faceted low-poly finish.**
  - Big glossy eyes with highlights.
  - One bold mutant feature.
  - Rarity add-ons as small crystals or sparkles.
- **Finish by material:** crisp, large facets for ice, crystal and rock; softer, smaller and fewer facets for gel, plant and fluffy species. The low-poly identity stays, but each material still reads.
- **Method:** each body is modelled in **Blender** with low-poly flat shading and imported as **MeshParts**. Eyes and face stay as parts so the approved expressions keep working.
- **Uploads:** the meshes upload as Roblox assets when the place is saved. **No publish.**
- **Superseded:**
  - "Faceted only where the material calls for it" ([[Creature Template Sheets]] *Finish*).
  - The C3 hybrid-Frostpup choice, which is now an interim baseline.
- **Body families and roster batches:** the plan stays, but every species is re-skinned in this style. The 7 representatives are re-done first, starting with Frostpup as the style anchor, and shown to the owner before scaling.

**Reason:** Owner request in chat, 2026-10-21 ("I kinda want the pets to have the same style like frostpup in the blueprint"), then the owner chose *All pets* + *Blender meshes*.

**References:** R15, R16

**Affected systems:** Creatures (templates, CreatureKit, LOD), the 29-species roster plan, specimen sheets

**Date:** 2026-10-21

## Production creature style: Frostpup + Mossbit Blender anchors approved

**Status:** Approved

**Decision:** The Blender **Frostpup** (animal / fur / ice) and **Mossbit** (plant / organism) style anchors are the **production creature direction** for the whole roster:
- cute collectible organism first, mutant biology second
- clean low-poly / faceted modelling and a species-specific silhouette
- an expressive Roblox-compatible face system (separate face parts; expressions are not baked into the mesh)
- matte body materials, restrained glow, one strong mutant feature
- readable at gameplay distance, light enough for LOD + animation

**Surface treatment varies by material, so the game stays cohesive without one uniform finish:**
- soft animal: broader, smoother low-poly planes
- plant: layered leaf/petal planes
- gel: soft rounded/faceted organic volume
- insect: clean segmented planes
- wisp: floating layered forms
- rock/crystal: strongest faceting

**Process:**
- **No broad creature-style exploration again.** Frostpup and Mossbit are only changed for real bugs.
- Order: the 5 remaining body-family anchors one at a time (Slimelet → Pebbletoad → Sparkbug → Magmawisp → Rockling), then a 7-anchor review, then the 29 species.
- Per species: specimen sheet → Blender → import → validation.
- Normal species inheriting an approved body family need **no** A/B/C concept round.
- **Explicit owner review stays required for:** Legendary, Mythic, secret species, Chimerax/hybrids, unusual anatomy, a new body family, or a substantially different art direction.

**Reason:** Owner approval in chat, 2026-10-21, after [[Style Anchor Review 2026-10-21]].

**Affected systems:** Creatures (templates, CreatureKit), specimen sheets, roster plan

**Date:** 2026-10-21

## Luminous variant: species-controlled glow

**Status:** Approved

**Decision:** Luminous **enhances the species' own identity**; it never replaces its colours with white glow.
- The body stays matte and keeps the species' colours.
- The mutant organ / accent gets brighter in a saturated species hue: `CreatureKit` template `LuminousTint` + `LuminousMix`, and per-part `LuminousGlow=false` to opt out.
- Subtle particles where appropriate.
- Frostpup = cyan luminous collar. Mossbit = rose/pink luminous flower bud.
- Every future species gets the same treatment, defined in its specimen sheet.

**Reason:** Owner approval in chat, 2026-10-21.

**Affected systems:** CreatureKit, CreatureAnimator (pulse), species templates

**Date:** 2026-10-21

## R17 / R18 reference decisions

**Status:** Approved

**Decision:**
- **R17** (MPL "Creature Blueprints: Core Roster" board) is approved as a **UI / specimen-sheet / Index-layout reference only**. Use it for:
  - hero creature presentation
  - front / side / back views
  - the variant row and the mutation-lineage/path row
  - specimen-sheet and Index-detail composition

  Production creature models do **not** move toward R17's soft/plush art style.
- **R18** (voxel pets video) is **inspiration only**: silhouette ideas, a creature-viewer/model-inspection workflow, rare/cosmic variant treatment. **Never** voxel/block pets; never copy its models; the approved Blender style stays.

**Reason:** Owner decision in chat, 2026-10-21.

**References:** [[Owner Reference Library#R17 · MPL "Creature Blueprints: Core Roster" board (added 2026-10-21)|R17]], [[Owner Reference Library#R18 · "Pov: you started to make models with Claude design" video (added 2026-10-21)|R18]]

**Affected systems:** Index, Creatures Viewer, specimen sheets

**Date:** 2026-10-21

## SEVEN BLENDER BODY-FAMILY ANCHORS APPROVED FOR PRODUCTION

**Status:** Approved (locked by the overnight-run brief: "If clean, record")

**Decision:** The seven Blender anchors are the binding style foundation for the remaining roster. Broad creature art direction is **not reopened**.

| Family | Anchor |
|---|---|
| Gel | Slimelet |
| Critter | Frostpup |
| Hopper | Pebbletoad |
| Flyer | Sparkbug |
| Sprout | Mossbit |
| Wisp | Magmawisp |
| Shellback | Rockling |

**Review (2026-10-22):** front / side / Luminous lineups, Index, viewer, pens and 30 studs all clean. Seven distinct silhouettes in one cohesive style; species-coloured Luminous on every anchor; no same-face syndrome (different eye colours, sizes and placements per family). Performance: 24 mixed Blender creatures at close/full rate = **0.285 ms/frame** (budget 0.5).

**Evidence:** `Planning/Assets/Overnight 2026-10-22/seven-anchors-*.jpg`

**Date:** 2026-10-22
