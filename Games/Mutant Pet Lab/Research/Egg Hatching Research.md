---
type: research
game: "[[Mutant Pet Lab]]"
research_target: "egg opening / hatching presentation"
researched_on: 2026-10-15
category: topic · hatching
status: complete
tags:
  - research
  - hatching
---
# Egg Hatching Research

> [!success] Decision outcome
> Owner decision 2026-10-16: the **hybrid in-world hatch is approved** (Normal ~3 s, Rare ~4–5 s, First discovery ~5–6 s, Secret strongest and the Reactor may react). Reveal order Species → Rarity → Trait → Variant. Short version for repeats; safe skip. The creature enters the world cosmetically. Sounds through the owner review gate. See [[Design Decisions]] (*Phase 2:* entries).

> Authority: REFERENCE-level research ([[Claude Workflow#Authority order]]). Nothing here is approved. Ideas go to [[Design Decisions#Candidates to confirm (not approved decisions)]].
> Labels: **OBS** = observed in a cited source · **INF** = inference · **MPL** = recommendation. Sources are in [[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)]].
> Visual references saved: [[Egg Design and Hatch Anticipation]] · [[Rarity Reveal Escalation]].

> [!warning] Evidence limit
> No game was played first-hand and no in-game hatch was recorded. Hatch sequences come from guides, official game descriptions, DevForum feedback threads and official promo images. Timings are **INF** unless marked otherwise.

## MPL today (from `current/source`)
- **New profiles:** 3 starter creatures (Slimelet, Rockling, Sparkbug), 150 Cash and **no egg**. Only migrated v1 profiles got one. The Field Research Egg costs 60 Cash, and its config lists a "Welcome" acquisition route, but I found no code that grants it (INF; verify).
- **Incubation:** 22 s for the Field egg up to 120 s for the Unstable egg. These are **already short**, closer to "anticipation" than to "wait wall".
- **Hatch:** select the incubator → HATCH → a **panel pops up** (`HatchReveal`):
  - A coloured tile with the species' first letter.
  - Name; rarity/variant/trait/family line.
  - A **NEW** tag on first discovery.
  - A pulse, then it auto-hides after 7 s, with an OK button.
- **After the hatch:** the creature goes into the inventory. Nothing happens in the world. No sound (the kit `Sounds` slots are empty).
- **Not egg results:** mutation-only species, including all Legendaries and secret Mythics (`EggFamilyConfig.MutationOnly`). So eggs never reach the top rarities, which is a strength (see C).

## Examples

### Adopt Me! (care-to-hatch, in-world)
- **OBS:** Eggs come from the Nursery gumball machine. The egg has **needs/tasks** like a pet (feed, bathe, play, sleep, school) before it hatches. Placed in a nest, the egg slowly cracks open ([[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)|S41]]). Odds are fixed at purchase (S41).
- **Why it works (INF):** You bond with the egg before it hatches, so the anticipation is *earned*. The hatch happens in your world.
- **Annoying (INF):** Task gating can feel like chores when you just want the pet.
- **MPL could adapt:** An optional "care" bonus on incubators. **Avoid:** mandatory chores before every hatch.

### Grow a Garden (egg placed in the garden, real-time timer)
- **OBS:** Buy at the Pet Egg Shop, place the egg in your garden, and wait for a real-time countdown; higher tiers take longer, some up to 8 h. Pets and an Egg Incubator structure (up to 10× faster, unlocked by achievements) shorten hatching ([[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)|S40]]).
- **Why it works:** The egg is a **world object on your property**. Speeding it up is a progression goal.
- **Annoying:** Multi-hour timers. **OBS:** a paid skip exists for the related pet mutation machine (S43).
- **MPL could adapt:** Eggs incubate on the plot (already true). Hatch speed as a Research/upgrade reward. **Avoid:** hour-scale timers with paid skips.

### Steal An Egg / Ride A Pet (physical eggs, carry and nest)
- **OBS:**
  - Eggs are carried by hand to a pen or nest. Hatch time varies by rarity ([[Steal An Egg]]).
  - Ride A Pet eggs have a **break timer**, and the egg must reach your nest in time ([[Ride A Pet]]).
  - Official promo art shows eggs whose **shape and pattern telegraph the creature**: spiked dino egg, flame egg, glowing cracked egg with a countdown ([[Egg Design and Hatch Anticipation]]).
- **Why it works:** The egg is a toy and a preview at the same time.
- **MPL could adapt:** Family-specific egg models. Glowing cracks in the last seconds of incubation.

### Pet Simulator 99 / Bubble Gum Simulator Infinity (screen-centred batch hatching)
- **OBS:**
  - The genre's typical hatch puts the egg in front of the camera and opens it.
  - Multi-hatch exists (BGSI paid Triple Hatch, S14).
  - Auto-hatch exists (BGSI; scripts also add it for PS99, S45).
  - BGSI added **auto-delete from the inventory menu** as quality of life (S45).
  - PS99 promo art teases a mystery silhouette, "1 in ???" ([[Rarity Reveal Escalation]]).
- **DevForum hatch implementations (S38):** Egg-in-front-of-camera is built either with a ViewportFrame (no particles) or by binding the egg to the camera each frame.
- **Why it works:** Very fast loops; rarity is shown with colour and glow.
- **Annoying, community sentiment, outside Roblox too:**
  - Repeated per-egg animations drag when opening many.
  - Pokémon GO grouped simultaneous hatches into one animation.
  - An itch.io player asked for a hatch skip and the developer added one (S47).
- **MPL should avoid:** Batch egg spam, paid multi-hatch, auto-hatch replacing play.

### Sol's RNG (rarity-escalation cutscenes)
- **OBS:**
  - Rare rolls play a **special cutscene** and may be announced to the server.
  - Settings include a **cutscene-skip rarity threshold** (low tiers skip automatically), auto-equip threshold, delete/swap warnings, and a toggle for server sound effects ([[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)|S46]]).
  - Promo images: each rare tier is a completely different colour world, with a title and odds ([[Rarity Reveal Escalation]]).
- **Why it works:** The *length and spectacle scale with rarity*, and common results don't waste time.
- **MPL could adapt:**
  - Rarity-scaled reveal length.
  - An optional server notice for secret discoveries.
  - A **skip-threshold** idea, simplified to "skip the animation for species you already own".
- **MPL should avoid:** "1 in 800,000,000" gambling framing; luck potions.

### Dragon Adventures (egg → hatchling → adult)
- **OBS:** Hatch and raise from birth. The promo shows egg → baby → adult sharing one pattern ([[Dragon Adventures]], [[Egg Design and Hatch Anticipation]]).
- **MPL could adapt:** The egg's colour and pattern match the creature it becomes (at least per family).

### DevForum feedback on hatch animations (community sentiment, S38)
- **Too fast to read.** Two of three repliers on one thread said the egg and pet appear too quickly.
- **Add a light burst on opening.** Two of three repliers.
- **Add sound and 2D particles** (confetti, shell burst). One replier on another thread.
- **Skip implementation pitfall:** a skip must also cancel sounds and tweens, not only the model.

## Answers

**A. In-world, screen reveal, or hybrid?** **Hybrid.**
- The **anticipation and the creature's arrival** happen *in the world*: the incubator on your plot cracks, glows, and the creature hops out and walks to its pen.
- A **compact reveal card** (screen) carries the information: name, rarity, trait, variant, NEW.
- Why: in-world fits the cozy ranch and "pet, not item" goals. A card is still needed for readability on phones. Every strong example keeps the information short and puts the spectacle where the creature is (S38, S41, S46).

**B. How long should a normal hatch feel?** About **2.5–3.5 s** from pressing HATCH to the card readable, and **≤ 5 s** until the creature is free to walk.
- DevForum: "too fast to comprehend" means under about 1 s is too short.
- Sentiment against long repeated animations means much over 5 s gets annoying (INF from S38, S47).

**C. How should rare / secret / first-discovery hatches escalate?** Escalate **length, light and space, not text**:
- Rare adds a tinted beam and one extra beat.
- First discovery adds a lab "NEW SPECIES" stamp and an Index entry animation.
- Secret / Mythic: the Mutation Reactor responds in the sky, plus an optional server notice. Only via mutation, because eggs can't produce them.

Reserve the longest sequence for *first-ever* events so it is never repeated (S46 pattern).

**D. Skip after seeing it before?** **Yes.**
- Tap anywhere to fast-forward any hatch.
- Automatically use the short version for **species already owned** (common duplicates).
- **Never auto-skip a first discovery or a secret.**
- A settings toggle "Full hatch animations: always / new only".

Skip must cancel sound and tweens cleanly (S38 pitfall).

**E. Transition into the property / pen?**
1. The creature lands beside the incubator, looks at the player, plays one personality idle.
2. It walks to its **assigned or nearest free pen**. If there is none, it stays in a holding area with a soft "Needs a pen" marker.
3. The card's action buttons: **Assign to pen** (default when one is free) · **View in Index** · **OK**.

This replaces the "teleport into inventory" feel ([[Steal a Brainrot]] delivery-walk pattern).

**F. Layering traits and variants?** Reveal in order, each as a beat on the *creature*:
1. **Species** (silhouette, then colour).
2. **Rarity colour** (card rim and beam).
3. **Trait chip** (icon + word).
4. **Variant last**, as the "bonus" sting: the Luminous / Chromatic / Prismatic effect switches on visibly on the creature, with its own sound.

Variants are the closest thing MPL has to a rare surprise, so they get the final beat.

**G. Mobile vs desktop?** Same sequence, different framing:
- **Mobile:** the camera gently frames the incubator (no hard cut). The card sits in the lower-centre safe area above the nav, with buttons ≥ 56 px. Tap anywhere to skip. HUD and nav hide during the beat (MobileUX already does this for majors).
- **Desktop:** the same, with Space/click to skip.
- **Controller:** ButtonA to skip or confirm.
- Avoid screen shake on mobile beyond a tiny pulse.

## Recommended MPL hatch flow
*Proposal only. Not implemented. Needs owner approval.*

| | NORMAL HATCH | RARE HATCH (Rare/Epic, or any variant) | FIRST DISCOVERY | SECRET / EXTREME (mutation-only Mythic; never from eggs) |
|---|---|---|---|---|
| **Sequence** | Incubator glow ramps (0.6 s) → egg wobbles twice → cracks with green light leaking → shell pops (light burst) → creature lands, looks at player | Normal + an extra wobble, cracks glow in the **rarity colour**, a rarity-tinted beam rises from the incubator | Rare sequence + freeze-frame on the creature's silhouette (0.4 s) → colour floods in → **"NEW SPECIES" lab stamp** on the card | Happens at the **Mutation Reactor**: the core surges → sky tint in the creature's colour → the creature materialises on the dais → stamp. See [[Mutation Reveal Research]] |
| **Camera** | No cut. A gentle 10–15% push toward the incubator if it is on screen; otherwise nothing | Same + a slight slow orbit | Short frame on the creature (≤ 1 s), returns to the player camera | Reactor framing shot (≤ 2 s), then returns |
| **Sound** | Wobble ticks → crack → soft "pop" + a short chime | Pitched-up chime + a rarity sting | A unique "discovery" jingle | Reactor hum swell → bass hit → discovery jingle. Optional server-wide soft chime (toggleable) |
| **VFX** | Crack glow, shell shards (6–10), small sparkle | + Beam, + rarity-coloured particles | + Silhouette fill, + stamp | + Reactor pulse, sky tint, ring shockwave on the plaza |
| **Duration** | ~3 s to card; ≤ 5 s to free | ~4.5 s | ~6 s | ~8 s (once per species ever) |
| **Skip** | Tap/click/ButtonA anytime; auto-short if the species is already owned | Tap to skip after the beam starts | Not auto-skipped; tap fast-forwards to the card | Not auto-skipped; tap fast-forwards to the card |
| **Trait/variant** | Trait chip on the card; variant sting if any | Same; variant gets its own beat on the creature | Same | Same |
| **Index update** | The Index count ticks silently (small toast if a family milestone) | Same | Card button "View in Index"; the Index tab shows the new entry with a glow on first open | Same + secret badge |
| **Into the world** | Walks to its pen / holding area | Same | Same, plus one personality idle first | Walks from the reactor plaza to the player's plot? **Too far.** Instead: teleport shimmer to the plot after the card |
| **Mobile** | Card lower-centre, HUD hidden ≤ 3 s, tap to skip | Same | Same | Same; no screen shake |

**Multi-egg:** MPL has several incubators. If several finish together, hatch them **one after another, in short form, rarest last** (the Pokémon GO grouping lesson, S47). No paid multi-hatch.

## Sources
[[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)]] · first pass: [[Research Sources]]
