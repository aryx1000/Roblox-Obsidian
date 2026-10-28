---
type: planning
game: "[[Mutant Pet Lab]]"
area: audio
status: current
updated: 2026-10-23
tags:
  - mutant-pet-lab
  - audio
---
# Audio placeholder audit (2026-10-23)

All 16 sounds live in `ReplicatedStorage.MutantPetLab.UI.Sounds`. Each carries the attribute `Interim` ("Roblox engine built-in sound … replace before launch") and is played through `Kit.Play(name)`.
- All 16 are **2D UI sounds**: parented to UI, no emitter part, so `MaxDistance` doesn't apply.
- **No sound was bought, uploaded or taken from an unlicensed source.**
- The `rbxasset://sounds/*` files ship with the Roblox client.

| Event (sound) | Fires from | Current placeholder | Intended emotion / function | Keep / replace | Volume now → target | Spatial? |
|---|---|---|---|---|---|---|
| **Click** | generic Kit buttons | `clickfast.wav` | light tactile tick | replace (soft bubbly "blip") | 0.35 → 0.25 | no |
| **Open** | panel open (4 callers) | `switch.wav` | airy lab-door "whoosh-pop" | replace | 0.35 → 0.30 | no |
| **Close** | panel close (3) | `switch.wav` (same as Open) | softer reverse whoosh | replace (must differ from Open) | 0.30 → 0.25 | no |
| **Error** | every refused request (27 callers) | `button.wav` | gentle "nope" bloop, never harsh | replace | 0.30 → 0.20 (it is frequent) | no |
| **Place** | Build Mode place (6) | `snap.mp3` | satisfying wooden "thunk" | **keep** until final | 0.45 → 0.40 | later: 3D at the placed structure |
| **Pickup** | Build Mode pick/move (4) | `clickfast.wav` | lift "pop" | replace | 0.35 → 0.30 | no |
| **Rotate** | Build Mode rotate (6) | `switch.wav` | short ratchet click | replace | 0.30 → 0.25 | no |
| **HatchCrack** | HatchSequence shards | `glassbreak.wav` | eggshell crack (organic, not glass) | **replace (priority)** | 0.25 → 0.40 | yes: at the incubator (RollOff 10–60) |
| **HatchPop** | creature appears | `snap.mp3` | cute "pop" + sparkle | replace (priority) | 0.50 → 0.45 | yes: at the incubator |
| **Discovery** | first discovery / NEW MUTATION reveal | `victory.wav` | rewarding fanfare jingle (2–3 s) | replace (priority) | 0.35 → 0.45 | no |
| **Success** | normal reveal / success toast | `electronicpingshort.wav` | short upbeat chime | replace | 0.30 → 0.30 | no |
| **MutateCharge** | Mutation charge start | `electronicpingshort.wav` | rising electric hum (loop-able, about 1.5 s) | replace (priority) | 0.25 → 0.35 | yes: at the Mutation Machine |
| **MutateSuccess** | mutation success | `victory.wav` (same as Discovery) | bio-electric "whump" + chime | replace (must differ from Discovery) | 0.30 → 0.40 | partly: whump 3D at the Reactor, chime 2D |
| **Sputter** | failed / secret-miss mutation | `Kerplunk.wav` | comic fizzle, friendly | **keep** (fits) | 0.40 → 0.35 | yes: at the machine |
| **ReactorPulse** | **no caller yet** (hook only) | `bass.wav` | low Reactor heartbeat | replace; wire into `MutationSequence` cable pulses | 0.20 → 0.20 | yes: at the Reactor core |
| **ResearchUnlock** | research purchase | `electronicpingshort.wav` | "data acquired" sparkle | replace | 0.30 → 0.35 | no |

## Gaps (final asset needs, not yet hooked)
- **Ambience:** campus bio-lab bed (bubbling tanks, distant hum), soft plot nature loop. 3D, low volume.
- **Creature voices:** short per-family chirps for acknowledge / eat / happy (Gel squish, Critter yip, Hopper croak, Flyer buzz, Sprout rustle, Wisp chime, Shellback clack). 3D, RollOff 8–40, rate-limited.
- **Egg:** incubator ready "ding" (3D), egg wobble rattle.
- **Feeding / harvest / sample-collect:** short positive SFX.
- **Music:** one calm main theme + an optional discovery sting. Must be licensed or original.

## Sourcing rule
Final audio must be original, commissioned, or from a license that clearly allows commercial Roblox use, and uploaded under the AYRX group. **No purchases or uploads without the owner's explicit approval.** Swapping is a one-line `SoundId` change per sound; the hooks are already in place. Clear the `Interim` attribute when a sound becomes final.
