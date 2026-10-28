---
type: planning
game: "[[Mutant Pet Lab]]"
area: onboarding
status: blocked-needs-owner-approval
updated: 2026-10-22
tags:
  - mutant-pet-lab
  - planning
  - onboarding
  - schema
---
# Welcome Egg: implementation plan (CP8, plan only)

> [!warning] STOPPED at the plan by design
> This needs a **DataStore schema change (v3 → v4)**. The overnight brief says: document the migration and stop. **Nothing was implemented.** `FeatureFlags.WelcomeEgg = false` is unchanged.

**Approved intent** ([[Design Decisions]], 2026-10-16, and [[Early Game Pacing Spec]]):
- one-time
- a guaranteed **undiscovered** species from the early pool
- persisted and server-authoritative
- appears in the **starter incubator**
- first hatch at about 1:30–2:00, followed by the full first-discovery reveal

## What exists today (verified in Studio 2026-10-22)
| Item | State |
|---|---|
| Schema | `PlayerDataSchema.CurrentVersion = 3`. Migrations 0→1, 1→2 (adds `Property = PropertySchema.New()`), 2→3 (adds `ResearchUnlocks`). |
| New property | `PropertySchema.New()` → `{Buildings={}, Food={}, Eggs=1, EggOrdinal=0, OwnedEggs={}, EggInventoryMigrated=false, Care={}, ExpansionStage=0}`. New players **already get one ordinary Field egg** (legacy `Eggs=1` → owned-egg compatibility). |
| Hatch | `PropertyService` "Hatch": `EggFamilies.Roll(familyId, random)` over the family's `HatchTable`. No per-egg overrides. |
| Flags | `FeatureFlags.WelcomeEgg = false`, `OnboardingV2 = false`, `HatchSequence = false` (the hatch FX shipped tonight are client-only and not behind that flag). |
| Presentation | Ready. The first-discovery tier in `HatchSequence` (2.6 s pre-reveal) and the `showReveal` discovery title already run for any `NewDiscovery` hatch. |

## Proposed design
1. **Schema v4** (forward-only):
   - `Migrations[3]`: set `SchemaVersion = 4` and add `Property.WelcomeEgg = { Granted = <bool>, Hatched = <bool> }`.
   - Existing profiles get `Granted = true, Hatched = true`, so **no retro grant**: veterans are untouched.
   - `PropertySchema.New()` (new players only) gets `WelcomeEgg = { Granted = false, Hatched = false }`.
2. **Egg record tag:** an owned egg / incubator record may carry `Welcome = true`. The sanitizer must keep this one boolean, which is why it is a schema change.
3. **Grant (server):**
   - On first load with `Granted = false`, convert the starter `Eggs=1` Field egg into the welcome egg, so the egg count is unchanged and the economy is neutral.
   - Auto-place it in the starter incubator with a **90 s** timer.
   - Set `Granted = true` in the same write.
4. **Hatch (server):**
   - If the incubator egg has `Welcome = true`, roll from the Field `HatchTable` restricted to species **not in `Discoveries`**, with the same weights renormalised.
   - Pool: Mossbit / Frostpup / Embercub (owner-approved early pool).
   - If every species is discovered (impossible for a new profile, defensive only), fall back to the normal roll.
   - Clear the tag and set `Hatched = true` **before** granting the pet, matching the existing exactly-once rule.
5. **Client:** no new authority. The existing reveal plays the first-discovery tier because `NewDiscovery` is true. Guide hint: "Your welcome egg is almost ready, select the incubator and HATCH."
6. **Onboarding:** `OnboardingV2` reorder ([[Early Game Reorder]]) ships together with this change, both behind flags.

## Migration risk and publish rule
- **v4 is forward-only.** A v3 server that loads a v4 profile refuses it ("stored schema version is newer"), so old servers must be shut down when this ships. That shutdown requires **owner approval at publish time**.
- Test plan:
  - unit tests for `Migrations[3]` (veteran: no egg added; new: one tagged egg; idempotent re-load)
  - hatch-roll restriction (1000 rolls → only undiscovered species)
  - storage-full path keeps the egg
  - `EconomySimulation` and `Finish2C_Economy_Test` re-run (should be neutral: the egg replaces the existing starter egg)
- Studio only, **Mock store**. No production saves touched.

## Owner decisions needed
1. Approve **schema v4** plus the publish-time server shutdown.
2. Confirm the **welcome egg replaces** the current free starter Field egg (economy-neutral) rather than adding a second egg.
3. Confirm the 90 s timer and the pool Mossbit / Frostpup / Embercub.

Estimated work after approval: about 2–3 hours (schema + service + 8–10 tests + guide copy + QA).
