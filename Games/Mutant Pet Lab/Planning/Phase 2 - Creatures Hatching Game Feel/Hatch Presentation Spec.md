---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: hatching
status: approved-direction
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - planning
  - phase-2
---
# Hatch Presentation Spec

> [!success] APPROVED DIRECTION (owner, 2026-10-16) — not implemented yet
> Binding decisions: the *Phase 2:* entries in [[Design Decisions]]. Where this spec and a decision differ, the decision wins. Implementation follows [[PHASE2_IMPLEMENTATION_PLAN]] after the owner reviews it.
> Design spec only. Nothing here changes Studio or game code until the owner approves it in [[Design Decisions]].
>
> **Built on:**
> - [[Egg Hatching Research]] (answers A–G)
> - [[Rarity Reveal Escalation]], [[Egg Design and Hatch Anticipation]]
> - [[Game Feel Research]]
> - [[Design Decisions#UI skin: friendly research device (lab skin, reference structure)]]


## What exists today (verified in `current/source`)
- **Incubation:** select the incubator, then HATCH. Times are 22–120 s per family ([[Egg Families]]).
- **Server:** rolls species, trait and variant ([[Traits and Variants]]) and returns only facts (`hatch returns only server facts for the reveal`).
- **Client reveal:** the `HatchReveal` panel in `MutantPropertyGui`.
  - A coloured tile with the first letter, the name, a rarity/variant/trait line and a NEW tag.
  - It pulses, then auto-hides after 7 s. OK closes it.
- **In-world creature:** the server-built ball body + 2 eyes in the plot's `Creatures` folder (`PropertyVisuals.Creature`). It appears only once the creature is assigned to a pen.
- **Gaps:**
  - No sound (UI kit `Sounds` slots are empty).
  - No in-world moment.
  - The variant doesn't show in pens.
  - The hatched creature goes straight into the inventory.

## Principles
1. **Hybrid.** Anticipation and arrival happen **on the incubator in the world**. A **compact card** carries the facts.
2. **Escalate with light, colour and space,** not with text or odds. Never show "1 in N". *(Updated 2026-10-20: the owner approved showing the **% chance** in the odds popup and on the hatch card; see [[Design Decisions#Egg interaction (owner, 2026-10-20)]]. Escalation still comes from light, colour and space.)*
3. **The longest sequences happen once:** the first discovery of a species, or a secret.
4. **Never block play.** Tap anywhere fast-forwards. Already-owned species play the short version automatically.
5. **Client-only presentation.** The server stays authoritative, and the client plays the sequence from the facts the server returns. No new trust surface.

## Tiers
How a hatch is classified is decided on the client from server facts:

| Tier | Condition |
|---|---|
| **Normal** | Common/Uncommon, no variant, species already discovered |
| **Rare** | Rare/Epic, **or** any variant (Luminous / Chromatic / Prismatic) |
| **First discovery** | `NewDiscovery == true` (any rarity) |
| **Extreme** | Not reachable from eggs: Legendary/Mythic are mutation-only (`EggFamilyConfig.MutationOnly`). The extreme tier lives in [[Mutation Reveal Spec]]. Eggs top out at "Rare + variant + first discovery" |

If several conditions apply, use the highest tier. A variant always adds its own beat (see *Trait and variant reveal*).

## Sequence per tier

| Beat | NORMAL (~3 s to card) | RARE (~4.5 s) | FIRST DISCOVERY (~6 s) |
|---|---|---|---|
| 0.0 Press HATCH | HUD and nav fade (MobileUX already hides them for majors). Incubator lid pops up 0.5 stud | same | same |
| Charge | The glass dome glows **mutation green**, ramping over 0.6 s. The egg wobbles twice (±8°, 0.15 s each) | 3 wobbles; cracks glow in the **rarity colour** | 3 wobbles, then a 0.3 s **pause**. The world dims 15% (client ColorCorrection tween) |
| Crack | Shell cracks; light leaks through | Cracks + a vertical beam (Neon cylinder, 1.2 s, rarity colour) | Same as Rare, plus a ring pulse on the ground |
| Burst | Shell pops into 6–10 shards (client-only parts, debris lifetime 1.2 s) and a **light burst** (PointLight flash 0.25 s) | Bigger burst + rarity-coloured particles | The creature appears as a **black silhouette for 0.4 s**, then its colour floods in |
| Creature | Lands beside the incubator, looks at the player, plays one personality idle ([[Creature Animation Spec]]) | Same + a small "show-off" spin | Same + the "NEW SPECIES" lab stamp slams onto the card |
| Card | Compact card, lower-centre (see below) | Card rim in the rarity colour | Card + stamp + "View in Index" emphasised |
| Exit | Creature walks to its pen or the holding spot | same | same, after the card is dismissed |

**Durations:**

| Tier | To card | Until free to move |
|---|---|---|
| Normal | ~3 s | ≤ 5 s |
| Rare | ~4.5 s | ≤ 6.5 s |
| First discovery | ~6 s | ≤ 8 s |

DevForum sentiment found that < 1 s is "too fast to read" and that long repeated animations annoy ([[Research Sources#Pass 2: hatching and simulator systems (2026-10-15)|S38, S47]]).

## Camera
- **No hard cuts** for Normal. If the incubator is on screen: a gentle 10–15% FOV/zoom push toward it, eased in and out (0.4 s each). If it isn't on screen: no camera move, and the card still appears.
- **Rare:** same + a slow 8° orbit during the beam.
- **First discovery:** a 0.8 s focus on the creature, then back to the player camera.
- **Mobile:** same rules. Never rotate more than 15° (motion comfort). No screen shake; at most a 2-pixel UI pulse.
- **Constraint:** this place has no PlayerModule (engine-side camera). Camera moves use a temporary `Scriptable` camera, then restore the previous CFrame and type. A known risk to test.

## Sound
The UI kit `Sounds` slots are empty today. **Sourcing rule (approved 2026-10-16):** Creator Store or custom audio. Candidates are recorded in a sound candidate list first, and the owner approves the final picks. Nothing is installed automatically, and nothing is copied from other games.

| Event | Sound |
|---|---|
| Lid / charge | soft servo click + rising hum (0.6 s) |
| Wobble | two "tok" ticks, pitch rising |
| Crack | glassy crackle |
| Burst | soft pop + short chime (Normal) / chime + sparkle (Rare) |
| First discovery | unique 1.5 s "discovery jingle" (also used by the Index banner) |
| Variant sting | its own 3-note sting per variant (Luminous warm, Chromatic shimmer, Prismatic bell) |

Volumes stay below the UI click level. Sounds are client-local, and other players don't hear them.

## VFX budget
- At most **1 PointLight** during the burst (destroyed after). Shell shards ≤ 10 client parts (destroyed ≤ 1.2 s). At most 1 ParticleEmitter (≤ 40 particles, 1 s).
- Neon beam: 1 part, client-only.
- Nothing persists after the sequence. Workspace budget is unaffected (client-side and temporary).

## Skip behaviour
- **Tap / click / ButtonA anywhere** jumps to the card. All tweens, sounds and debris are cancelled (DevForum pitfall: a skip must stop sounds and tweens too).
- **Auto-short** when the species is already owned and there's no variant: lid → pop → card, ~1.5 s.
- **Never auto-skipped:** first discovery, any variant.
- **Setting** (added later to the Guide/settings panel): "Hatch animations: Full / New only".

## Trait and variant reveal
Shown in this order, each as a beat on the creature and as a chip on the card:
1. **Species:** silhouette, then colour.
2. **Rarity:** card rim + nameplate colour + base ring under the creature ([[Creature Visual Language Spec#Rarity readability]]).
3. **Trait chip:** icon + word. The creature plays the trait's idle flavour once (e.g. Curious leans in, Calm slow blink).
4. **Variant last,** as the bonus sting: the variant effect switches on visibly on the creature (Luminous glow / Chromatic hue drift / Prismatic sparkle) + the variant sound + a chip in the variant colour.

## The card (lab-skin kit component)
Lower-centre, above the nav safe area.

**Contents, top to bottom:**
1. Species name (large).
2. Rarity word in the rarity colour.
3. Trait chip and variant chip.
4. Short description (1 line, from `SpeciesConfig.Description`).

**Buttons** (≥ 56 px, primary on the right):
- **Assign to pen** (default when a pen has space).
- **View in Index.**
- **OK.**

**Implementation note for later:** this replaces or extends `HatchReveal` as an editable StarterGui template ([[Design Decisions#UI is editable in Studio (hybrid architecture)]]).

## Creature entering the world
1. Lands beside the incubator and looks at the player (head turn toward the camera) — 0.6 s.
2. One personality idle — 1 s.
3. **If a pen has space:**
   - With **Assign** chosen, the creature walks (client-side visual path) to the pen gate and enters.
   - The server assignment happens through the existing request when the player presses Assign.
   - If the player closes the card instead, the creature waits in a **holding spot** next to the incubator with a small "needs a pen" bubble.
4. **If no pen exists:** it stays at the holding spot. The card shows "Build a containment pen" (links to Build Mode).
5. **Server truth unchanged:** the walk is cosmetic. Assignment is still a server request; nothing moves until the server confirms.

## Multiple incubators finishing together
- Play them **one after another in short form, rarest last.** Never more than one full sequence at a time.
- No multi-hatch purchase, no auto-hatch ([[Anti-Patterns#Pass 2: simulator features we should NOT copy]]).

## Mobile vs desktop
- **Identical sequence.** The card fits the 4 representative viewports (≥ 56 px buttons, text ≥ 15 px).
- **Mobile:** tap anywhere = skip. Joystick and Jump stay hidden during the sequence (MobileUX).
- **Desktop:** Space/click = skip. **Controller:** ButtonA = skip/confirm, ButtonB = OK.

## Acceptance (for the later implementation)
- Normal ≤ 5 s to free movement. Skip works at any beat with no leftover sound or debris.
- No server change is needed except optional data the client already gets.
- Holds 60 fps on a mid phone (to be measured on a device, not throttled Studio).
