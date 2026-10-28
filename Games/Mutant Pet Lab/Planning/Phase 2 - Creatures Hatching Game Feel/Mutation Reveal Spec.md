---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: mutation
status: approved-direction
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - planning
  - phase-2
---
# Mutation Reveal Spec

> [!success] APPROVED DIRECTION (owner, 2026-10-16) — not implemented yet
> Binding decisions: the *Phase 2:* entries in [[Design Decisions]]. Where this spec and a decision differ, the decision wins. Implementation follows [[PHASE2_IMPLEMENTATION_PLAN]] after the owner reviews it.
> **Built on:**
> - [[Mutation Reveal Research]]
> - [[Rare and Secret Content Research]]
> - [[Design Decisions#Map: Mutation Reactor approved as the central landmark]]
> - [[Design Decisions#Map overhaul implementation (approved implementation notes)]]


## What exists today
- **Where:** the Mutation Lab panel opens at the campus `MutationMachine` (NW court, prompt at −50, 2.9, −37).
- **Rules:**
  - Two owned, unassigned creatures + Research. **Both parents are consumed** and the result is added instantly.
  - First discovery grants 15 Cash / 20 Research / 50 XP.
  - A failed secret attempt is **free** and returns a category message + the hint.
- **Reveal:** a purple result card inside the panel. The reactor doesn't take part.
- **The approved reactor** (`MutantWorld/MutationReactor`) has named neon parts ready for animation:
  - `Core`, `CoreBlend`, `CoreUpper`
  - `Crown`
  - `DaisTrim1`, `DaisTrim3`
  - `TankLiquid1–4`
  - `CrownTrim`

## Principle
**The Mutation Lab is where you decide; the Reactor is where it happens.** The panel stays the place for choosing parents (a real choice that needs a menu). The *reveal* moves into the world, at the reactor everyone can see.

The interaction point does **not** move in this proposal:
- The prompt stays at the MutationMachine.
- The reactor responds remotely, connected by the approved cables that already run from the dais to the station courts.
- Moving the interaction to the reactor would be a separate owner decision and a frozen-object change.

## Sequence

| Beat | Standard result (seen before) | First discovery | Secret (mutation-only Mythic) |
|---|---|---|---|
| Confirm (panel) | MUTATE pressed. The two parent icons slide together on the card | same | same |
| **Machine** (local) | The MutationMachine's chamber lights green. The parent models (client copies) step onto the pads and dissolve into light (0.8 s) | same | same |
| **Cable pulse** | A light pulse travels along the cable from the NW court to the reactor (0.6 s) | same | same, purple |
| **Reactor charge** | The core brightens; `CoreBlend` hue drifts (1 s) | + catwalk trims flicker, 1.5 s | + all 4 tank liquids rise in brightness; the crown spins up (2 s) |
| **Result** | The result appears **at the machine pad** as a silhouette, then colour (0.4 s). The card shows the result + **"from A + B"** with both parent icons | + **"NEW SPECIES"** stamp + Index entry glow | + the reactor **beacon**: crown flash and a 3 s sky tint in the species colour, visible from every plot (sight lines are guaranteed) |
| **Server notice** | none | none (**default OFF**, owner 2026-10-16) | none by default; the system is prepared as an optional, configurable setting limited to secret/very rare discoveries |
| **Into the world** | The creature hops off the pad and follows the player for 3 s, then waits at the machine's holding spot until assigned | same | same |

**Durations:**
- Standard ~3 s.
- First discovery ~5 s.
- Secret ~7–8 s (only once per player per species).

**Skip:** tap fast-forwards to the card. Never auto-skip a first discovery or a secret.

## Anticipation and uncertainty
- **Known recipe** (in the Index): no uncertainty about the species. The surprise comes from the trait/variant roll, revealed in the same order as hatching ([[Hatch Presentation Spec#Trait and variant reveal]]).
- **Secret attempt that fails:** the reactor **sputters**:
  - The core dims, a crackle plays, and the crown flickers once (1 s).
  - The card shows the hint as a **"Lab note"** in the lab-skin style, not as an error.
  - Still free, as today. It should feel like research progress.
- **Progressive hints** (Candidate): each failed secret attempt reveals one more fragment of the hint. The conditions stay server-only.

## Rare / secret escalation
- **Escalation is about the world reacting:** reactor → sky. Never longer UI.
- **Secret = the rarest moment in the game** and the only use of the sky tint. Keep it unique.
- **Server notices: default OFF** (owner, 2026-10-16). Build the hook so it can later be enabled per server config for secret/very rare discoveries only. Never announce failures.

## Discovery feedback
- **Index:** the species card animates from silhouette to colour the first time the Index is opened afterwards. Family completion progress ticks.
- **Discovery Board** (the reserved plinth on the promenade, no logic yet): a later candidate is to list the server's last 5 discoveries. Cosmetic, no rewards.
- **Assignments:** existing `FirstDiscovery` / `SecretDiscovery` events are unchanged.

## Mutation result readability
A mutated species must **look like both parents.** The inheritance table is in [[Creature Visual Language Spec#Mutation inheritance table]]. The result card repeats it in words: "Molten core from Slimelet · stone shards from Rockling".

## Technical notes (for the later build)
- **All reactor and machine effects are client-side** tweens of the existing neon parts, triggered by the existing mutation result response (and a broadcast for the optional server notice).
- **No server authority change.** Effects restore the parts' exact original properties afterwards.
- **One shared reactor:** concurrent mutations from several players queue their pulses (max 1 reactor sequence at a time per client view; others shorten to a single pulse).
