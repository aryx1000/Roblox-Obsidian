---
tags: [knowledge, roblox, ui, mobile]
sources: [Mutant Pet Lab, Shift From Hell]
---

# Responsive Mobile UI

Back to [[Knowledge/Index|Knowledge]].

## Test only 4 representative sizes (the owner's rule)
- Small phone **667×375** (iPhone 7)
- Modern phone **874×402** (iPhone 17 Pro)
- One tablet (iPad Air 1180×820)
- Desktop **1366×768** (Average Laptop)

Use Studio's real **device emulator** (viewport toolbar: the phone/laptop icon, then the device dropdown). Prioritize function over pixels: overlaps, unreachable buttons, clipped scroll content, thumbstick/Jump conflicts, giant panels. Cosmetic spacing waits for the Figma polish phase.

## Bugs worth remembering (MPL Checkpoint E)
- **The camera reports a 1×1 viewport at startup.**
  - Controllers that computed `UIScale = clamp(ViewportSize.X/790, .58, 1)` once got stuck at minimum scale on desktop.
  - A responsive layer computed negative widths, giving invisible labels on tablets.
  - Fix: ignore viewports smaller than 200 px and re-run on `ViewportSize` change.
- **Profile branches must set every element.** A tablet branch that sets only some elements leaves stale phone values behind.
- **The Jump button sits bottom-right on touch devices.** Stack corner buttons above `TouchGui…JumpButton.AbsolutePosition.Y`.
- **Size modals from the usable height** (viewport − `GuiService:GetGuiInset()`), not the full viewport.
- **Close buttons on scaled-down panels shrink to about 18 px.** Grow them to about a 34 px effective target; the default `TextSize` is 8 if never set.
- **CoreGui (player list / top bar) covers the top-right corner.** Give big modals a second, footer CLOSE button.
- `ScreenOrientation = LandscapeSensor`, set in both the place and the client.

## Patterns
- **Clip vs scale (MPL 2026-10-21):** a "fit to screen" that clamps a frame's *Size* breaks offset-laid-out overlays; their children still overflow. For reveals and overlays, shrink the whole thing with a uniform UIScale: `min(scale, H*0.92/authoredH, W*0.94/authoredW)` (MPL `Kit` `FitUniform` attribute).
- **Celebration overlays are modals too:** hide the HUD, rails and guide while a reveal is up, but don't run the close-other-panels rule for it (the screen behind it must survive).
- Use a central responsive controller with profiles (PhoneLandscape / Tablet / Desktop). Major panels are mutually exclusive, and the HUD and guide hide while a modal is open.
- SFH: `Theme.lua` tokens mirror Figma variables and `UIKit.lua` holds the components; touch targets are 44 px or more after scaling; WCAG-AA colors; 13 px captions.
- **Measure, don't eyeball:** walk every panel's `AbsolutePosition/Size`, `TextFits`, ScrollingFrame canvas vs content, and `GetGuiObjectsAtPosition` at the Jump button.

Related: [[Testing and Validation]], [[Roblox Studio MCP Quirks]]
