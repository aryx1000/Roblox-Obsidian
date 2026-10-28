---
type: planning
game: "[[Mutant Pet Lab]]"
area: onboarding
status: proposal-awaiting-owner-approval
updated: 2026-10-23
tags:
  - mutant-pet-lab
  - planning
  - schema
  - onboarding
---
# Welcome Egg: exact migration proposal (v3 → v4)

> [!warning] PROPOSAL ONLY: nothing implemented
> The direction is approved conceptually (owner, 2026-10-23). **No schema, service or config has changed.** `FeatureFlags.WelcomeEgg = false`. Source facts are from snapshot `2026-10-22_overnight_cp9_campus`. Earlier outline: [[Welcome Egg Implementation Plan]].

## A. Current schema / state involved
| Where | Today |
|---|---|
| `PlayerDataSchema.CurrentVersion` | **3** (migrations 0→1, 1→2 add `Property`, 2→3 adds `ResearchUnlocks`). A server refuses any profile newer than its version. |
| `Schema.NewProfile()` | Starter creatures **Slimelet, Rockling, Sparkbug** (discovered), `Property = PropertySchema.New()`, onboarding `{Steps={}, Dismissed=false}` |
| `PropertySchema.New()` | `{Buildings={}, Food={}, Eggs=1, EggOrdinal=0, OwnedEggs={}, EggInventoryMigrated=false, Care={}, ExpansionStage=0}`. **No buildings, so no starter incubator.** |
| Starter egg today | `Eggs=1` → on first sanitize `PrepareOwnedEggInventory` converts it into **one owned FieldEgg `egg_1`** in `OwnedEggs`. The player must build an incubator (25 Cash) and incubate it (onboarding steps BuyEgg → Incubate → Hatch, near the end of the guide). |
| `PropertySchema.Sanitize` | Rebuilds the property from **known fields only**. Owned eggs keep only `{Id, FamilyId}`; incubators keep `EggType, EggId, EggOrdinal, ReadyAt`. **Any new flag would be stripped, which is why this is a schema change.** |
| Hatch (`PropertyService` "Hatch") | `EggFamilies.Roll(familyId, random)` over the Field `HatchTable` (Slimelet 2400, Rockling 2400, Sparkbug 1500, Mossbit 2200, Frostpup 750, Embercub 750). The record is cleared **before** the creature is granted (exactly-once). A full storage refuses safely and the egg stays. |
| Incubator | `BuildableConfig.Incubator` 8×8, Cost 25, Limit 2; Stage-0 bounds X ±48, Z −38..38. Selling is refused while `EggType` is set. |

## B. Proposed new fields (schema v4)
```lua
Property.WelcomeEgg = {
	State = "None" | "Pending" | "Incubating" | "Hatched",  -- string enum, sanitized
	EggId = "egg_N" | nil,                                    -- the egg that carries the guarantee
}
```
That is the only new persisted data. The **guarantee is keyed on `EggId`**, not on a tag stored on the egg record, so the existing egg / incubator shapes don't change.

## C. Defaults
| Profile | Value after load |
|---|---|
| **Existing profile (v3 → v4 migration)** | `{State = "Hatched"}`: treated as already done, **no retro grant**, nothing else touched |
| **New profile** (`PropertySchema.New`) | `{State = "Pending"}` |
| Malformed / unknown value on load | Sanitize to `"Hatched"` (the safe direction: never grants twice) + a warning |

## D. New-player flow
1. **First load** (`State == "Pending"`), all inside the server load transaction, before the first save:
   - Place a **free starter Basic Incubator** at a fixed valid Stage-0 spot (plot-local X = 20, Z = −20, Rotation 0, Id `build_1`). If that spot fails `B.Validate` (impossible on an empty plot), try 3 fallback spots.
   - Take the starter FieldEgg `egg_1` out of `OwnedEggs` and put it **directly in that incubator** (`EggType="FieldEgg", EggId="egg_1", ReadyAt=now+90`).
   - Set `WelcomeEgg = {State="Incubating", EggId="egg_1"}`.
2. The guide points at it: "Your welcome egg is almost ready, select the incubator and HATCH." (`OnboardingV2`, also flagged).
3. **Hatch:** if `target.EggId == WelcomeEgg.EggId` and `State == "Incubating"`, roll from the Field table **restricted to species not in `Discoveries`**, same weights renormalised. For a new player that is Mossbit 59% / Frostpup 20.5% / Embercub 20.5%, which is always a NEW DISCOVERY (5–6 s reveal). If everything in the table is discovered (defensive), use the normal roll.
4. In the **same mutation** that clears the incubator: `State = "Hatched"`, `EggId = nil`, then grant the creature.
5. The starter incubator is an ordinary structure afterwards: it stays, can be moved, and can be sold for the normal half refund.

## E. Existing players
Migrated straight to `Hatched`. No incubator added, no egg added, no inventory or balance change. They never see welcome-egg UI.

## F. Save / load behaviour
- **Migration `[3]`:** deep copy, `SchemaVersion = 4`, `Property.WelcomeEgg = {State="Hatched"}`. Pure and deterministic, like 1→2 / 2→3.
- **Sanitize:** keep `State` only if it is one of the 4 strings and `EggId` only if it matches `^egg_%d+$`.
  - Cross-check: `State == "Incubating"` requires an incubator whose `EggId` equals it.
  - If not, apply the recovery rules in H.
- **Forward-only:** a v3 server refuses a v4 profile ("stored schema version is newer"). **Publishing v4 needs "shut down all servers"** so no v3 server keeps writing. Owner approval is needed at publish time.

## G. Duplicate prevention
- The guarantee applies to **one EggId**, only while `State == "Incubating"`, and is consumed in the same write that clears the incubator (before the creature grant, matching today's exactly-once hatch).
- The grant step runs only when `State == "Pending"` and ends in `"Incubating"` in the same save, so a re-load can't grant twice.
- `Hatched` is terminal. No code path moves it back.
- The egg is the **existing** starter egg (converted, not added), so even a bug can't create an extra egg.

## H. Recovery (disconnect mid-flow, corrupt data)
| Situation | Result |
|---|---|
| Disconnect before the first save | Nothing persisted; next load is still `Pending` → grant runs once |
| Disconnect while incubating | ReadyAt is an absolute timestamp; the egg keeps incubating offline; HATCH works on return |
| Disconnect mid-hatch | Hatch is one server mutation + save; either the old state (egg still there) or the new state (Hatched + creature) persists |
| Storage full at hatch | Existing safe refusal: the egg stays, `State` stays `Incubating` |
| `Incubating` but no incubator holds `EggId` (corrupt/hand-edited) | Sanitize sets `State = "Hatched"` + warning. **No softlock:** the player still has the normal egg loop |
| `Pending` but the plot already has buildings (e.g. a v4 profile from a test build) | Skip incubator placement; put `egg_1` in `OwnedEggs` with the guarantee still attached via `EggId`, `State="Incubating"` when they incubate it |
| Starter incubator moved | Allowed. Selling is refused while the egg is inside (existing rule) |

## I. Test cases (to add before enabling)
1. v3 profile → v4: `WelcomeEgg.State == "Hatched"`; no buildings / eggs / currency change.
2. New profile: exactly 1 incubator `build_1` holding `egg_1`; `OwnedEggs` empty; `State == "Incubating"`.
3. Reload of 2 (twice): still exactly 1 incubator, 1 egg; no second grant.
4. 1,000 welcome hatches with a seeded RNG: results ∈ {Mossbit, Frostpup, Embercub}, always `newDiscovery == true`.
5. Welcome hatch when all Field species are discovered: falls back to the normal roll and still ends in `Hatched`.
6. A second, normal FieldEgg hatch after the welcome hatch uses the full table.
7. Storage full: refusal; `State` unchanged; the egg stays.
8. Corrupt `State` / `EggId` values → sanitized to `Hatched` with a warning.
9. `Incubating` without a matching incubator → `Hatched`, no crash.
10. Hatch twice in a row (replay): the second hatch is refused ("No incubating egg").
11. Sell the starter incubator while incubating: refused.
12. `EconomySimulation` + `Finish2C_Economy_Test`: unchanged except the incubator's 25 Cash (see J).
13. Version guard: a v4 profile loaded by a v3 schema module fails safely (existing guard test).

## J. Starter free egg: replace, keep, or convert?
| Option | Effect | Verdict |
|---|---|---|
| 1. Replace (remove `Eggs=1`, add a separate welcome egg) | Same net egg count, but two code paths touch the starter egg | — |
| 2. Keep as-is + add a welcome egg | **+1 free egg and +1 incubator**: economy and onboarding change twice | No |
| **3. Convert** the existing starter egg into the welcome egg | Same egg count as today; only change is the free incubator (+25 Cash of value) | **Recommended** |

**Recommendation: option 3 (convert).** It is the smallest change: the existing `egg_1` becomes the welcome egg and gets pre-incubated in a free starter incubator. The only economy delta is the free incubator (worth 25 Cash). The new `Incubate` guide step should then pay no extra Cash, or the free incubator simply replaces that step's reward.

## Owner decisions
1. Approve **schema v4** (the fields above) + **shutdown-on-publish**.
2. Approve **option 3**, including the free starter incubator.
3. Approve the **90 s** timer and the Mossbit / Frostpup / Embercub pool.

After approval: about 2–3 h of work (migration + service + 13 tests + guide copy + QA), behind `FeatureFlags.WelcomeEgg` and `OnboardingV2`.
