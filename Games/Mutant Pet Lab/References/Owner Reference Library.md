---
type: reference
category: library-analysis
source: user
strength: strong-reference
status: active
applies_to: [ui, hud, navigation, shop, index, build-mode, eggs, hatching, vfx, creatures, creature-animation, upgrades]
reviewed: 2026-10-26
decision_status: not-approved (references only; see Candidates to confirm)
tags:
  - reference
  - mutant-pet-lab
  - owner-library
---
# Owner Reference Library (analysis of the living file)

> [!important] ACTIVE REFERENCE SOURCE: re-check before any player-facing design work
> **The owner's living file:** [[References for games with assets that I like and dont like.]] (vault root). The owner keeps adding images and videos there, so **re-read it each time**; this note is Claude's analysis of what was in it on the review date.
> - **Your text is never edited.** Each entry below quotes your comment word for word, then adds Claude's analysis underneath.
> - **Media moved, links unchanged:** your media now lives in `References/Assets/Owner Library/`. Obsidian resolves embeds by filename, so your note still shows everything. New pastes land in the vault root by default (Obsidian setting), and Claude files them on the next review.
> - **Authority:** owner references sit above research and below approved [[Design Decisions]] ([[Claude Workflow#Authority order]]). Nothing here is an approved decision by itself.

**Last reviewed:** 2026-10-26 · **Items:** 23 entries (R19–R23 added 2026-10-26; R17–R18 added 2026-10-21) (R15–R16 added 2026-10-20 14:34) (15 images + 9 video files; one video is a byte-identical duplicate) · **Media inspected:** all images were viewed directly. Videos were sampled at 8 evenly spaced frames each with a local AVFoundation tool, because ffmpeg isn't installed. Audio was not reviewed.

**Dislikes captured so far:** none. Every comment in the file is a like. The file title says "like and don't like", so dislikes will be filed into [[Do Not Copy]] when they appear.

---

## R1 · Pet Index (collection screen)
![[D773C1AF-8F6C-49CC-BC5C-4E8B874169DC_1_105_c.jpeg]]
> **Owner:** "I like how this index is set up and easy to read and see with the pictures and the overal style of the UI and has the sillutete of things that can eb discovered"

| | |
|---|---|
| What you like | Readable at a glance; big pictures; overall UI style; **silhouettes** of undiscovered pets |
| Why it works | One framed modal, one page per biome/family (left art panel "Forest"), a 4×2 grid of rarity-coloured tiles, a **dark silhouette on the rarity colour**, a big focal detail tile on the right with rarity + "???", a family completion bar (1/8) and **per-family rewards** (Cash + item, CLAIM / CLAIM ALL) |
| Don't copy | Their art, "L" brick texture, their pets, exact layout |
| MPL could adapt | **Already adopted in UI-C1:** rarity-framed cards, 3D silhouettes, focal detail card ([[C1 Review Stage 2026-10-16]]). **Not yet:** a page per egg family with its own art panel, and **family completion rewards with CLAIM** (candidate C-R1) |
| System | Index, Discovery, Progression |

## R2 · Shop storefronts
![[6B75E173-9F57-42D2-8E50-0ECD4A643C41_1_105_c.jpeg]]
![[0FC524B9-DD0A-4590-AEE0-4646F90012E5_1_201_a.jpeg]]
> **Owner:** "I like how these Shop UIs have nice details and and stand out and also have transactions that players are more likely to buy."

| | |
|---|---|
| What you like | Detailed, standout shop cards; layouts that make purchases appealing |
| Why it works | A hero banner with real creature renders plus **% odds on each creature**; the best result framed and glowing ("SKELETAL 1%"); chunky price buttons in escalating colours; big product art per card; section dividers ("-- PASSES --", "-- MONEY --") |
| Don't copy | Robux pricing, limited-time countdowns, strike-through "was" prices, gift buttons, "50 eggs" bulk bundles. **Monetization isn't approved** ([[Design Decisions]], [[Monetization TODO]]); your "transactions players are more likely to buy" is recorded as an **interest**, not an approval |
| MPL could adapt | Egg Shop hero with **3D creature renders and odds per creature**, the rare result highlighted in its rarity frame, section dividers. All in Cash |
| System | Egg Shop (and future monetization, if ever approved) |

## R3 · Grid build placement
![[6DC6D812-FA4F-4A56-A863-E4F92ED6A369.png]]
![[CC008A2C-45BD-4DEC-95CB-31693CE0FF68.png]]
![[04DA45A1-046E-4101-A620-F52A26E8A43B.png]]
> **Owner:** "I like this building aspect where you can snap to build on a grid layout that is customizable in 3-4 sizes of grid; with an option to rotate or cancel and a confirm button"

| | |
|---|---|
| What you like | Grid snapping, **3–4 selectable grid sizes**, rotate, cancel, confirm |
| Why it works | The visible grid on the plot shows exactly where things land; a centre move handle; rotate + green ✓ big and together; the item name + cost + red Cancel in one card; a vertical tool rail (undo/redo/grid/height/more); a Build / Decorate / Inventory tab bar |
| Don't copy | Their art, house kit, tab bar placement (MPL keeps the bottom clear) |
| MPL could adapt | MPL Build Mode already does drag → release → ROTATE/PLACE/CANCEL ([[Design Decisions]]). **New:** a grid-size toggle (e.g. 1 / 2 / 4 studs) and an undo button (candidate C-R2) |
| System | Build Mode, Plots |

## R4 · Tap-to-open egg
![[ScreenRecording_10-16-2026 13-15-57_1.mp4]]
![[frame-tap-to-open-egg-0.6s.jpg]] ![[frame-tap-to-open-result-new-1in4-5.7s.jpg]]
> **Owner:** "This is a type of animation i like for egg opening where the player can click the egg to crack it and reveal the pet"

| | |
|---|---|
| What you like | **The player clicks/taps the egg to crack it** |
| Timeline (10.1 s video) | 0.6 s: big egg fills the screen, "Tap to open!" → 1.9–3.1 s: sparkles, crack lines → ~4.4 s: burst, result "1 in 30" → 5.7 s: **"New!" stamp + pet name + "1 in 4"** on the hatched pet. ~9 s: the recording leaves the game |
| Why it works | The player *causes* the reveal (agency); a short, readable sequence; the odds line gives meaning; "New!" marks a first discovery |
| Don't copy | Exact egg, layout, sparkle art |
| MPL could adapt | Add an optional **tap-to-crack beat** to the approved hybrid hatch ([[Hatch Storyboard]]): the egg waits for a tap (or auto-cracks after ~2 s), then the tier sequence plays. This fits the approved skip rules (candidate C-R3) |
| System | Hatching |

## R5 · Egg odds popup + Open 1× / 3×
![[3D5480A8-A660-4DCD-AAA1-7A41CF2156A6_1_105_c.jpeg]]
![[DE5CFCCA-2AE3-4321-AF90-1E1DFA8E465F_1_201_a.jpeg]]
![[ScreenRecording_10-16-2026 13-25-17_1.mp4]]
![[frame-world-egg-hatch-7.3s.jpg]] ![[frame-new-pet-discovered-in-world-10.2s.jpg]]
> **Owner:** "I like how this screen shows up whenever you get to the egg which shows the percentages of pets you can get from said egg and has an option to open 1x or 3x"

| | |
|---|---|
| What you like | A popup **appears automatically when you walk up to the egg**; shows % per pet; Open 1× or 3× |
| Timeline (23.3 s video) | 1.5–4.4 s: popup above the egg with a 3×3 grid (silhouettes for undiscovered, % on each), Open ×1/×3/×8, a tutorial quest bar top-centre ("Purchase your first Egg!"), a quest panel on the right → 7.3 s: the egg swells **in the world** in front of the player → 10.2 s: **"New pet discovered! Pig, 1 in 7"** above the pet in the world → 13–16 s: Index-style grid updates, "Equipped best pets!" → 18.9 s: next hatch, "BONUS!" → 21.8 s: "New pet discovered! Cat 1 in 3" |
| Why it works | Zero menus: proximity opens the odds; the hatch happens in the world; the discovery label sits on the pet; quests guide the first minutes |
| Don't copy | Their art, ×8 bulk + auto-hatch (auto-hatch is **not approved**) |
| MPL could adapt | A **proximity odds card at each egg pedestal** in the Egg Facility (silhouettes + %), with BUY/INCUBATE. **Multi-open (×3)** is a new decision for you (candidate C-R4) |
| System | Egg Shop, Hatching, Onboarding |

## R6 · Bubble Gum Simulator egg UI (separate note)
![[8E2D1DEC-36C7-41EB-B270-E62E0F9C8366_1_102_o.jpeg]]
> **Owner (note title):** "egg opening video taken from bubble gum sim"

| | |
|---|---|
| Seen | An odds card floating beside the egg in the world (40/30/25/5 %, "Unique" in orange), with Auto / Open 3 / Open 1 hand buttons and an **"i"** info button. **The right side has a vertical rail** (Items, Shop, Trading) and top-left tiles (Index, Prizes, Boosts, Teleport) |
| Why it matters | A popular simulator puts **navigation on the side rails**, which supports the approved Direction C rails |
| Don't copy | Auto-open, boosts, 2× luck banners, the currency stack on the left |
| System | Egg Shop, Navigation |

## R7 · Hexagon upgrade board
![[33A497A0-B89B-4CE7-9D4A-7329E7F6F8F8.png]]
> **Owner:** "this is the type of upgrades screen i like where its the hexicone layout, can be used for upgrades and such"

| | |
|---|---|
| What you like | **Hexagon layout** for upgrades |
| Why it works | Each node is a big hex with an illustrated icon + short name + cost; **neighbours unlock outward**, so the path is visible; locked nodes are dark hexes with "???"; a gold hex marks progress ("3/64"); full-screen board with one Exit |
| Don't copy | The upgrade contents: Faster/Even Faster/Instant Hatch, Luckier, Auto Roll, Golden Dice, Boosts are **paid speed / luck / auto features that are not approved** ([[Do Not Copy]]) |
| MPL could adapt | Redraw the **Research tree and/or lab upgrades as a hex board** (prerequisites = adjacency, locked = dark "???" hexes). This fits the approved "Research: tree feel, prerequisites, locked paths" (candidate C-R5) |
| System | Research, Upgrades |

## R8 · Locked eggs on display
![[337F466A-E624-4A5F-AD0E-AFE3CBBCAD8B.png]]
> **Owner:** "this is a good egg setup where you can see the ones youve unlocked and are able to buy whilst the other ones remain blacked out and and chained."

| | |
|---|---|
| What you like | Unlocked eggs visible and buyable; locked ones **blacked out and chained** in the world |
| Why it works | A physical egg row on pedestals with price plates; locked = black egg + chains + padlock, a visible goal; a sign "Hatch eggs to get powerful pets!" |
| Don't copy | Their art, the rebirth/currency HUD |
| MPL could adapt | The Egg Facility shows **all six family eggs as physical models on pedestals**: locked = dark + chained + "🔒 Lv N", unlocked = coloured + price plate (candidate C-R6; supports [[Simulator UI Research]] "shop as a place in the world") |
| System | Egg Shop, Map, Progression |

## R9 · Tiered hatch: "Inferno Egg" → LEGENDARY card
![[v26044gc0000dat8uknog65nu9p7c12g.mp4]]
![[frame-inferno-egg-charge-0.9s.jpg]] ![[frame-legendary-reveal-card-4.7s.jpg]]
![[F11F82A2-5777-45C7-9B41-C710517A7758_1_102_o.jpeg]]
> **Owner:** "this is a really cool animation i like that can be used in the future to unlock cool eggs and such and then depending on the egg and its difuculty to obtain the animation can get crazier or more normal.; I also like how it displays its stats when the pet is hatched"

| | |
|---|---|
| What you like | **Animation intensity scales with egg difficulty**; stats shown on hatch |
| Timeline (14.9 s, Studio dev clip) | 0.9 s: dark scene, "Hatching Inferno Egg…", an egg outlined in glowing lava cracks over a dashed fire ring → 2.8 s: the cracks spread and the egg brightens → 4.7 s: **"LEGENDARY!" / Phoenix Wraith / "Legendary • 5.5% chance" / one-line description / green "Awesome!"**, with a glowing ring under the creature and flying embers → 8–10 s: holds on the card |
| Why it works | A dark backdrop makes the light the star; a 3-line stat block (rarity word, name, rarity + chance); one button |
| Don't copy | Exact effect art; "% chance" on the card is optional for MPL (the approved spec avoids "1 in N" in the reveal) |
| MPL could adapt | **Matches the approved tiers** (Normal / Rare / First discovery / Extreme, [[Hatch Storyboard]]). Adds: a darkened backdrop for high tiers, an element-themed egg per family (lava cracks for fire eggs), and the 3-line stat card. Whether to show the chance % needs your call (candidate C-R7) |
| System | Hatching, VFX |

## R10 · Premium egg designs (Voidheart, Celestial)
![[v15044gf0000db9t2lfog65mlua6qu80 1.mp4]]
![[v26044gc0000db76hvvog65vje5mg320.mp4]]
![[frame-voidheart-egg-14.2s.jpg]] ![[frame-celestial-egg-5.9s.jpg]]
> **Owner:** "I like this type of cool egg design and animation." · "This is another cool egg design and i like these types of designs"
> (The same Voidheart video is also embedded at the top of your file with no comment.)

| | |
|---|---|
| Seen | Both are **Claude Design artifacts** (web 3D), not Roblox games. **Voidheart Egg** ("Mythic relic"): a dark faceted egg, neon violet seams, a halo, **spread crystal wings**, orbit rings, on a glowing altar disc with runes, in a nebula sky. **Celestial Egg**: a blue voxel egg in a gold lattice cage, white angel wings, a gold halo, teal orbit rings |
| Why it works | The egg is a **trophy object**: silhouette from accessories (wings, halo, cage), a pedestal/altar, orbiting rings; rarity reads from across a room |
| Don't copy | These exact eggs |
| MPL could adapt | **Rarity-tiered egg language:** Common family eggs stay simple; the top families (and future special eggs) gain a cage/halo/wings/orbit rings + an altar. MPL eggs are currently simple models (candidate C-R8). [[Reference Gaps]] tracks a Roblox-native version |
| System | Eggs, Egg Shop, Hatching |

## R11 · Detailed, animated pet (Leviathan, pet viewer)
![[v15044gf0000dba2hcfog65hav0lqs60.mp4]]
![[frame-leviathan-pet-viewer-tabs-0.5s.jpg]]
> **Owner:** "I like how this pet design because it is detailed and animated as well"

| | |
|---|---|
| Seen (7.9 s) | A Claude Design artifact: a **sea-serpent "Leviathan"** in faceted low-poly, coiled body with gold bands, fins, an open jaw with many teeth, on a whirlpool disc with water pillars and gold spikes. The viewer has **tabs: Idle / Move / Ability / Still** and variants ("Secret + Kraken", "Effect kit") |
| Why it works | Strong silhouette from coils and fins; detail in bands and teeth; it is always moving; the base/platform sells the element |
| Don't copy | The creature |
| MPL could adapt | The **viewer pattern** (state tabs, element platform) for the Index / Creatures detail (candidate C-R9). The detail level fits a **Legendary/Mythic hero** tier, which is a likely MeshPart/Blender job ([[Reference Gaps]]) |
| System | Creatures, Creature animation, Index |

## R12 · Creature template sheet ("you should do the same")
![[v15044gf0000dbb92sfog65uht5r2dlg.mp4]]
![[frame-creature-template-sheet-11.3s.jpg]] ![[frame-template-vs-model-multiview-15.9s.jpg]] ![[frame-silhouette-check-sheet-vs-model-20.4s.jpg]]
> **Owner:** "I like how this claude uses a template to design the pets with multiple angles showing each part, and you should do the same"

| | |
|---|---|
| Seen (36.2 s) | A creator's pipeline: **TEMPLATE → CODEX → CLAUDE + BLENDER → ROBLOX**. ~11 s: a **creature model sheet** (hero view, orthographic front/side/back, components/gear breakdown, expressions/action poses, material colours, scale vs player) → ~16 s: **sheet vs model** in 4 views → ~20 s: **"Silhouette check: sheet vs model"** comparing the sheet's outline with the built model's → 25–29 s: the results in a Roblox game ("Coming soon") |
| Why it works | Every creature is designed **once on paper** before it is built, so proportions, parts, colours and expressions are fixed. The silhouette check catches drift |
| MPL could adapt | **This is an explicit owner request** ("you should do the same"). Proposal: a **Creature Template Sheet** per species (front / side / back / top / 3⁄4, part breakdown with Roles, face + 5 expressions, palette, rarity add-ons, scale vs avatar), plus a silhouette check (sheet outline vs Studio render). Recorded as candidate C-R10, flagged **likely approved: confirm** |
| System | Creature Overhaul (production pipeline) |

## R13 · Pet showcase from all angles
![[v24025gl0000db527tvog65mrsf80r0g.mp4]]
![[frame-dragon-showcase-angles-8.5s.jpg]]
> **Owner:** "This is a very cool way to display pet animations so I can look at them properly and cool pets can have a design like that"

| | |
|---|---|
| Seen (19.4 s) | "Opus 5.5 one prompt": a black-and-red **blocky dragon** in Roblox, shown idle, walking, from the top, and in flight. A second dragon roars; wings spread. The camera orbits |
| Why it works | You see the creature from every angle **in motion**, which is how you judge a design |
| MPL could adapt | A **creature review stage** (turntable + idle/walk/action) for each new template, used in every creature review from now on (process change). "Cool pets can have a design like that" points to a **dragon-class hero** for high rarity |
| System | Creature review process, Index viewer |

## R15 · MPL Creature Specimen File: blank blueprint template (added 2026-10-20)
![[Pasted image 20261020143330.png]]
> **Owner:** "Possible Blueprint layout for pets?"

| | |
|---|---|
| What it is | **An MPL-branded blueprint sheet**: "MUTANT PET LAB — Creature Specimen File" |
| Layout | Header fields **Species / Body Plan / Rarity / Habitat** · a big three-quarter **construction drawing** (ellipse guides, centre lines, ground grid) · **Front / Side / Back / Top** · **Parts** (6 slots) · **Face** (4) · **Palette** (5 swatches) · **Add-ons** (6) · **Scale** (vs a Roblox avatar) · **Assembly** · **Lineage** (parent tree) |
| Why it works | It's the R12 pipeline in MPL's own lab language; every field maps to something MPL already defines (plan, rarity, habitat, Roles, face language, rarity add-ons, recipes) |
| MPL use | **The standard template for [[Creature Template Sheets]] (C-R10).** Recommended as-is, with three small additions: a 5th face slot (the approved expression set is 5), a Mutant-feature line, and a Silhouette-check box (the Frostpup example already adds one) |
| System | Creature Overhaul (production pipeline) |

## R17 · MPL "Creature Blueprints: Core Roster" board (added 2026-10-21)
![[A925534D-4413-40FD-BB97-F812CD03FB08.png]]
> **Owner:** "i like this kind of UI"

| | |
|---|---|
| What it is | An MPL-branded **roster board**: "MUTANT PET LAB · Creature Blueprints · Species: Core Roster", with a pipeline strip (Capture → Study → Combine → Mutate → Evolve). There are 15 species cards; each has a big hero render, small Front / Side / Back views, labelled anatomy callouts, a **Variants** row and a **Mutation Paths** row, plus rarity and element tags |
| Species shown | Mossbit, Frostpup, Embercub, Slimelet, Rockling, Sparkbug (in the MPL roster) and **Shadowling, Aquarex, Skylet, Venomwisp, Magneton, Terrapaw, Phoenikit, Nebula, Chimera** (**not** in the MPL roster). The mutation paths (e.g. Fernbit, Glacipup, Toxilet) don't match MPL's recipes |
| What to take | (1) **Layout:** a dark lab-blueprint UI with a coloured header tag, rarity + element chips, a hero render with callouts, and 3 small views. It's strong inspiration for the **Index detail / specimen screen** and for the specimen-sheet template. (2) **Variants row:** shows variants as small recoloured copies. (3) **Mutation-paths row:** shows what a species can become (MPL has this data in recipes) |
| Art style note | The creatures are **soft, plush and fluffy with glow** (illustration-grade), **not faceted low-poly**. The approved direction (2026-10-21) is the faceted low-poly R16 style. **Flag for the owner:** is R17 a UI/layout reference only, or should the creature finish also move toward this softer, more detailed look? No change has been made |
| Do not copy | Species names, mutation paths and element pairings that conflict with MPL data (roster, recipes, rarities are server-authoritative); the board's exact art |
| System | Index / Creature Viewer UI, specimen sheets, (possibly) creature finish |

## R18 · "Pov: you started to make models with Claude design" video (added 2026-10-21)
![[v1c044g50000dba33ivog65rfhnpr6ug.mp4]]
![[R18-claude-design-pets-frame-01.jpg|180]] ![[R18-claude-design-pets-frame-02.jpg|180]] ![[R18-claude-design-pets-frame-03.jpg|180]] ![[R18-claude-design-pets-frame-04.jpg|180]]
> **Owner:** "possible pet designs"

| | |
|---|---|
| What it shows | A creator's model viewer (species list on the left, OBJ + MTL / GLB download buttons) showing **chunky voxel / blocky low-poly pets**: a mossy turtle, a crab, a leaf-hat plant cat, and a cosmic lizard with glowing particle trails and bloom. The opening shot shows them in a Roblox pen |
| What to take | (1) **Workflow:** a model viewer per species with export to Roblox, which matches MPL's Blender → FBX → MeshPart pipeline. (2) **Plant-cat with a leaf hat** and the **mossy turtle** are good silhouette ideas for Sprout / Shellback species. (3) **Cosmic glow variant:** sparkle trail + bloom on dark crystal parts reads as "rare" at a glance (Legendary / Mythic / Radiant ideas) |
| Art style note | Blocky voxel geometry, a third style next to R16 (faceted) and R17 (plush). Useful for anatomy ideas and variant FX, not as the finish |
| Do not copy | Specific models, names and the creator's art |
| System | Creature roster ideas, variant VFX, pipeline |

---
## R19 · Index with rarity tabs + sunburst tiles (filed 2026-10-26)
![[IMG_6968.jpg]]
> **Owner:** *(no comment of its own; it sits between "Frostpup example" and "i like this kind of UI". Treated as liked, please confirm.)*

| | |
|---|---|
| What it shows | A simulator **Index**: blue glossy header with a big book icon and a heavy outlined title, a red X, a 4-column grid of square tiles. Each tile has a **grey sunburst (radial rays) behind the creature**, the name in outlined white at the bottom, and **undiscovered = solid black silhouette + "???"**. Down the right edge is a **rarity filter tab stack** (Common, Uncommon, Rare, Epic, Legendary, Mythic, Divine, Cosmic), each tab a glossy bar in its rarity colour |
| What to take | (1) **Sunburst behind every tile:** a cheap way to make each creature a focal point (MPL could use a soft radial gradient image, tinted by rarity). (2) **Rarity tab rail** on the Index's right side as a filter, matching our side-rail language. (3) Silhouette + "???" confirms R1 (already adopted) |
| Don't copy | Their art, chick models, the Divine/Cosmic rarity names (not MPL rarities) |
| System | Index (second pass), Egg Lab result tiles |

## R20 · Glossy menu buttons → compact icon tiles ("Train a Boss" video, filed 2026-10-26)
![[v12025gd0000darulgnog65g8m15cp4g.mp4]]
![[R20-menu-buttons-full-1.9s.jpg|180]] ![[R20-menu-buttons-compact-13.0s.jpg|180]]
> **Owner (file note, 2026-10-26):** "I really like this type of UI"

| | |
|---|---|
| What it shows | A UI-making clip (a Figma-like editor): a stack of **wide glossy menu buttons**: Admin Panel, Shop (pink), Sell (green), Collection (blue), Rebirth (red), Teleport (purple), Daily Gifts, Quests (green), Inventory (grey). Each is a strong colour gradient with a **white diagonal sheen stripe**, an outlined pixel-style label and an illustrated icon breaking the left edge. At 13 s the same set collapses into **compact square icon tiles with tiny labels** in two columns (the in-game rail form) |
| What you like (confirmed) | **This type of UI**: glossy function-coloured buttons with icons, long and compact forms |
| Why it works | **One colour per function**, the icon overlapping the frame edge (feels 3D), the same sheen on every button = one family; the long form for menus and the short form for rails |
| What to take | MPL already has function colours + square rail tiles. Adopt (1) **the icon breaking the tile edge** (scale 1.15, offset up-left), (2) the **diagonal sheen stripe** on rail tiles and primary buttons, (3) a **long-button form** for list menus (Goals, Upgrades, My Lab actions) using the same colour per function |
| Don't copy | Rebirth / Daily Gifts / Admin Panel features (rebirth isn't approved), the pixel font, their icons |
| System | HUD rails, buttons, Goals/Upgrades lists |

## R21 · Card-pack reveal with escalating FX ("Took 3 days to make this", filed 2026-10-26)
![[v12044gd0000dbc5o87og65kgqipv8jg.mp4]]
![[R21-card-reveal-charge-1.8s.jpg|160]] ![[R21-card-reveal-spin-12.7s.jpg|160]] ![[R21-card-reveal-final-16.4s.jpg|160]]
> **Owner (file note, 2026-10-26):** "i love this animation"
> **Owner (2026-10-26, in chat):** "for r21 i like the cool animation to show the card and how the design is, and how it displays the stats on it with a cool boarder"

| | |
|---|---|
| Timeline (21.8 s, Studio clip) | 0–9 s: a **full-screen red cinematic build-up**: dark backdrop, speed lines, a dramatic zoom on the character, red energy streaks → 12.7 s: a **card spins in a violet galaxy swirl** with sparkle particles → 16.4 s: the **final card**: a big rarity word over it ("GALACTIC"), a **gem-studded frame**, a name banner ("NIGHTMARE"), the odds ("1 in 300"), a stat line, all over a coloured world backdrop |
| Why it works | **Three acts** (tension → spin/reveal → hold); the rarity word is the loudest element; the colour theme changes per rarity; the backdrop is fully taken over, so nothing competes |
| What you like (confirmed) | (1) The **reveal animation** that brings the card in; (2) the **card design** itself; (3) **stats printed on the card**; (4) the **decorative border** |
| What to take for MPL | For **First discovery / Legendary / Mythic / Secret mutation** only: (1) a darkened full-screen takeover tinted in the rarity colour, (2) a short spin/flip of the reveal card or a rotating creature turntable before it settles, (3) a **framed reveal card** whose frame gets richer by rarity (plain → studded → glowing), (4) the rarity word big above the card. Commons stay short (repeat hatches must not be slowed) |
| Don't copy | Anime character art, gacha card mechanics, "1 in N" phrasing on the card (the approved spec avoids it), gambling-feel pacing |
| System | Hatch / discovery reveal, mutation reveal (secret) |

## R22 · "All models made with Claude": detailed pets + viewer tabs (filed 2026-10-26)
![[v12044gd0000dbdf33vog65voqpa09n0.mp4]]
![[R22-claude-pets-mythic-wolf-3.9s.jpg|160]] ![[R22-claude-pets-octopus-6.4s.jpg|160]] ![[R22-claude-pets-clockwork-9.0s.jpg|160]]
> **Owner (file note, 2026-10-26):** "these models are really cool"

| | |
|---|---|
| What it shows | A creator's web model viewer with tabs **Idle / Move / Ability / Still**, round selector (Round 1–3), Front/Side views, GLB/OBJ export, a rarity label ("MYTHIC"), and models next to a Roblox avatar for scale: a **dark armoured wolf with red glow + floating red crystal shards + a red moon halo** (Mythic), a **teal octopus with glowing studded tentacles and a gold band**, a **clockwork/brass creature in a gold ring halo with orbiting gears**. The first frame shows the batch prompt: per-species tweak lists by rarity tier |
| What you like (confirmed) | The **models**: detailed creatures with accessories, glow and animation (owner: "really cool") |
| What to take | (1) **High-rarity escalation through accessories:** halo rings, orbiting shards/gears, a rim glow, a coloured backdrop orb. This is exactly the tool for MPL's Legendary/Mythic specs ([[Remaining 12 Species Production Specs]]). (2) **An "Ability" tab** in the viewer: MPL's viewer already has Idle / Move / Still, and an Ability preview (mutant-feature animation) would fit. (3) **Scale vs a Roblox avatar** in the viewer, like our template sheets. (4) The **batch prompt per tier** matches our roster pipeline |
| Art style note | Blockier and more detailed than R16, consistent with R18. It confirms **detail and accessories rise with rarity**. The faceted R16 finish stays approved |
| Don't copy | Those species/models, the wolf/octopus/clockwork designs |
| System | Legendary/Mythic creature design, Creatures viewer (Ability tab), variant FX |

## R23 · Minimal dark panel: "U rid ur Claude of slop UI" (filed 2026-10-26)
![[v15044gf0000dbf58evog65pd1gc9e20.mp4]]
![[R23-minimal-dark-panel-48.2s.jpg|240]]
> **Owner (file note, 2026-10-26):** "this UI is something that i like"
> **Owner (2026-10-26, in chat):** "for r23 i like the clean ui"

| | |
|---|---|
| What it shows | A Roblox admin "COMMANDS" panel: near-black translucent panel with **rough, brush-torn edges**, a red ink-brush emblem, a serif title + small subtitle, rows of commands with small pill arguments, a single red accent arrow, over a dim scene. Opening animation: an **ink splash** effect |
| Why it works | It avoids the "AI default UI" look (generic rounded cards, gradients everywhere, emoji icons, even padding): **one accent colour, a texture edge, real typographic hierarchy, restraint** |
| What you like (confirmed) | The **clean UI**: restraint, uncluttered layout, one accent, clear hierarchy |
| What to take for MPL | The **anti-slop / clean-UI rules**, not the dark gothic style (MPL stays bright, friendly bio-lab, not dark/serif): (1) one accent per screen; (2) no emoji icons in final UI (MPL has its vector icon set; remaining emoji like 🐾 🍽 🏡 in rows should go); (3) a distinct edge/texture treatment instead of plain rounded rectangles (MPL: a stud-free lab-glass edge or a subtle panel bevel); (4) a clear type scale (title / label / value), not everything bold; (5) an entrance animation with character (MPL: a quick "slime splash" or lab-glass wipe) |
| Don't copy | Dark gothic look, serif fonts, admin-command content, the brush emblem |
| System | All UI (second pass quality bar) |

**Duplicate:** `v1c044g50000dba33ivog65rfhnpr6ug 2.mp4` is byte-identical to R18's video (same MD5); no new content.

---
## R16 · Frostpup filled example (added 2026-10-20)
![[Pasted image 20261020143437.png]]
> **Owner:** "Frostpup example"

| | |
|---|---|
| What it shows | FROSTPUP · "ARCTIC CANID" · RARE. A **chunky chibi quadruped** in a **faceted low-poly crystal style** (white faceted fur, pale-blue facets on ears/paws/tail), a **jagged ice-crystal mane/collar** (the mutant feature), small ice spikes along the spine, big glossy blue eyes, a black nose, a smile |
| Parts row | Head, Ears, Eyes, Ice Mane, Foreleg, Hind Leg, Tail, Ice Spikes |
| Face row | Neutral, Happy (closed-eye), Alert, Determined, Sleepy |
| Other panels | Palette (white, pale blue, cyan, periwinkle, slate) · Scale: pup **0.9× height**, avatar 1.8× · Lineage: snowflake + wolf → Frostpup (concept) · Rarity add-ons: crystal cluster, star, diamond sparkles · **Silhouette panel** (outline check) |
| What it teaches | (1) The intended **finish is faceted / low-poly**, not smooth balloons. That's the main gap in the C1 Frostpup (smooth ellipsoids). (2) The ice mane is **one bold mutant feature** around the neck rather than small back crystals. (3) Ears are tall, faceted and pointed: canine, not rabbit. (4) It reads at 0.9× avatar height |
| Notes | Matches the approved LEFT chunky-quadruped choice. **Lineage** here is concept-level: in MPL data Frostpup is an **egg species** (Field / Cryogenic eggs), not a mutation, so its real sheet shows the egg family instead of parents. "Determined" brows are fine as an expression, but low wellbeing must stay sad, not angry (approved) |
| System | Creature Overhaul, Creature Face Language, template sheets |

---
## R14 · Trail shop (no comment yet)
![[4134A454-21B9-45D1-AE01-85062C37B717_1_201_a.jpeg]]
> **Owner:** *(image present in the vault with no comment)*

Seen: rarity-coloured product cards (Common grey / Uncommon green / Rare blue), the item render in a dynamic pose, a stat chip ("x2 Speed"), and two price buttons (Cash + Robux). **Needs your clarification:** what you liked here (card colours? stat chip?). Listed in [[Master Visual and Gameplay References#Needs owner clarification]].

---
## Related
[[Master Visual and Gameplay References]] · [[Do Not Copy]] · [[Reference Gaps]] · [[Similar Games Overview]] · [[Design Decisions#Candidates to confirm (not approved decisions)]]
