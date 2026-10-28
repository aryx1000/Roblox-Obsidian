---
type: planning
game: "[[Mutant Pet Lab]]"
area: ui
status: ready-to-build
updated: 2026-10-23
tags:
  - mutant-pet-lab
  - ui
  - hatching
  - mutation
---
# UI pass 2 + final hatch/mutation presentation: build plan

Written from the actual owner references (R1 Index, R2 shop, R5/R6 egg odds, R7 hex board, R9 reveal card) while Studio was unavailable. Everything stays original MPL art: shapes, the vector icon system and 3D ViewportFrame renders of our own creatures. **No reference artwork is copied.**

## Shared language (from R1/R2/R9, adapted)
| Element | Rule |
|---|---|
| **Frame** | Keep the Direction-C dark ink frame. Add a **glossy header band**: function colour + a white diagonal sheen stripe (UIGradient, 2 stops) + a heavy outlined title (FredokaOne, white, 3 px ink stroke) |
| **Focal point** | Every screen gets ONE hero: a large 3D creature/egg render (ViewportFrame) or a hero banner. Everything else is secondary |
| **Tiles** | Rarity-coloured tiles: rarity fill + a darker 2 px inner stroke + an ink outer stroke; creature render centred; a small corner chip for %, count or level; undiscovered = dark silhouette on the rarity colour + "???" |
| **Buttons** | One primary action per view: big, green (or function colour), lip shadow, press scale 0.96. Secondary actions are ghost buttons |
| **Selected state** | Gold 4 px stroke + a 1.06 scale tween + a small pip, the same on every screen (the Creatures viewer tabs already do this) |
| **Text** | Shorter labels; numbers as chips; ≥ 12 px at 667×375 |
| **Progress** | Thick rounded bar with an outlined count ("3/8"), in the function colour |

## Additions from the 2026-10-26 references (R19–R23)
- **Clean-UI quality bar (R23, owner: "i like the clean ui"):**
  - one accent colour per screen;
  - **remove remaining emoji icons** (🐾 🍽 🏡 📦 ✅ in Creatures rows, toasts) in favour of the vector icon set;
  - a real type scale (title / label / value), not everything bold;
  - a panel edge treatment beyond a plain rounded rectangle (subtle lab-glass bevel);
  - a characterful entrance (quick slime-splash / glass-wipe, ≤ 0.25 s).
- **Buttons and rails (R20):** function colour + diagonal white sheen stripe on every primary button and rail tile; the **icon breaks the tile edge** (1.15× scale, offset up-left); a long-button form for list menus with the same colour per function.
- **Tiles (R19):** a soft **radial sunburst behind each creature tile**, tinted by rarity (one shared image, ImageColor3 per rarity); undiscovered stay silhouette + "???".
- **Index (R19):** a **rarity filter tab rail** on the panel's right edge (MPL rarities only: Common → Mythic).
- **Reveal card (R21, owner-confirmed 2026-10-26: "the cool animation to show the card… how it displays the stats on it with a cool boarder"):** every reveal shows a **designed card**, not plain text:
  - an animated entrance (fly-in + flip/turntable);
  - the creature render inside;
  - a **stats block on the card**: rarity, species, trait chip, variant chip, wellbeing-neutral stats such as sample class / habitat / family;
  - an **ornamental border** whose tier rises with rarity: Common plain bevel → Rare double line → Epic corner gems → Legendary studded gold + glow → Mythic animated shimmer. Original MPL art: lab-glass + DNA-node motifs, no copied frames.
- **Reveal escalation (R21 + R9):** for First discovery / Legendary / Mythic / Secret mutation only:
  - a full-screen takeover tinted in the rarity colour;
  - a short turntable spin of the creature;
  - a framed card whose frame gets richer by rarity (plain → bevelled → studded + glow);
  - the rarity word largest.

  Commons stay short. No "1 in N" on the card.
- **Creatures viewer (R22):** add an **ABILITY** tab next to Idle/Move/Still that plays the species' mutant-feature motion (orbit spin, glow pulse, tail flick), plus an avatar-height scale marker.
- **Legendary/Mythic design (R22):** rarity rises through accessories (halo ring, orbiting shards/gears, rim glow), added to [[Remaining 12 Species Production Specs]] as the escalation toolkit.

## Per screen (priority order)
1. **HUD (status pod):** level ring with an XP arc; the currency chips get a glossy top highlight. Keep the "Specimens · Index" line but turn it into 2 icon chips (paw, book). Toasts slide from the top with rarity colour.
2. **Side rails:** square icon tiles already exist. Add a selected state (gold stroke + pip) for the open screen, a notification badge (red dot + count) on Goals/Index when something is claimable, and a short label under each icon on ≥ tablet only.
3. **Goals (Lab Task Board):** a hero "CURRENT TASK" card (icon tile + one line + progress bar + reward chips + CLAIM). The list below becomes compact rows with a status chip (✓ / bar / lock).
4. **Egg Lab:** an R2-style **hero banner per family**: big egg render left; the creature results as 3D tiles with % chips, the rarest framed and glowing; the price button (Cash/Research) bottom-right; locked families show the chained dark egg + "Lv N" chip. Section divider "— FAMILIES —".
5. **Mutation Lab:** two big **parent slots** (3D renders in rarity tiles) with a ➕ between them, an arrow to the **result chamber** tile ("???" silhouette until known), recipe chips below, and one MUTATE button with its cost chip. Selected parents get the gold stroke.
6. **Creatures viewer:** already strong (live rig). Swap the text rows for **chip rows** (trait chip with icon, wellbeing pips, favourite-food chip, habitat chip with ✓/✗) and add a rarity-coloured stage glow ring under the rig.
7. **Ranch:** pen cards as habitat-coloured tiles with 3 creature-face slots, a hunger/sample status chip and one action per card.
8. **Research:** strengthen the R7 hex board: completed = gold hex with ✓; available = function colour with a cost chip and a pulse; locked = dark hex "???"; a progress hex "3/9".
9. **My Lab:** a property card (stage art + land bar), a structure count chip, and a featured-specimen slot (3D render).
10. **Upgrades:** a tier ladder per upgrade (pips), icon tile, a cost chip and a BUY primary button; maxed = gold "MAX".
11. **Hatch/discovery reveal (R9):** see below.

## Final hatch presentation (production timing)
Current pre-reveal tiers are Normal 1.1 s / Rare 1.8 s / Extreme 2.2 s / Discovery 2.6 s, followed by the card. Targets are **total time to "continue" available**:

| Tier | Incubator react | Wobble | Cracks + light | Camera push | Shell break → creature | Card | Total |
|---|---|---|---|---|---|---|---|
| Normal (repeat common) | 0.2 | 0.5 | 0.4 | — | 0.3 | 1.2 (auto-dismiss allowed) | **≈ 2.6 s** |
| Rare+ | 0.3 | 0.9 | 0.8 | subtle (FOV −4) | 0.5 | 1.6 | **≈ 4.1–4.5 s** |
| First discovery | 0.4 | 1.1 | 1.0 + rising beams | FOV −6 | 0.6 + flash | 2.2 + "NEW DISCOVERY!" ribbon + Index note | **≈ 5.3–5.8 s** |

**Card (R9-style, MPL art):**
1. darkened backdrop (Rare+ only);
2. **rarity word** large in its rarity colour with a glow stroke;
3. **species name**;
4. a chip row: **Trait** (icon chip) · **Variant** (chip only when not Standard);
5. a one-line description;
6. "NEW DISCOVERY" ribbon when applicable;
7. one **CONTINUE** button. Tap anywhere skips the remaining animation (never blocks play).

**Repeat commons** after the 3rd hatch of the same species in a session use the Normal timing with a 0.8 s card.
**Not added:** Open ×3, auto-hatch, paid luck.

## Final mutation presentation
1. **Parent clarity:** both parents float above the two machine pods as small display rigs (client-only) during the charge, then dissolve into light that runs down the cables.
2. **Charge build-up:** 3 pulses whose speed increases (0.45 → 0.3 → 0.2 s) along Cable1–4; the core brightens in steps; ReactorPulse sound on each pulse (the hook exists but is unused today).
3. **Result chamber:** the Reactor core flashes, then the result rig appears in front of the console on a glowing ring and the reveal card follows (same card as hatch, with title "NEW MUTATION!").
4. **Secret:** the gold/violet double ring + a 0.4 s screen-edge shimmer + "SECRET MUTATION!" title. The recipe is still never shown before discovery.
5. **Failed secret attempt / failure:** a sputter, smoke and a short "The mutation fizzled — try different parents" note; no hint about secret recipes.

Recipes and odds are untouched.

## Creature reaction review (to run in Studio)
For each family anchor + one roster species (Gel: Slimelet/Gloamgel, Critter: Frostpup/Voltusk, Hopper: Pebbletoad/Glacierbit, Flyer: Sparkbug/Miremoth, Sprout: Mossbit/Bloomtail, Wisp: Magmawisp/Cryolume, Shellback: Rockling): trigger eating / favourite / acknowledge / sleepy / sample / sad through the care attributes and capture front views.

Expected per-family deviations:
- **Flyer / Wisp:** no ground hop; use a hover dip instead (the hop would lift them off their hover height).
- **Gel:** squash instead of pitch.
- **Shellback:** sleepy = tuck (lower 0.15) rather than a head pitch.
