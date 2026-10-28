---
tags: [knowledge, roblox, multiplayer, testing]
sources: [Mutant Pet Lab]
---

# Multiplayer Testing in Studio

Back to [[Knowledge/Index|Knowledge]].

## Setup
- **Toolbar:** set the play mode to **Server & Clients**, set the player count with the spinner arrows, then press Play.
  - Typing into the count field doesn't stick; use the arrows.
- **Each window is its own RobloxStudio process with its own MCP `studio_id`.**
  - Identify roles with `RunService:IsServer()` and `LocalPlayer`.
  - Test players get **negative UserIds** (-1, -2…), and Mock stores isolate them.
- **The owner's Mac overloads:** keep at most **3 Studio processes**, and the Edit window counts. Ask before going to 4. Close kicked or stale clients and end the session when done.

## Controls
- **Test → Add Clients** (in a server or client window; disabled in the Edit window) adds the toolbar's *count*, not one client. Close extras immediately.
- **MCP `start_stop_play(false)` does not end** a Server & Clients session; use **Test → End Session**.
- **Leave test:** `LocalPlayer:Kick()` from the client gives a real PlayerRemoving.
- **Abrupt kill:** the server only notices after a timeout (about 40–60 s).
- To tell which PID is which client, busy-loop one client via MCP and watch `ps %cpu`.

## What to test (MPL M1–M9 matrix)
1. Plot allocation, owner signs, fresh profiles.
2. Simultaneous building stays per-player.
3. Visitor and cross-player attacks: explicit PlotId, id collisions (pet ids are per-profile, so `pet_1` exists for everyone), foreign creatures.
4. Shared stations: per-player cooldowns and cycles.
5. Concurrent duplicate mutation, purchase or claim: exactly one success.
6. Concurrent collect and hatch, plus replays.
7. Egg buys with forged price or id fields.
8. Research, Index and assignment isolation.
9. Leave/rejoin: plot released and reused, no stale references, the other player unaffected, server logs clean.

Related: [[Server Authority and Anti-Exploit]], [[Roblox Studio MCP Quirks]]
