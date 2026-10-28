---
tags: [knowledge, roblox, testing]
sources: [Mutant Pet Lab, Shift From Hell]
---

# Testing and Validation

Back to [[Knowledge/Index|Knowledge]].

## Automated tests
- **Run them in a fresh Play server.** Edit-mode `require` caches modules, so after edits run `require(ServerStorage.UnitTest.RunUnitTest)(nil,10)` in a new Play session.
- **Make logic injectable:** pass `deps.random`, `deps.clock` and adapters so tests stay deterministic, and keep production paths separate.
- **Pure functions for rules** (selectors, `BuildEntries`, `applyInbox`, `parseConfig`) are easy to test exhaustively.
- **Red then green:** reproduce a bug as a failing test first. SFH keeps "negative controls", deliberately broken variants that must FAIL.
- **Never weaken a test.** A test made obsolete by an intended change gets an equivalent or stronger replacement (e.g. a hard-coded `+16` became `2*SampleResearch`).
- **Graph and economy tests:** reachability closure over recipes, eggs, research and stages; no cycles; a minute-step economy simulation with sane milestone bounds.

## Playthroughs
- Run a **fresh-profile critical path** through real input: UI clicks, walking up to prompts and pressing E, and the same remotes the UI calls.
- **Accelerators come only after the early loop is proven.** Use a Studio-only `BindableFunction` in ServerStorage, between `MPL_TEMP` markers, gated by `RunService:IsStudio()`, and remove it before every snapshot. Verify removal by a byte-identical diff.
- **Never rig RNG for a "legit" result.** Earn rare outcomes naturally or test the probability path separately (MPL: a Botanical egg naturally hatched a Radiant Fungloom).
- **Snapshot and diff** before and after, at both script and instance-tree level, so every changed file has a reason.

## Honesty labels (SFH)
- Mark every claim as VERIFIED, IMPLEMENTED-NOT-VERIFIED, KNOWN DEFECT, NOT IMPLEMENTED or BLOCKED.
- Evidence types: CODE / MEM / SIM / LIVE / DASH.
- Mock is never "live".

## Performance
- MPL benchmark: 48 creatures / 8 properties / 240 ticks, mean ~0.17–0.30 ms.
- The first run after load or on a busy Mac reads high. Re-run before calling a regression; check `vm.loadavg`.

Related: [[Multiplayer Testing in Studio]], [[Responsive Mobile UI]], [[Roblox Studio MCP Quirks]]
