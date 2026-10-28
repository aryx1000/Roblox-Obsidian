---
type: planning
game: "[[Mutant Pet Lab]]"
area: creatures
status: ready
updated: 2026-10-22
tags:
  - mutant-pet-lab
  - planning
  - creatures
---
# Roster Conversion Plan (remaining 29 species), Blender production

> [!info] Gate
> Production style: the **seven Blender body-family anchors** ([[Design Decisions#Production creature style: Frostpup + Mossbit Blender anchors approved]]). The roster starts after the 7-anchor review / style lock. **Not started.**

**Per species (no A/B/C round for normal species):**
1. Specimen sheet spec (R15/R16 layout; R17 = composition reference only).
2. Blender model in its family's surface treatment.
3. Export the FBX and add it to `MutantPetLab/blender/IMPORT_QUEUE.md`.
4. The owner bulk-imports the queue.
5. Fit: Roles, LOD, the Roblox-part face, Luminous tint.
6. Validate: pen, 30 studs, Index, viewer, Standard + Luminous, cost.

**Explicit owner review:** Legendary · Mythic · secret · Chimerax/Hybrid · new anatomy · new body family · major MeshPart exceptions.

**Family anchors and surface treatment:**

| Family | Anchor | Surface |
|---|---|---|
| Gel | Slimelet | soft rounded volume, single translucent part |
| Critter | Frostpup | broad animal planes; crystal/ice faceting where the material calls for it |
| Hopper | Pebbletoad | soft animal planes + faceted mineral accents |
| Flyer | Sparkbug | clean segmented planes, one wing mesh per side |
| Sprout | Mossbit | layered leaf/petal planes |
| Wisp | Magmawisp | floating layered forms, orbit parts as separate meshes |
| Shellback | Rockling | soft critter + strongly faceted shell |

**Targets:** Common–Rare ≤ 650 tris / ≤ 12 meshes · Epic ≤ 750 / ≤ 14 · Legendary/Mythic ≤ 900 / ≤ 16. Face parts are extra (≈ 10 parts). Animation ≤ 30 µs close per creature.

**Variants:** Luminous = the species' signature organ glows in a **saturated species hue** (`LuminousTint` / `LuminousMix`; pale tints bloom white). The body stays matte; other accents opt out. Chromatic / Prismatic: existing rules.

## Species by family

### Gel
| Species | Rarity | Lineage / eggs | Silhouette + signature anatomy | Mutant feature | Luminous tint | Animation | Tris / meshes | Review |
|---|---|---|---|---|---|---|---|---|
| **Gloamgel** | Uncommon | Slimelet + Mossbit · Unstable 16% | Dusky violet gel dome with moss tufts on top, puddle skirt | Inner glow spots visible through the gel | violet (170,90,255) | Gel | 550 / 8 | no |
| **Tidegill** | Rare | Rockling + Sparkbug · Unstable 14% | Teal aquatic gel with 3 frilled gill fans on each side, droplet crest | Glassy gill membranes | aqua (40,220,230) | Gel + gill sway (Crown) | 600 / 9 | no |
| **Aquaflux** | Epic | Circuitfin + Tidegill · Conductive 11% | Blue liquid body held in shape by 2 floating field rings | Electric field rings (Orbit meshes) | electric blue (60,150,255) | Gel + Orbit rings | 700 / 10 | no |

### Sprout
| Species | Rarity | Lineage / eggs | Silhouette + signature anatomy | Mutant feature | Luminous tint | Animation | Tris / meshes | Review |
|---|---|---|---|---|---|---|---|---|
| **Bloomtail** | Uncommon | Sparkbug + Mossbit · Botanical 26% | Sprout body + a long curling tail ending in a big flower | Tail flower that opens (petal mesh) | magenta (255,70,200) | Sprout + Tail | 620 / 11 | no |
| **Thornling** | Uncommon | Mossbit + Embercub · Botanical 24% | Low crawling sprout, rows of soft rounded thorns down the back | Bioluminescent thorn tips | lime (150,255,60) | Sprout (crawl) | 600 / 10 | no |
| **Radisprout** | Rare | Slimelet + Sparkbug · Botanical 12% | Round radish-bulb body, leafy top tuft, root feet | Glowing nutrient bulb in the chest | warm yellow (255,210,40) | Sprout | 560 / 9 | no |
| **BrimstoneBloom** | Epic | Embercub + Bloomtail · Thermal 11% | Upright flower-creature, red/orange petal collar, ember pollen | Heat-opening petals | ember orange (255,110,30) | Sprout | 700 / 12 | no |
| **Toxibloom** | Epic | Miremoth + Bloomtail · Unstable 14% | Warning-coloured (purple/green) petal hood, bulb body | Stable toxic core | toxic green (120,255,40) | Sprout | 700 / 12 | no |
| **Auroroot** | Legendary | Radisprout + Cryolume · mutation | Tall botanical sentinel with aurora-coloured hanging roots | Aurora roots | aurora (90,255,200) | Sprout (tall) | 850 / 14 | **yes** |

### Critter
| Species | Rarity | Lineage / eggs | Silhouette + signature anatomy | Mutant feature | Luminous tint | Animation | Tris / meshes | Review |
|---|---|---|---|---|---|---|---|---|
| **Embercub** | Rare | Field 7.5% · Thermal 40% | Feline cub, flame-tipped tail and ear tufts | Ember core chest (**currently falls back to the server ball, so this is the top Critter priority**) | ember (255,120,30) | Critter | 650 / 12 | no |
| **Cinderhorn** | Rare | Rockling + Embercub · Thermal 36% | Stocky grazer with a mineral horn crown | Glowing crown | lava (255,90,40) | Critter (heavy) | 650 / 12 | no |
| **Voltusk** | Epic | Sparkbug + Circuitfin · Conductive 13% | Grazer with two arcing static tusks | Static tusks | electric (80,200,255) | Critter (heavy) | 720 / 13 | no |
| **Sporephant** | Epic | Fungloom + Pebbletoad · mutation | Fungal giant with a short trunk | Trunk sensory organ | spore teal (60,230,180) | Critter (giant) | 750 / 14 | **yes** (new anatomy: trunk, size) |
| **ObsidianLynx** | Legendary | Cinderhorn + Prismaclaw · mutation | Volcanic lynx with faceted obsidian plates | Obsidian plates | magma red (255,60,40) | Critter | 880 / 15 | **yes** |

### Hopper
| Species | Rarity | Lineage / eggs | Silhouette + signature anatomy | Mutant feature | Luminous tint | Animation | Tris / meshes | Review |
|---|---|---|---|---|---|---|---|---|
| **Glacierbit** | Rare | Slimelet + Frostpup · Cryogenic 36% | Small round hopper with faceted ice body plates | Ice plates + ice-mote trail | ice cyan (40,190,255) | Hopper | 600 / 10 | no |
| **Fluxaroo** | Epic | Slimelet + Magmawisp · mutation | Kangaroo-like hopper with a glowing biomass pouch and balance tail | Rearranging pouch | magma gold (255,170,40) | Hopper + pouch | 750 / 13 | **yes** (new anatomy) |

### Flyer
| Species | Rarity | Lineage / eggs | Silhouette + signature anatomy | Mutant feature | Luminous tint | Animation | Tris / meshes | Review |
|---|---|---|---|---|---|---|---|---|
| **Circuitfin** | Rare | Sparkbug + Frostpup · Conductive 36% | Fish-like flyer with fin-wings | Charged fins | electric (80,200,255) | Flyer | 650 / 11 | no |
| **Miremoth** | Rare | Mossbit + Frostpup · Unstable 14% | Velvety moth, broad round wings | Fungal wing spots | spore green (120,255,120) | Flyer (slow flap) | 650 / 11 | no |
| **Tempestrix** | Legendary | Voltusk + Cryolume · mutation | Large electro-cryo bird/flyer | Quiet lightning aura | storm blue (80,160,255) | Flyer (large) | 900 / 16 | **yes** |

### Wisp
| Species | Rarity | Lineage / eggs | Silhouette + signature anatomy | Mutant feature | Luminous tint | Animation | Tris / meshes | Review |
|---|---|---|---|---|---|---|---|---|
| **Fungloom** | Rare | Sparkbug + Embercub · Botanical 8% | Floating mushroom-cap cloud with a curious nucleus eye | Nucleus | spore purple (180,90,255) | Wisp | 600 / 10 | no |
| **Cryolume** | Epic | Frostpup + Gloamgel · Cryogenic 13% | Icy membrane wisp with faceted ice shards orbiting | Stored light in ice | ice blue (60,200,255) | Wisp + Orbit | 700 / 12 | no |
| **Geodewisp** | Epic | Rockling + Prismaclaw · mutation | Wisp around a rotating crystal lattice | Faceted lattice (Orbit) | crystal violet (150,110,255) | Wisp + Orbit | 720 / 12 | no |
| **Nucleonox** | Legendary | Toxibloom + Radisprout · mutation | Shielded lab organism | Shielded core | toxic lime (150,255,40) | Wisp | 850 / 14 | **yes** |
| **Biolume** | Mythic (secret) | Aquaflux + Fungloom | Mythic pulse organism | Activity-reactive light | bio cyan (40,255,220) | Wisp | 900 / 15 | **yes** |
| **Nullmorph** | Mythic (secret) | Tempestrix + Auroroot | Refraction-only organism | Shifting refraction (glass) | prism (200,140,255) | Wisp | 850 / 14 | **yes** |
| **Quasipod** | Mythic (secret) | Biolume + Nullmorph | Phase-mutant whose form changes | Form change (needs design) | phase pink (255,90,200) | Wisp | 900 / 16 | **yes** |

### Shellback
| Species | Rarity | Lineage / eggs | Silhouette + signature anatomy | Mutant feature | Luminous tint | Animation | Tris / meshes | Review |
|---|---|---|---|---|---|---|---|---|
| **Prismaclaw** | Epic | Frostpup + Embercub · Cryogenic 11% | "Crystalline hunter": shellback with claws and a hunter stance | Refractive crystal shell | prism blue (90,170,255) | Shellback + claws | 750 / 13 | **yes** (anatomy may break the baseline) |
| **FerriteDrake** | Legendary | Geodewisp + Voltusk · mutation | Mineral drake | Magnetic core | magnet red (255,70,70) | new rig | 900 / 16 | **yes** |

### Hybrid / exceptional
| Species | Rarity | Lineage | Notes | Review |
|---|---|---|---|---|
| **Chimerax** | Mythic (secret) | Fluxaroo + Nucleonox | Many-lineage mutant mixing several family parts; new rig; ≤ 900 tris / 16 meshes | **yes** |

## Batches
1. **Batch 1: Gel + Sprout (owner preference).** Gloamgel, Tidegill, Aquaflux, Bloomtail, Thornling, Radisprout, BrimstoneBloom, Toxibloom. 8 species, none needs explicit review. Auroroot (Legendary) is held for Batch 4.
2. **Batch 2: Critter + Hopper + Flyer (normal).** **Embercub** (fallback ball today), Cinderhorn, Voltusk, Glacierbit, Circuitfin, Miremoth.
3. **Batch 3: Wisp (normal).** Fungloom, Cryolume, Geodewisp.
4. **Batch 4: review species, one concept sheet each:** Prismaclaw, Fluxaroo, Sporephant, then the Legendaries: Auroroot, ObsidianLynx, Tempestrix, Nucleonox, FerriteDrake.
5. **Batch 5: Mythic / secret (each reviewed):** Biolume, Nullmorph, Quasipod, Chimerax.

Each batch: model everything → one queue → owner bulk import → fit + validate → one review → save/snapshot.
