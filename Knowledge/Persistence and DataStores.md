---
tags: [knowledge, roblox, datastore, persistence]
sources: [Mutant Pet Lab, Shift From Hell]
---

# Persistence and DataStores

Back to [[Knowledge/Index|Knowledge]]. Proven in [[Mutant Pet Lab]] (production since v88) and [[Shift From Hell]] (`SFH_PlayerData_v1`).

## Non-negotiables
- **Studio never touches live player data.**
  - Gate it in code, not in a setting: `RunService:IsStudio()` → an in-memory Mock store, whatever the config says (MPL's `PersistenceSelector`; SFH's `StudioUsesLiveData = false`).
  - Keep "Enable Studio Access to API Services" **off**.
  - Add defense in depth: the DataStore adapter itself refuses to open in Studio.
- **Pick the store in a pure function** of the config and environment (place id, owner id, owner type, isStudio). Unit-test it with fake environments.
  - The wrong place, owner or namespace **fails closed**: the server errors before touching any profile.
- **A dedicated, exact production namespace** per game (MPL: store `MPL_PlayerData_PROD_V1`, scope `Production`, keys `MPL_PROD_V1_<UserId>`). Never reuse dev or test namespaces.
- **Negative UserIds** (local Server & Clients test players) must never reach a real store.

## Load
- Use bounded retries. On failure the profile is **LoadFailed**: pause progression and refuse every save. **Never** create a default profile after a failed read; it would overwrite the real one later.
- Create a new profile only when the key is genuinely absent.
- Sanitize everything on load (NaN, negatives, unknown ids, bad types). A **future SchemaVersion fails closed** and is never overwritten.
- Make migrations idempotent and run them inside sanitize, with markers such as `EggInventoryMigrated`.

## Save
- **Optimistic revision:** `Revision` lives in the profile. Re-check it inside the `UpdateAsync` transform; a missing or newer revision becomes a **SaveConflict**, which blocks writes for the session instead of overwriting. SFH uses a session lock instead; both work.
- Corrupt stored data is never overwritten.
- Transient errors get bounded retries and the profile stays dirty.

## Concurrency bugs that bite only with a real store (found in MPL's audit)
1. **Lost changes during a save:** clearing `dirty` when a save *finishes* also drops changes made while it was in flight. Fix: a change counter; clear `dirty` only if nothing changed since the snapshot.
2. **Overlapping saves:** autosave + PlayerRemoving, or PlayerRemoving + BindToClose, race on the same revision, produce a false conflict, and drop the newest data. Fix: **one save per profile at a time**; later callers wait, then save against the new revision.
3. **Leaving during load** leaves a stale cached record. Fix: release it when `player.Parent ~= Players` after the load.
4. **Shutdown:** `BindToClose` saves **in parallel** within the ~30 s budget.

## Wiring checklist
- [ ] Load on PlayerAdded (and for players already present at startup).
- [ ] Autosave on a loop (MPL: 120 s), dirty profiles only.
- [ ] PlayerRemoving: save, then release the plot and record.
- [ ] BindToClose: parallel SaveAll.
- [ ] Every gameplay mutation marks the profile dirty (ticks too).
- [ ] Session-only state is deliberate and documented (e.g. a "this session's supply" counter).
- [ ] Tests use fakes or Mock only: fail-closed load, bounded retries, conflicts, in-flight changes, overlapping saves, a full round trip, sanitize, the future-schema guard.

## Leaderboards (SFH 0.15.0)
- Use an OrderedDataStore that mirrors the authoritative profile value.
- Encode tiebreaks into the value, e.g. `score × 1e9 + (999,999,999 − secondsSinceEpoch)`, clamped below 2^53.
- `UpdateAsync` keeps the higher value. Writes are queued and gated by request budget.

Related: [[Release and Publish Safety]], [[Testing and Validation]]
