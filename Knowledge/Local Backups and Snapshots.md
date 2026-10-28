---
tags: [knowledge, workflow, backup]
sources: [Mutant Pet Lab, Shift From Hell]
---

# Local Backups and Snapshots

Back to [[Knowledge/Index|Knowledge]].

## Two workflows that work
- **Disk is the source (SFH):** code lives in `src/`; `tools/make_manifest.py` plus a temporary local HTTP server and `tools/sync.lua` push it into Studio. HttpEnabled is on only during the sync.
- **Studio is the source (MPL):** Studio is authoritative and the local folder is a *verified export*.
  - An in-Studio exporter prints base64 chunks (`MPLX|id|seq|…`) to Output. They land in `~/Library/Logs/Roblox/*Studio*.log`, and `tools/extract_studio_export.py` reassembles them.
  - `tools/snapshot.py` verifies the script count, bytes and a checksum (`h=(h*31+byte)%2147483647` summed over scripts) against Studio, writes the manifest, and refuses to overwrite.
  - `make_restore_chunks.py` rebuilds missing instances (`RESTORE.md`).

## Habits
- Snapshot at every checkpoint with dated, immutable folders, then commit to git.
- Record the test count, checksum, save and publish state, and known issues in the manifest and the state file (`CLAUDE_PROJECT_STATE.md`).
- Before risky changes, confirm Studio is byte-identical to the last snapshot.
- Keep large exports out of Obsidian; link docs only.

Related: [[Release and Publish Safety]]
