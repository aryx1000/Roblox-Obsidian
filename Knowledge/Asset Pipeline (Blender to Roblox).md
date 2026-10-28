---
tags: [knowledge, art, blender, roblox]
sources: [Grab & Run]
---

# Asset Pipeline (Blender to Roblox)

Back to [[Knowledge/Index|Knowledge]]. The source standard is [[GR_AssetStandards]], set by the Grab & Run Golden Toilet test.

## Units and axes
- 1 Blender unit = 1 stud.
- Blender: Z up, front faces −Y. Roblox: Y up, front faces −Z.
- **FBX export:** Forward −Z, Up Y, Apply Unit, Bake Space Transform, scale 1.0. Roblox Import 3D: Scale Unit = Stud.

## Pivots and naming
- Pivots: loot at the bounding-box **center**; environment and props at the **base center**.
- Names: `GR_<Category>_<Asset>`, materials `GR_M_<Name>`, textures `T_<Asset>_<Map>.png`. Work-only objects use `GT_*` / `LD_*` and are never exported.
- **For new games, swap the prefix** (e.g. `MPL_`, `SFH_`).

## Budgets (triangles)
| Class | Budget |
|---|---|
| Focal item | 3–5k |
| Other items | 1–3k |
| Vehicles | 4–8k |
| Building modules | 0.5–2k |
| Street props | 100–800 |

Textures: 512–1024, with shared atlases for the environment.

## Look and materials
- Stylized commercial look: chunky, readable silhouettes. No emissive on items; glow comes from game systems.
- **Gold recipe:** base #F2BE48, metal 0.85, rough 0.30, baked AO 0.72 plus a top-bright gradient. Pure metal 1.0 goes flat under Roblox sky reflections.
- One MeshPart plus one SurfaceAppearance per item when quality allows (one draw call). Bake Color (with AO), Metalness and Roughness at 1024.

## Override contract (gameplay-safe art swaps)
- A model named after the data id, with PrimaryPart = an invisible collision box "Body".
- The visual MeshParts don't collide, are massless, and are welded to Body.
- Removing the override restores the generated visual.

## Other projects
- [[Mutant Pet Lab]] and [[Shift From Hell]] currently use primitive parts; SFH documented that Blender wasn't needed.
