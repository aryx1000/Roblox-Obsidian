---
type: planning
game: "[[Mutant Pet Lab]]"
area: creatures
status: review
updated: 2026-10-23
tags:
  - mutant-pet-lab
  - creatures
  - planning
---
# Remaining 12 species: production concept specs (2026-10-23)

**Status:** 24/36 species are Blender production models. These 12 are the review-flagged set from the [[Roster Conversion Plan]].

**Rule (owner, 2026-10-23):**
- If a species cleanly extends an approved body family, continue to production.
- Legendary, Mythic, secret, Chimerax/hybrid and fundamentally new anatomy get a spec first and are flagged.

**Rarity escalation toolkit (owner refs R10/R18/R22, 2026-10-26):** Legendary and Mythic gain detail through **accessories**, not a new finish: a halo ring, orbiting shards/gears/motes, a rim glow on the signature organ, and a stronger Luminous. Epics get at most one of these.

All species keep the shared language:
- Roblox-part face (big glossy eyes + glints);
- flat-shaded low-poly;
- one bold mutant feature;
- matte body, with a Luminous glow only on the signature organ.

## Verdict summary
| Species | Rarity | Family | Verdict |
|---|---|---|---|
| Prismaclaw | Epic | Shellback + claw accents | ✅ **extends Shellback, continue** |
| Sporephant | Epic | Critter (heavy) + trunk | ✅ **extends Critter, continue** |
| Fluxaroo | Epic | Hopper + pouch + balance tail | ✅ **extends Hopper, continue** (keeps the Hopper crouch; no upright kangaroo stance) |
| Auroroot | Legendary | Sprout (tall) | 🟡 spec, owner review (Legendary) |
| ObsidianLynx | Legendary | Critter | 🟡 spec, owner review (Legendary) |
| Tempestrix | Legendary | Flyer (large) | 🟡 spec, owner review (Legendary) |
| Nucleonox | Legendary | Wisp | 🟡 spec, owner review (Legendary) |
| FerriteDrake | Legendary | Shellback today → **needs a Drake rig** | 🔴 **new body family: flag** |
| Biolume | Mythic (secret) | Wisp | 🟡 spec, owner review (secret) |
| Nullmorph | Mythic (secret) | Wisp | 🟡 spec, owner review (refraction-only look is a style exception) |
| Quasipod | Mythic (secret) | Wisp + form swap | 🔴 **new mechanic (form change): flag** |
| Chimerax | Mythic (secret) | Hybrid | 🔴 **new hybrid rig: flag** |

---
## Prismaclaw (Epic): Shellback
- **Anatomy:** a Rockling-style soft critter under a **refractive crystal shell**, plus **two oversized crystal claws** held forward (a hunter stance, low front).
- **Silhouette:** wide, low triangle; claws give a crab-like front read; 3 tall prism spikes on the shell.
- **Mutant feature:** refractive crystal shell + claws.
- **Materials:** body matte lilac (173,112,255 → softened 150,120,210); shell + claws Glass T 0.15 violet-blue; dark rim.
- **Glow:** inner shell core (Neon). **Luminous** tint prism blue (90,170,255), mix 0.8; claws opt out.
- **Animation:** Shellback walk; claws = `Accent` with a small idle "snip" (Crown-style sway on the claw parts). No new rig.
- **Variants:** Chromatic tints the shell; Prismatic suits glass well.
- **Targets:** ≤ 750 tris / ≤ 13 meshes. **Family:** extends Shellback.

## Sporephant (Epic): Critter (heavy)
- **Anatomy:** a heavy four-legged fungal calf with a **short drooping trunk** and a **mushroom-cap back** (2–3 caps), with small floppy ears.
- **Silhouette:** big rounded body, short legs, trunk curve at the front, caps on top: it reads as "elephant-mushroom" at 30 studs.
- **Mutant feature:** trunk sensory organ (glowing tip).
- **Materials:** tan/brown matte body (182,147,105), cream underside, cap tops spore-teal with cream dots.
- **Glow:** trunk tip + cap gills. **Luminous** tint spore teal (60,230,180), mix 0.8.
- **Animation:** Critter heavy walk (Voltusk/Cinderhorn); trunk = `Tail`-style sway parented at the face (role `Crown` with a sway so the trunk swings slowly). Larger scale (Epic), slow bob.
- **Targets:** ≤ 750 / ≤ 14. **Family:** extends Critter (heavy).

## Fluxaroo (Epic): Hopper
- **Anatomy:** a Pebbletoad/Glacierbit-style hopper with **long back feet**, a **thick balance tail** and a **glowing biomass pouch** on the belly that shifts colour.
- **Silhouette:** crouched hopper (not upright), tall ears, tail sweeping back.
- **Mutant feature:** rearranging pouch (Neon blob with 2–3 inner bubbles).
- **Materials:** pink-magenta matte body (250,151,220 softened), cream belly ring, gold pouch.
- **Glow:** pouch. **Luminous** tint magma gold (255,170,40), mix 0.8.
- **Animation:** Hopper hop + tail counter-swing (`Tail`). The pouch pulses (Glow).
- **Targets:** ≤ 750 / ≤ 13. **Family:** extends Hopper.

## Auroroot (Legendary): Sprout (tall), needs review
- **Anatomy:** a **tall** botanical sentinel (about 1.6× Mossbit height); slim trunk body, leaf crown, **long hanging aurora roots** (4–5 ribbon roots).
- **Mutant feature:** aurora-coloured roots (green → teal → violet gradient, as separate meshes per colour band).
- **Glow:** the roots. Luminous aurora (90,255,200).
- **Animation:** Sprout sway, roots as `Tail` parts with phase offsets.
- **Variants:** Prismatic suits the roots.
- **Targets:** ≤ 850 / ≤ 14. **Family:** extends Sprout, but its height is a scale exception.

## ObsidianLynx (Legendary): Critter, needs review
- **Anatomy:** a sleek feline (Embercub's elder) with **faceted obsidian plates** on its back and legs, ear tufts and a long tail with a lava-crack tip.
- **Mutant feature:** obsidian plates with thin magma seams.
- **Materials:** Basalt-dark (67,63,82), plates near-black glossy; seams Neon red.
- **Glow:** seams + tail tip; Luminous magma red (255,60,40).
- **Animation:** Critter walk, lower/stalking idle.
- **Targets:** ≤ 880 / ≤ 15. **Family:** extends Critter.

## Tempestrix (Legendary): Flyer (large), needs review
- **Anatomy:** a round bird-like flyer with **two large swept wings**, a crest of ice feathers and a **floating storm ring** (Orbit) around it.
- **Mutant feature:** quiet lightning aura: 3 small orbiting bolt meshes.
- **Materials:** pale blue body, white chest, ice-glass wing tips.
- **Glow:** bolts + crest tips; Luminous storm blue (80,160,255).
- **Animation:** Flyer, with a slower, larger flap; Orbit bolts.
- **Targets:** ≤ 900 / ≤ 16. **Family:** extends Flyer (scale up).

## Nucleonox (Legendary): Wisp, needs review
- **Anatomy:** a floating lab organism: a soft green body inside a **3-plate hex shield** that rotates slowly, with a bright core visible between the plates.
- **Mutant feature:** shielded core.
- **Glow:** core; Luminous toxic lime (150,255,40).
- **Animation:** Wisp hover; the shield plates are `Orbit` at a slow rate.
- **Targets:** ≤ 850 / ≤ 14. **Family:** extends Wisp.

## FerriteDrake (Legendary): FLAG, new body family
- **Why flagged:** a drake (long neck, four legs, small wings, tail) doesn't fit Shellback's low dome or any current plan. It needs a **Drake rig** (neck segment + wing hinge + long tail chain).
- **Concept:** a metallic blue-grey mineral drake with magnetite scale plates and a **magnetic core** in the chest; iron filings orbit it.
- **Glow:** core + orbiting filings, magnet red (255,70,70).
- **Targets:** ≤ 900 / ≤ 16 + a new `Drake` plan in `CreatureVisualConfig`.
- **Owner decision:** approve a new Drake family, or redesign it as a Shellback "armadillo-drake".

## Biolume (Mythic, secret): Wisp, needs review
- **Concept:** a jellyfish-like pulse organism: dome bell + 6 trailing tendrils; the bell light **pulses faster when players are researching or mutating nearby** (client-only effect, read from public state).
- **Glow:** bell rim + tendril tips; bio cyan (40,255,220).
- **Targets:** ≤ 900 / ≤ 15. Extends Wisp; the activity-reactive pulse is a small client effect.

## Nullmorph (Mythic, secret): Wisp, needs review
- **Concept:** visible **only through refraction**: an all-Glass body (T 0.6) with an outline rim of soft Neon and floating prism shards; the eyes stay solid so it keeps the face language.
- **Style exception:** the near-invisible body breaks the "matte body" rule, and Glass hides other transparent parts. Test readability at 30 studs before approving.
- **Targets:** ≤ 850 / ≤ 14.

## Quasipod (Mythic, secret): FLAG, new mechanic
- **Concept:** a phase-mutant that **changes form under lab sensors**: two poses/forms (a pod form and an unfurled form) swapped client-side every N seconds or near lab machines.
- **Why flagged:** it needs two models + a swap mechanic (new). The form-change rules need design.
- **Targets:** ≤ 900 / ≤ 16 per form.

## Chimerax (Mythic, secret): FLAG, hybrid rig
- **Concept:** a many-lineage mutant: Critter body + Flyer wing on one side, Sprout leaves on the other, a Thermal tail. Deliberately asymmetric.
- **Why flagged:** asymmetric multi-family parts need a `Hybrid` plan (the animator must drive mixed roles), and its look is the most sensitive in the roster.
- **Targets:** ≤ 900 / ≤ 16.

---
**Next:** Prismaclaw, Sporephant and Fluxaroo go to Blender now (normal pipeline: model → FBX → import queue → fit). The other 9 wait for owner review of these specs.
