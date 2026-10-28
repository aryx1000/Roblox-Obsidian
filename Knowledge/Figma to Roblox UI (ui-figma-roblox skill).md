---
tags: [knowledge, ui, figma, roblox, tools]
sources: [ui-figma-roblox skill]
installed: 2026-10-20
---

# Figma to Roblox UI (ui-figma-roblox skill)

Back to [[Knowledge/Index|Knowledge]].

## Context
On 2026-10-20 the owner asked Claude to install the community skill **ui-figma-roblox** (from `github.com/grim-technologies-arch/ui-figma-roblox`, commit `99d2861`) and use it for our games. The skill teaches how to design layered "stud-style" Roblox UI in Figma (panels, headers, product cards, buttons, currency HUD) and port it to a native `ScreenGui`. It is based on Kek's tutorial *The Greatest Stud UI Tutorial on Roblox (w/ Figma)*.

- **Installed at:** `~/.claude/skills/ui-figma-roblox/` (329 MB, mostly art). It loads automatically as the `ui-figma-roblox` skill. Manual copy, no npx installer run; the `.installed-commit` file records the version.
- **Update:** re-clone the repo into a scratch folder, review the diff, then `rsync -a --exclude .git` over the install.
- **Needs:** the Figma MCP for building in Figma (load the `figma-use` skill before any `use_figma` call). The Roblox Studio MCP is only needed for the port.

## What's in it
| Path (inside the skill) | Use |
|---|---|
| `SKILL.md` | Workflow: large forms → details, one visual language, repeat cards systematically, review at real size, label the deliverable honestly |
| `references/design-workflow.md` | Layer recipes (panel, header, extrusion, studs, hero card, nav, side buttons, currency), layer tree, review checklist, failure table |
| `references/asset-library.md` | Asset inventory and lookup commands |
| `assets/kek-ui-essentials/` | 106 images: `kek_stud.png`, halftones, rays, sparkles, slashes, chains, flames, smoke |
| `assets/ui-resources/` | 975 files (Effects, Backgrounds, Renders, Textures, Faces, Brushes, Icons, 6 UI sounds) + `MANIFEST.csv` |
| `examples/stud-shop/` | Full worked shop: Figma scripts, `bake_roblox_studs.py`, Luau `build_shopgui.luau` + `ShopController.client.luau`, renders |

**Browse the images in the vault:** [[UI Art Library]] (1,087 images copied into `Knowledge/UI Art Library/`, with a gallery note per pack/category).

Find art with the manifest, not by listing folders, and open the image before choosing it:
```bash
grep -i "halftone" ~/.claude/skills/ui-figma-roblox/assets/ui-resources/MANIFEST.csv | cut -d, -f2,3,5,8
```

## Lessons: building the look (Figma)
- **Depth:** duplicate the face, nudge it down, and fill it darker (about ×0.62; ×0.45 on buttons for a thick bottom edge). Keep the offset small and consistent (10 px for cards and headers, 6 px for buttons).
- **Outlines:** Outside strokes, 3–5 px, one near-black colour everywhere.
- **Button effects:** a light inner rim (Inside stroke 3–4 px), a darker bottom lip (~20 % of height) with a 2 px light line on top, masked diagonal sheen stripes, and faint studs that fade upward.
- **Hard shadows** on text and icons: 0 blur, 100 % opacity, small offset.
- **Texture with restraint:** tile studs (never stretch them), lower their contrast, and keep them out from under small text.
- **After scaling** a duplicated card, re-check stroke widths, shadows and text sizes; Figma's Scale tool changes them.
- **Bitmap icons** get a rectangular stroke. Use a vector icon when the outline must follow the silhouette.

## Lessons: porting to Roblox (verified in Studio by the skill author)
- **No Overlay blend mode.** Bake the stud tile into white-alpha highlights + black-alpha shadows (`bake_roblox_studs.py`). It then reads like Overlay on any colour.
- **`UIGradient.Transparency` does not fade a tiled `ImageLabel`**, even inside a `CanvasGroup`. Bake the fade into the image and use `ScaleType.Stretch`. Check fades by measuring pixel contrast in a PNG capture, not by eye on a JPEG.
- **Outlines:** `UIStroke` (Border mode) draws outside like Figma's Outside stroke. Use `LineJoinMode.Miter` for square corners.
- **Hard text shadow:** a black duplicate `TextLabel` nudged down, as a **sibling**. Under `ZIndexBehavior.Sibling` a child always draws above its parent.
- **`ClipsDescendants` does not clip rotated children.** Use a `CanvasGroup` for stripes, halos and sheen.
- **Hover scale from centre:** set `AnchorPoint = (0.5, 0.5)` and move `Position` to the centre before adding a `UIScale`.
- **Shine sweep:** a white `Frame` with a narrow-band `UIGradient` (Rotation 25); tween its `Offset` from (-1, 0) to (1, 0).
- **Uploading local PNGs:** serve them with `python -I -m http.server 8765 --bind 127.0.0.1`, pass `http://localhost:8765/x.png` to the Studio MCP `upload_image`, then stop the server. Asset ids in the example belong to the author's account; re-upload for our games.
- **Figma `get_screenshot` exports at 1×.** For a bigger export, scale a temporary clone, export it, then delete it. The Figma Starter plan has an MCP call limit, so batch calls.

## Licensing (important before a release)
- The skill's own text and scripts are MIT.
- **The bundled art is not licensed to us.** The Kek pack shipped without a licence. UI Resources is a community directory, and "free" there is not permission to use the art in a commercial game. The Robux icon and Roblox renders are Roblox IP.
- **Rule:** use bundled art for **mockups and reference only**. Before any of it ships in a game, record its title, creator and `source_url` from `MANIFEST.csv`, and get the owner's OK on the rights. Prefer making our own textures (for example, re-bake our own stud or halftone tile).

## Not our owner's preferences
`examples/stud-shop/README.md` has a "User preferences learned" section. Those are **the skill author's client's preferences** (square corners, translucent frame, animate only buy buttons). They are not [[Working With the Owner|our owner's]] rules and never override a game's approved decisions.

## Applies to
- Any Roblox game UI: shops, HUDs, menus, currency displays, button systems.
- **[[Mutant Pet Lab]]:** the technique layer only. Approved **UI Direction C** stays the visual identity, so the stud look is not adopted by default. See [[UI - Figma TODO#Toolkit: ui-figma-roblox skill (installed 2026-10-20)]].
- Pairs with [[Responsive Mobile UI]] (4 test sizes, touch targets) and [[Roblox Studio MCP Quirks]].
