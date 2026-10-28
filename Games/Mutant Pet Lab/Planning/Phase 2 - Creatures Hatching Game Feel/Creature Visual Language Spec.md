---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: creatures
status: approved-direction
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - planning
  - phase-2
  - creatures
---
# Creature Visual Language Spec

> [!success] APPROVED DIRECTION (owner, 2026-10-16) — not implemented yet
> Binding decisions: the *Phase 2:* entries in [[Design Decisions]]. Where this spec and a decision differ, the decision wins. Implementation follows [[PHASE2_IMPLEMENTATION_PLAN]] after the owner reviews it.
> No models are built in this pass.
>
> **Built on:**
> - [[Creature Presentation Research]], [[Creature Silhouette and Personality]]
> - [[Design Decisions#Overall direction: cozy bio-lab ranch with a mutant-lab identity]]
> - The 36 species in `SpeciesConfig` ([[Species]])


## What exists today
- **Every species uses the same model:** a 2.7 × 2.3 × 2.7 coloured ball + 2 dark eyes + a nameplate (`PropertyVisuals.Creature`). That's 3 anchored parts, built by the server.
- **Species differ only by colour.** The material in `SpeciesConfig` is used only for the Index/showcase.
- **Variants show only on the Featured Specimen pedestal** (Neon/Glass/ForceField material). Creatures in pens show no variant.
- **The ranch benchmark assumes 3 anchored parts per creature** (`PropertyPerformance_Test`: 48 creatures / 144 parts).

> [!important] Biggest gap found in the research
> Silhouette identity: [[Creature Presentation Research#Recommended for MPL (candidates only)]]. Successful creature games make species readable by **shape** first, then colour ([[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)|S39]]; shape-language guidance from [rocketbrush](https://rocketbrush.com/blog/shape-language-in-game-character-design-how-to-make-characters-readable-and-consistent)).

## Shape language (house rules)
1. **Silhouette first:** every species must be recognisable as a solid black shape at 30 studs.
2. **Cozy base, mutant accent:**
   - Bodies use **rounded primary forms** (friendly).
   - Each species gets **one mutant accent** in a secondary shape: crystal spikes (triangles), shell plates (squares), glowing organs, extra eyes, antennae, fins.
   - At most 1–2 accents per species, so they stay readable.
3. **Big readable eyes:** 2 eyes (3 for Unstable/Experimental lineages), placed high on the front. Eye white + pupil so the creature can *look* at things. This is the "pet, not item" anchor.
4. **Glow = biology:**
   - Neon is reserved for a creature's **core/organ** (one glowing part per species).
   - Variants change the glow behaviour, not the base colour.
5. **Chunky and low-poly:**
   - Parts-based (Ball, Cylinder, Wedge, Block), matching the map's look.
   - **Phase 2 default: no MeshParts** (open owner question).

## Proportions
- **Head/body ratio:** juvenile-cute. Head ≈ 55–70% of body volume (Gel, Wisp and Sprout read as "all head").
- **Footprint:** Common/Uncommon ~3 × 3 studs (today's ball is 2.7), so pens and feeding spacing stay valid.
- **Size by rarity** (gives rarity a silhouette signal):

| Rarity | Common | Uncommon | Rare | Epic | Legendary | Mythic |
|---|---|---|---|---|---|---|
| Scale | 1.0 | 1.0 | 1.1 | 1.2 | 1.3 | 1.35 |

  The max height of 4.5 studs keeps creatures inside pen walls. Sporephant ("massive") is the one exception, allowed 1.5.

- **Parts budget (client display model):** Common–Rare ≤ 8 parts, Epic ≤ 10, Legendary/Mythic ≤ 12. **LOD:** beyond ~80 studs, show only the body + eyes (3 parts).

## Body plans (family resemblance)
Seven body plans plus one hybrid. Every species belongs to exactly one plan, so the whole roster reads as a family while the silhouettes differ.

| Plan | Silhouette | Signature parts | Species (36) |
|---|---|---|---|
| **Gel** | dome / teardrop, no legs, squash and stretch | gel body, inner glow organ, eye stalks optional | Slimelet, Gloamgel, Tidegill, Aquaflux |
| **Critter** | 4 short legs, big head, tail | head, body, 4 nubs, tail, ears/horns/mane | Frostpup, Embercub, Cinderhorn, Voltusk, Obsidian Lynx, Sporephant |
| **Hopper** | squat body, big back legs, wide mouth | body, 2 large hind legs, 2 small fore nubs | Pebbletoad, Fluxaroo, Glacierbit |
| **Flyer** | small body, 2–4 wings, antennae | body, wings (thin wedges), antennae | Sparkbug, Miremoth, Circuitfin (fin-wings), Tempestrix |
| **Sprout** | bulb body on a short stem/feet, leaf/petal crown | bulb, 2 feet, leaf/petal ring, bloom | Mossbit, Bloomtail, Thornling, Radisprout, Auroroot, Brimstone Bloom, Toxibloom |
| **Wisp** | floating core + orbiting pieces, no ground contact | core orb, 2–4 orbiting satellites, shadow disc | Magmawisp, Geodewisp, Cryolume, Fungloom, Biolume, Nucleonox, Nullmorph, Quasipod |
| **Shellback** | low crawler under a shell/plate dome | shell, small head, 4–6 stubby legs, crystals | Rockling, Prismaclaw, Ferrite Drake |
| **Hybrid** | parts from several plans, deliberately "wrong" | body from one plan, limbs/wings/orbit from others | Chimerax |

**Habitat accents** (family colour/material cues, shared across plans):

| Habitat | Accent |
|---|---|
| Botanical | leaves, moss |
| Thermal | ember cracks, warm glow |
| Cryogenic | ice crystals, frosted tips |
| Conductive | coils, arcing antenna |
| Geological | stone plates, crystals |
| Humid | gills, spores, wet sheen |
| Unstable | asymmetry, third eye |
| Experimental | lab tags, glass parts |

## Rarity readability
- **Scale** (table above).
- **Base ring:** a thin ring under the creature in the rarity colour. Uses the showcase pedestal colours already applied: Common grey-green, Uncommon green, Rare blue, Epic purple, Legendary gold, Mythic pink.
- **Nameplate:** colours already follow rarity; keep the "compact, transparent" rule.
- **Legendary/Mythic:** one extra accent part allowed (crown, halo, orbit) and a slow idle glow pulse.
- **Never** rely on colour alone (colour-blind safety): scale + ring + accent count all agree.

## Trait readability (behaviour first, icon second)
Traits are **behavioural** and stay subtle, so creatures of the same species still match:

| Trait | Idle flavour | Icon |
|---|---|---|
| Calm | slower breathing, long blinks | 🌙 |
| Curious | leans toward nearby players, investigates often | ❓ |
| Vigorous | bouncier steps, quicker idle | ⚡ |
| Adaptive | tint drifts 10% toward the pen's habitat colour | 🔄 |
| Volatile | occasional tiny spark/fizz (≤ 1 per 8 s) | 💥 |
| Radiant | faint aura on the glow organ | ✨ |
| Insulated | a frost or heat puff when it sleeps | 🧊 |
| Forager | sniffs the ground between moves | 🍃 |

Icons appear on the hatch card, the Creature detail and the nameplate (one small icon).

## Variant readability (must read from ~30 studs)

| Variant | Visual rule | Cost |
|---|---|---|
| **Luminous** | The glow organ becomes Neon and brighter; a slow 3 s pulse. No PointLight in pens (light budget) | 0 extra parts |
| **Chromatic** | The accent part's hue drifts slowly through a 3-colour loop, tweened client-side | 0 extra parts |
| **Prismatic** | Iridescent accent (Glass) + a small sparkle ParticleEmitter (≤ 6 particles/s), only within 60 studs | +1 emitter |

**The variant must show everywhere the creature appears:** pen, holding spot, showcase, hatch, Index. Today it shows only on the pedestal.

## Mutation inheritance table
Mutation results are fixed species (`RecipeConfig`), so inheritance is **authored into each result's design**:
- The result takes its **body plan + one feature from parent A** (form) and its **glow colour or surface pattern from parent B** (finish).
- The result card says it in words.

| # | Recipe | Result (plan) | From A | From B |
|---|---|---|---|---|
| 1 | Slimelet + Rockling | Magmawisp (Wisp) | gel core | orbiting stone shards |
| 2 | Sparkbug + Mossbit | Bloomtail (Sprout) | antennae → stamen | leafy crown |
| 3 | Frostpup + Embercub | Prismaclaw (Shellback) | pup head shape | ember-crack glow in crystal claws |
| 4 | Slimelet + Mossbit | Gloamgel (Gel) | gel body | moss tufts (dusk-tinted) |
| 5 | Rockling + Mossbit | Pebbletoad (Hopper) | stone plates on the back | moss patches |
| 6 | Mossbit + Embercub | Thornling (Sprout) | leaf body | ember-tipped thorns |
| 7 | Sparkbug + Frostpup | Circuitfin (Flyer) | static wings → fins | frosted fin edges |
| 8 | Rockling + Embercub | Cinderhorn (Critter) | mineral crown | warm mane glow |
| 9 | Slimelet + Frostpup | Glacierbit (Hopper) | jiggle body | ice-crystal back |
| 10 | Mossbit + Frostpup | Miremoth (Flyer) | moss wing texture | cool blue wing tips |
| 11 | Slimelet + Sparkbug | Radisprout (Sprout) | gel bulb | amber glow bulb |
| 12 | Rockling + Sparkbug | Tidegill (Gel) | stone-grey gill plates | charged shimmer |
| 13 | Sparkbug + Embercub | Fungloom (Wisp) | antenna fronds | ember-glow spores |
| 14 | Sparkbug + Circuitfin | Voltusk (Critter) | crackling tusks | fin-shaped ears |
| 15 | Embercub + Bloomtail | Brimstone Bloom (Sprout) | ember core | petal crown |
| 16 | Frostpup + Gloamgel | Cryolume (Wisp) | icy membrane | dusk glow core |
| 17 | Rockling + Prismaclaw | Geodewisp (Wisp) | stone core | crystal lattice orbit |
| 18 | Miremoth + Bloomtail | Toxibloom (Sprout) | moth-wing petals | bright warning bloom |
| 19 | Circuitfin + Tidegill | Aquaflux (Gel) | fins | glassy fluid body |
| 20 | Slimelet + Magmawisp | Fluxaroo (Hopper) | elastic gel pouch | molten glow |
| 21 | Fungloom + Pebbletoad | Sporephant (Critter, giant) | spore cloud on the back | stone-heavy legs |
| 22 | Geodewisp + Voltusk | Ferrite Drake (Shellback) | crystal orbit → back spines | tusks → horns, static glow |
| 23 | Toxibloom + Radisprout | Nucleonox (Wisp) | warning petals as shielding | radiant bulb core |
| 24 | Radisprout + Cryolume | Auroroot (Sprout) | nutrient bulb | aurora icy glow |
| 25 | Cinderhorn + Prismaclaw | Obsidian Lynx (Critter) | horned crown → ears | crystal claws |
| 26 | Voltusk + Cryolume | Tempestrix (Flyer) | static horns → antennae | icy wings |
| 27 | Aquaflux + Fungloom (secret) | Biolume (Wisp) | fluid glow body | spore satellites |
| 28 | Fluxaroo + Nucleonox (secret) | Chimerax (Hybrid) | hopper legs | shielded core + extra eye |
| 29 | Tempestrix + Auroroot (secret) | Nullmorph (Wisp) | storm wings as refraction shards | aurora roots as trailing light |
| 30 | Biolume + Nullmorph (secret) | Quasipod (Wisp) | luminous body | refraction phase-shift |

> [!note] Design direction, not final art
> Species ids, names, colours and saved data stay unchanged ([[Persistence]]).

## Technical approach (proposal)
- **Server proxy stays as is:** the 3-part ball, anchored, moved by the shared scheduler. Tests and the benchmark are unaffected.
- **Clients render a display model** from editable templates in `ReplicatedStorage/MutantPetLab/Creatures/<Plan>/<Species>`:
  - Built in Studio, consistent with the editable-UI decision.
  - The model follows the proxy and the server proxy goes invisible on clients.
  - Animation is client-side ([[Creature Animation Spec]]), with distance LOD and culling. This is the common DevForum recommendation for many pets ([pet-system threads](https://devforum.roblox.com/t/how-does-pet-simulator-do-it/2779392); [optimisation write-up](https://devforum.roblox.com/t/3127146)).
- **Fallback:** if a template is missing, the client shows the current ball, so nothing breaks while species are made one by one.

## Production order (proposal)
1. One template per body plan, using the starter species as prototypes:
   - Slimelet = Gel
   - Rockling = Shellback
   - Sparkbug = Flyer
   - Mossbit = Sprout
   - Frostpup = Critter
   - Magmawisp = Wisp
   - Pebbletoad = Hopper
2. Owner approves the look.
3. The rest of each plan follows.
4. Mythics last.
