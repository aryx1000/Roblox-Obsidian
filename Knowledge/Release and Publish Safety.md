---
tags: [knowledge, release, roblox, safety]
sources: [Mutant Pet Lab, Shift From Hell]
---

# Release and Publish Safety

Back to [[Knowledge/Index|Knowledge]].

## Approval gates
- **Separate steps:** creating a place ≠ publishing a build ≠ production cutover ≠ visibility changes. **Each needs its own explicit owner approval.**
- **Never publish** SHIFT FROM HELL!, GRAB N RUN! or another experience by mistake.
  - Verify **PlaceId, CreatorId, CreatorType and the group name** (via GroupService) right before any save or publish.
  - Don't trust window titles; MPL is still named "Untitled Experience" on Roblox.
- **Save ≠ Publish.**
  - "No changes to the place detected" on save means the Roblox copy already matches.
  - Publish logs "Place published… Add publish notes to vN"; record vN.

## Unexpected publishes
- MPL v83 was published by something other than Claude while "OP Auto Clicker" was running and Studio was in use. Watch Output for "Place published" lines you didn't cause, and report them.
- Auto-clickers or another person in Studio can also select or move things. Before saving, diff the instance tree against the last snapshot.

## Before every release
- [ ] All tests pass in a fresh Play server.
- [ ] 0 game errors on server and clients.
- [ ] No temporary hooks, attributes or MPL_TEMP sources (search sources and names).
- [ ] Only the known remotes.
- [ ] HTTP off; Studio API access off.
- [ ] Persistence mode as intended (Studio is always Mock).
- [ ] Byte-level diff vs the previous snapshot; every changed file has a reason.
- [ ] Snapshot plus git commit, then Save, then (if approved) Publish, then record the version.

## Rollback
- Keep a known-good tag or version: SFH `known-good-two-experience-v0.12.0`, Lobby version history; MPL dated snapshots plus `RESTORE.md`.

Related: [[Persistence and DataStores]], [[Local Backups and Snapshots]]
