---
type: game
tags:
  - roblox
  - game
  - mutant-pet-lab
place-id: 86236241957181
game-id: 10770449805
owner: AYRX Entertainment (group 9350216)
status: Build B released (v88)
project-folder: ~/Claude's Personal Workspace/MutantPetLab
updated: 2026-10-15
---

# Mutant Pet Lab
Back to [[Home]]. Lessons learned here are in [[Knowledge/Index|Knowledge]].


A Roblox creature-breeding and ranch game by **AYRX Entertainment**: PlaceId `86236241957181`, GameId `10770449805`. On Roblox the place is still named "Untitled Experience".

## Dashboard

> [!abstract] Start here
> [[Current State]] · [[Roadmap]] · [[Known Issues]] · [[QA - Test History]] · systems map: [[Mutant Pet Lab Systems.canvas|Systems canvas]]

| Systems | Data | Planning |
|---|---|---|
| [[Architecture]] | [[Species]] (36 notes) | [[UI - Figma TODO]] |
| [[Economy]] | [[Mutation Recipes]] | [[Map Overhaul]] |
| [[Persistence]] | [[Egg Families]] | [[Creature Overhaul]] |
| [[Research Tree]] | [[Traits and Variants]] | [[Monetization TODO]] |

![[MPL Notes.base#All MPL notes]]

### Species Index
![[Species.base#By rarity]]

> [!info] Refreshing the data notes
> Species, recipes, eggs, traits, research and the snapshot table are generated from the verified export, never typed by hand. After a new snapshot run:
> ```
> cd "$HOME/Claude's Personal Workspace/MutantPetLab" && python3 -I tools/vault_export.py
> ```
> Only text between `%% BEGIN GENERATED %%` and `%% END GENERATED %%` is replaced; anything you write outside those markers stays.

## Design Memory

> [!tip] References & similar games (2026-10-20)
> [[Master Visual and Gameplay References]] · your living file: [[References for games with assets that I like and dont like.]] · [[Owner Reference Library]] · [[Do Not Copy]] · [[Reference Gaps]]
> [[Similar Games Overview]] · [[Similarity Matrix]] · [[Feature Comparisons]]
> **Design specs (2026-10-20, candidates):** [[MPL Visual Fingerprint]] · [[Next Build Brief]] · [[Creature Template Sheets]] · [[Building Art Direction]] · [[Egg Research Center Redesign]] · [[Physical Egg Interaction]] · [[Creature World Interaction]] · [[Variant Visual Language]] · [[Creature Viewer]] · [[Plot Decoration and Visiting]]


> [!important] Before visual/design work, Claude reads approved decisions and relevant references first.
> Rules and the session-start routine: [[Claude Workflow]].

- [[Design Decisions]]: approved decisions (strongest authority after your current instruction)
- [[Reference Library]]: visual/design references by category · [[References.base|browse]]
- [[Reference Inbox]]: drop raw screenshots, links and ideas here
- [[Roblox Market Research]]: 2026-10-15 competitor/UI/loop research (reference-level, not decisions) · [[Roblox Research.base|browse]] · [[Anti-Patterns]]
- [[Phase 2 Spec]]: **proposed** creature + hatching + game-feel overhaul (design pass, awaiting approval)
- [[Egg Hatching Research]]: recommended hatch flow · [[Roblox Market Research#Simulator feature priority matrix|feature priority matrix]]
- [[UI - Figma TODO]] · [[Map Overhaul]] · [[Creature Overhaul]]

## Status (as of 2026-10-16)
- **Map overhaul applied** (Checkpoint C passed, 185/185): Mutation Reactor, plaza, Specimen Showcase, valley terraces, 8 biomes. **Saved to Roblox, not published** — snapshot `2026-10-16_map_overhaul_checkpointC`. See [[Map Overhaul#Applied 2026-10-16]].
- **Build B is released as v88**, with production saving for live players.
- **Live servers** save to DataStore `MPL_PlayerData_PROD_V1`, scope `Production`. **Studio** always uses an in-memory test store, so it never touches real player data.
- **Tests:** 185/185 passing.
- **Release build:** checksum `2048056006`, snapshot `2026-10-14_release_persistence`.
- **Open items:**
  - The live leave/rejoin save check hasn't been run yet; it needs a real account.
  - The experience appears to be editors-only.
  - Small UI polish items remain on phones (see [[FINISH_3_VALIDATION]], section 4).

## Project docs
These are linked from the project folder, so edits here change the real files there.
- [[CLAUDE_PROJECT_STATE]]: read this first; current state and how to resume.
- [[PERSISTENCE_ACTIVATION]]: production saving, the store and its safety rules.
- [[FINISH_3_VALIDATION]]: Checkpoint E hardening (trait RNG, Specimen Supply range, mobile UI).
- [[FINISH_3_MULTIPLAYER]]: two-player tests M1–M9.
- [[PLAYTHROUGH_2C_D]]: Finish 2C new-profile playthrough and the Biolume secret.
- [[ECONOMY_2C]]: Level 1–25 unlock map, sources and sinks, pacing.
- [[RESTORE]]: how to rebuild the place from a local backup.

%% BEGIN CODE GRAPH STATUS %%
## Code Graph

| | |
|---|---|
| Last refresh | 2026-10-15T12:28:11-04:00 |
| Mode | code-only, --no-label, sandbox deny network* |
| Graph | `~/Claude's Personal Workspace/MutantPetLab/graphify-out/graph.json` · vault pages: `Code Graph/` · report: [[GRAPH_REPORT]] |
| Indexed | 65 modules (61 game scripts from `current/source` + 4 backup tools) · 458 nodes · 757 edges · 39 communities |
| Curated links | 125 code links across 8 system notes (see each note's *Code references*) |

> [!warning] Luau parsing limits
> - graphify parses Luau with a **standard Lua** grammar: type annotations, compound assignment (`+=`), `continue` and string interpolation are partly missed. About 87% of named functions are captured (307/354 at the 2026-10-15 audit); the gaps are mostly in tests.
> - Roblox `require(script.Parent.X)` paths are not resolved, so there are almost no module→module edges (44 cross-file edges). Use the curated links and [[Architecture]] for dependencies.
> - Remote handlers (`X.OnServerInvoke = function`) are anonymous and do not become nodes.
> - Communities stay numbered (`Community N`): naming them needs an LLM, which is deliberately not used.

**Refresh (offline, repeatable):**
```
cd "$HOME/Claude's Personal Workspace/MutantPetLab" && zsh tools/graph_refresh.sh
```
%% END CODE GRAPH STATUS %%

## Build history
| Milestone | Result |
|---|---|
| Finish 2A | Six-family Cash Egg Shop, hatching |
| Finish 2B | 4-stage property expansion, Featured Specimen |
| Finish 2C | Onboarding, assignments, economy pass, secret mutations (163 tests) |
| Finish 3 | Two-client multiplayer M1–M9 passed |
| Checkpoint E | Server trait RNG, Specimen Supply range check, responsive UI (173 tests) |
| Release | Production persistence, published v88 (185 tests) |

## Where things live
- **Project folder:** `~/Claude's Personal Workspace/MutantPetLab/`. It's a local git repo; dated `snapshots/` are never overwritten.
- **Source of truth:** Roblox Studio. Script exports live under `snapshots/<label>/source/`; they're kept out of this vault to avoid thousands of files.
- **Rules:**
  - Never touch SHIFT FROM HELL! or GRAB N RUN!.
  - Publish only with explicit approval.
  - Keep at most 3 Roblox Studio processes running.
