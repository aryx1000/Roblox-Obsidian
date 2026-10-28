---
tags: [knowledge, tooling, roblox-studio, mcp]
sources: [Mutant Pet Lab, Shift From Hell]
---

# Roblox Studio MCP Quirks

Back to [[Knowledge/Index|Knowledge]]. These are working notes for driving Studio through the Roblox Studio MCP and computer use.

## Connection and limits
- **Calls over about 60 s time out and can drop the connection.** Keep loops short and use `task.wait` in chunks.
- **`screen_capture` in Play mode** times out and drops MCP. Read the UI tree instead, or use edit-mode previews.
- **Studio ids change** after reconnects. Re-run `list_roblox_studios`; "Place is not open" means it's at the start page.

## Modules and VMs
- Edit-mode `require` caches modules; test in a fresh Play server, or `require` a `:Clone()` for a quick check.
- The command bar and MCP `execute_luau` run in a **separate VM** from game scripts and can't reach game locals. Use a Studio-only BindableFunction bridge, and remove it afterwards.
- `loadstring` works in Edit, not in the Play server.

## Input
- **Proximity prompts:**
  - `prompt:InputHoldBegin()` from MCP only fires client-side.
  - Use `character_navigation` to the prompt, then `user_keyboard_input` with "E".
  - If navigation parks the character *inside* geometry, the prompt hides; approach from open ground.
  - Under **touch emulation** prompts become CoreGui tap buttons that can't be clicked, so do playthroughs under desktop emulation.
- **`user_mouse_input`:** x/y are GUI coordinates (the tool adds the 58 px inset). "hits CoreGUI" means a real overlap worth fixing.
- **ScrollingFrame rows:** scroll them into view before clicking.

## Computer use (desktop)
- Sometimes access is declined; don't nag. Dock/Finder access was denied, so reach hidden windows by minimizing the ones in front.
- **Never** use ⌘\` or Escape key presses in batches (they interrupt the tool), or `osascript` System Events (it hangs on a permission prompt).
- **Menus:** `app_menu` works on the main Studio process (File → Save to Roblox, Test → End Session). The newer Studio File menu says **"Publish"** and **"Publish As"**.
- **Self-modification guard:** editing `~/.claude` config (skills, CLAUDE.md, settings) is blocked for Claude; the owner must run such installs.

## Misc
- `CreateHumanoidModelFromDescription` rigs can render invisible in edit mode; convert them to Parts + Motor6D.
- New avatars use AnimationConstraint joints.
- `StudioDeviceSimulatorService:SetDeviceAsync` rejects device names; use the viewport device dropdown instead.

Related: [[Multiplayer Testing in Studio]], [[Testing and Validation]]
- **(2026-10-21)** The Studio id can change mid-session ("not connected" / "Place is not open") while the same Studio process keeps running. Call `list_roblox_studios` again; the place re-registers within a minute and Edit changes survive. Verify PlaceId/CreatorId before continuing.
- **(2026-10-21)** A `require` of a cloned tool module parented inside the DataModel shows up in exports. Leave the clone unparented (`require(module:Clone())` works when the module doesn't use `script.Parent`).
- **(2026-10-21)** `Source:gmatch("[^\n]*")` yields extra empty matches, so line numbers double and blank lines appear that aren't in the source. Use `"[^\n]+"` or plain `find` on exact text.
