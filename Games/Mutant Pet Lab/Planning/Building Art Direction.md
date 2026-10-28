---
type: planning
game: "[[Mutant Pet Lab]]"
area: buildings
status: candidate
updated: 2026-10-20
tags:
  - mutant-pet-lab
  - planning
  - buildings
---
# Building Art Direction

> [!success] Budget route B APPROVED (owner, 2026-10-20)
> **Server / shared geometry** for gameplay-relevant architecture; **client-local visual detail** for decorative, non-interactive polish where appropriate. **Do not raise the global part budget casually.** [[Design Decisions#Building budget: Route B (owner, 2026-10-20)]] The per-building designs below are still **candidates** (not built).

> [!info] Design status: candidate (2026-10-20 offline pass)
> Implements the approved identity: **cozy bio-lab ranch with a mutant-lab identity** ([[Design Decisions#Overall direction: cozy bio-lab ranch with a mutant-lab identity]]). The map **layout** is approved and stays: plot origins, bounds and station interaction positions are frozen ([[Design Decisions#Map: performance and frozen-geometry constraints]]). This pass is about **what the buildings look like**.

## The core problem (verified in snapshot `2026-10-16_creature_c1`)
- **The Egg Research Center, Mutation Lab, Research Center, Supply Store and Mutation Museum all use the same booth template:**
  - a 36×28 floor, a 36×17 back wall, two 15-tall side wings and a flat 40×14 canopy;
  - a 31×7 sign and two neon light strips;
  - colours: mint walls (196,218,210) under a dark teal canopy (25,51,59).
  - From a plot path **they are the same building with different signs.**
- **Stations** (Mutation Machine, Research/Upgrade/Supply stations) are a console box + base + screen + neon button + glow core: readable, but generic sci-fi.
- **Budget:** the Workspace holds **1,947 instances against the approved ~2,000 cap**, and imported 3D models aren't allowed this phase. An art pass is **impossible without a budget decision** (below).

## Budget options (decided: **B**)
| Option | How | Pros | Cons |
|---|---|---|---|
| **A. Rebuild inside the cap** | Replace each booth's ~8–13 parts with a new silhouette; remove decor elsewhere (e.g. 114 Wayfinding parts) | No rule change | Little room; trade-offs everywhere |
| **B. Client-side decorative layer** (**approved 2026-10-20**) | Static silhouette parts stay server-side; **detail props are spawned client-side** from templates (like the creature display layer), culled by distance | Rich detail without touching the server count; distance-culled on phones | A new client system; needs a perf budget |
| **C. Raise the cap / allow MeshParts** | Owner decision: raise to e.g. 3,000, or allow a few Blender meshes for hero buildings | Best quality per instance (one mesh = one instance) | Changes approved constraints; needs a phone test |

Every per-building budget below uses **B**: a **server shell ≤ the current count** (anything players touch, stand on or interact with) + a **client detail layer** shown within ~120 studs (decorative only, non-collidable, not gameplay-relevant).

## Shared building language
- **Silhouette first:** each building gets **one unmistakable top shape** visible from any plot: a dome, an egg roof, a tower, a greenhouse, a crane, an arch.
- **Material hierarchy:**
  - **Base:** warm wood / stone (cozy).
  - **Middle:** pale lab panels with rounded edges.
  - **Top:** glass (domes, tanks).
  - **Accents:** the building's function colour as Neon trim, **max 2 Neon strips**.
- **Colour hierarchy:**
  1. Function colour (egg orange, mutation violet, research teal, supply green, upgrade gold, showcase pink, matching the UI accents).
  2. Neutral lab mint / cream.
  3. Wood / stone.
  4. Dark teal outline elements (canopy edges, frames) that echo the UI's ink outlines.
- **Signage:** a **chunky outlined name sign** on the roofline (readable from 60+ studs) + a **floor-painted word** at the interaction spot ("EGGS", "MUTATE", "RESEARCH") + a pictogram (egg / DNA / microscope). Supported by R5/R6/R8 ([[MPL Visual Fingerprint#Buildings / World]]).
- **Detail density:** **low on the shell, high at the counter** (where the player stands). Detail clusters: jars, tanks, cables, crates, plants, lab stools.
- **Mobile readability:** silhouette + sign + floor word must read at **667×375 from the plaza**; no small text on buildings except the counter screen.
- **Lights:** ≤ 1 PointLight per building (most glow from Neon + SurfaceLights is cheaper).

**Not to copy (approved negative rules 2026-10-20):** **repeated booth-shaped buildings**, a generic sci-fi lab look (chrome / hospital-white boxes), excessive neon / cyberpunk cities, gritty realism, "polish" that is only gradients/colours, the wood/parchment shop skin of the UI references, any reference's actual buildings. See [[Do Not Copy]].

**References:**
- ![[slime-rancher-2-conservatory-corrals.jpg|300]] ![[slime-rancher-2-conservatory-dome-tech.jpg|300]] Slime Rancher 2's Conservatory: **a glass greenhouse dome over corrals, gardens and tech poles** is the closest public example of a cozy bio-lab ranch.
- ![[slime-rancher-2-glass-dome-lab.jpg|300]] ![[my-singing-monsters-breeding-structure.jpg|300]] ![[my-singing-monsters-tech-island-machine.jpg|300]]

---

## Per building
### Egg Research Center
Full design: [[Egg Research Center Redesign]]. Role (approved): **teaches and sells later eggs**; the welcome hatch happens on the player's own plot.
- **Weakness:** a booth; 3-stud glass balls on cube pedestals.
- **Silhouette:** an **egg-shaped glass dome roof** over a round hatchery hall.
- **Budget:** shell ≤ 46 (current) + client layer ≤ 120 parts.

### Mutation Machine building (Mutation Lab court)
| | |
|---|---|
| Current weakness | The same booth as everything else + a console box; the cable to the Reactor is the only link to the landmark |
| Desired silhouette | A **twin-pod chamber**: two glass specimen tubes (the parents) feeding a central fusion tank, under an arched roof with a **crane arm / pipe crown** pointing toward the Reactor |
| Materials | Riveted metal base, glass tubes, wood floor decking, violet Neon fluid |
| Colour | Mutation violet → green gradient fluid; mint panels; dark teal frame |
| Signage | "MUTATION LAB" roof sign + a DNA pictogram + floor word "MUTATE" in front of the console |
| Props / detail | Specimen jars, bubbling tubes, cable bundles toward the Reactor, a lab-coat rack |
| References | [[Mutation Storyboard]] (the parent pods are where the dissolve happens) |
| Not to copy | A horror lab, a mad-scientist Frankenstein look |
| Mobile | The tubes glow violet: readable from the plaza even when the sign isn't |
| Budget | Shell ≤ 24; client layer ≤ 60; ≤ 1 PointLight |

### Research Terminal area (at the Reactor front, approved move)
| | |
|---|---|
| Current weakness | A console box on the Reactor dais; the Research Center booth is separate and empty |
| Desired silhouette | A **curved "observatory desk"**: a raised semicircular console with **3 tall holo-panels** showing research nodes (the hex board motif from R7), under a small **telescope/antenna** |
| Materials | Pale lab panels, glass panels, brass/wood trim |
| Colour | Research teal; gold for completed nodes |
| Signage | "RESEARCH" + a microscope pictogram; the hex panels themselves read as research |
| Detail | Notebooks, a specimen microscope, a hex floor inlay |
| Not to copy | Generic hologram UI walls |
| Mobile | The hex-panel silhouette, not text |
| Budget | ≤ 30 server (shared with the Reactor area) + ≤ 40 client |

### Specimen Supply
| | |
|---|---|
| Current weakness | A booth + a console with a canister |
| Desired silhouette | A **field-station wagon / greenhouse cart**: a covered cart with crates of specimen canisters and a hanging lantern, a **chute** where the claimed canister drops |
| Materials | Wood planks, canvas canopy, glass canisters |
| Colour | Supply green; cream canvas |
| Signage | "SPECIMEN SUPPLY" on the canopy; a cooldown shown on a canister gauge (world-readable) |
| Detail | Crates, nets, labels, a small flag |
| Not to copy | A Robux-shop stall look |
| Budget | ≤ 20 server + ≤ 40 client |

### Upgrade Station
| | |
|---|---|
| Current weakness | A generic console |
| Desired silhouette | A **workshop bench with a gantry crane** holding a part, a tool wall, and a gear sign |
| Materials | Wood bench, metal gantry, pegboard |
| Colour | Upgrade gold; dark teal metal |
| Signage | "UPGRADES" + a wrench/gear pictogram |
| Detail | Tool silhouettes, spare parts, a blueprint on the wall (a nod to the template-sheet style) |
| Budget | ≤ 20 server + ≤ 40 client |

### Specimen Showcase
| | |
|---|---|
| Current weakness | A pad + dais + two pylons + header: a stage without an audience |
| Desired silhouette | A **museum display ring**: a raised round dais under a **glass display dome** with a halo light ring, flanked by placard stands |
| Materials | Polished stone, glass dome, gold trim |
| Colour | Showcase pink + gold (prestige) |
| Signage | "SPECIMEN SHOWCASE"; placards show species name + rarity (SurfaceGui) |
| Ties to | [[Plot Decoration and Visiting]] (the server's best creatures), [[Variant Visual Language]] (shown under a dome light) |
| Budget | ≤ 13 server (current) + ≤ 30 client |

### Player plot entry / gate language
| | |
|---|---|
| Current weakness | Two pillars + lights + an "AVAILABLE RESEARCH PROPERTY" sign; the plot doesn't say whose it is or what's inside |
| Desired silhouette | A **ranch arch gate**: two posts + an arched beam with a **nameplate** (owner name) and a **lab crest** (shows the plot's featured creature icon or the player's level) |
| Materials | Wood posts, metal arch, a lantern pair |
| Colour | Neutral wood + the plot's chosen accent (a decoration choice later) |
| Signage | "[Name]'s Lab" + level; expansion stage signs keep "STAGE n" but move to small posts |
| Budget | ≤ 85 per plot today (unchanged); the arch replaces the pillars (+0); the crest is client-side |
| Decorations | Future player decorations are a **separate category** from these functional structures ([[Plot Decoration and Visiting]]) |

### Ranch structures (player-built: Containment Pen, Feeder, Crop Bed, Incubator, Bio Lantern)
| | |
|---|---|
| Current weakness | Functional placeholders |
| Desired silhouette | **Pen:** low wooden corral + a glass-panel side + a habitat floor insert (puddle, soil, rock, ice per habitat). **Feeder:** a hopper with a visible food level. **Crop bed:** raised wooden bed with visible crop stages. **Incubator:** glass dome on a warm base (lights pulse while incubating). **Bio Lantern:** a glowing seed-pod lamp |
| Materials | Wood, glass, soft metal |
| Colour | Neutral; the habitat colour inside the pen |
| Signage | None (world-readable states instead: food level, crop stage, egg glow) |
| References | Slime Rancher corrals (above); [[Creature World Interaction]] |
| Budget | Per structure ≤ current part count + a client-side habitat dressing layer |
| Note | **Placement footprints and saved data must not change**; only the visuals |
