---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: animation
status: approved-direction
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - planning
  - phase-2
  - animation
---
# Creature Animation Spec

> [!success] APPROVED DIRECTION (owner, 2026-10-16) — not implemented yet
> Binding decisions: the *Phase 2:* entries in [[Design Decisions]]. Where this spec and a decision differ, the decision wins. Implementation follows [[PHASE2_IMPLEMENTATION_PLAN]] after the owner reviews it.
> **Built on:**
> - [[Creature Visual Language Spec]] (body plans)
> - [[Game Feel Research]]
> - [[Creature Silhouette and Personality]] (idle life)


## Approach
- **Procedural, client-side, per body plan.** No Humanoids, no Animator, no uploaded animation assets.
  - Parts-based display models animate by tweening part offsets (CFrame) around a root.
  - One shared client scheduler; no per-creature scripts.
- **Why:**
  - Works with parts-built creatures.
  - Edits stay inside Studio.
  - Zero server cost.
  - Matches the DevForum guidance to run pet motion on the client ([devforum](https://devforum.roblox.com/t/how-does-pet-simulator-do-it/2779392)).
- **Budget:**
  - Full rate (RenderStepped) within 40 studs, 10 Hz to 90 studs, frozen beyond.
  - At most 24 fully animated creatures per client; the rest drop to LOD.
  - To be measured on a real phone.
- **Server movement is unchanged:** the shared scheduler keeps creatures in containment, and the display model follows the proxy smoothly (lerp 0.15/frame).

## Animation set
Each entry gives: trigger · duration · per-plan notes.

| Animation | Trigger | Duration | Gel | Critter | Hopper | Flyer | Sprout | Wisp | Shellback |
|---|---|---|---|---|---|---|---|---|---|
| **Idle** | default | loop 2–3 s | squash breath 4% | breath + tail wag | throat pulse | wing flutter (slow) | leaf sway | bob ±0.4 + orbit spin | shell rise 2% |
| **Walk** | proxy moving < 6 studs/s | per step 0.35 s | slide + squash | 4-nub trot | short hops | low glide, wings fast | waddle on 2 feet | glide, orbit tilt | slow crawl, leg ripple |
| **Run** | ≥ 6 studs/s (follow/come-to-player) | 0.25 s steps | stretch + bounce | gallop bounce | long hops | fast glide | hop-waddle | streak + trail | scuttle |
| **Eat** | server feed event / feeder | 1.5 s | engulf (grow 10%, shrink) | head dips ×3 | tongue flick | hover-dip | roots dip, bloom opens | core flares, absorbs | head dips, crunch |
| **Sleep** | night-time (ClockTime ≥ 19 or ≤ 6, if a day cycle is added later) or wellbeing "Stable" rest windows | loop | flatten, eyes closed | curl up | tuck legs | land, wings fold | petals close | dim, sink to the ground | retract into shell |
| **Investigate** | a player within 8 studs (Curious: 12) | 2 s | lean + eye-stalk look | sniff toward the player | head tilt | hover closer | turn bloom toward the player | satellite reaches out | peek out of shell |
| **Social reaction** | owner nearby / favourite food / pet tap (later) | 1 s | happy jiggle | bounce + tail | double hop | loop-de-loop | bloom pop | sparkle burst | shell spin |
| **Hatch emergence** | hatch sequence | 1.2 s | ooze out, pop round | stumble, shake off shell | leap out | dry wings, take off | sprout up | condense from light | shell forms, then legs |
| **Mutation reaction** | result appears at the machine pad | 1 s | wobble, inspects self | sneeze + shake | surprised hop | wing check | petal flutter | orbit re-forms | shell knock |

## Shared rules
- **Look-at:** eyes/head track the nearest player within 10 studs, clamped to ±40° yaw and ±20° pitch, smoothed. This is the single most important "alive" cue.
- **Blink:** every 3–6 s at random (Calm: every 6–9 s).
- **Trait flavours** are layered on top ([[Creature Visual Language Spec#Trait readability (behaviour first, icon second)]]).
- **Variant effects** (glow pulse, hue drift, sparkle) run on the same scheduler.
- **No animation ever moves the authoritative proxy.** Animations stay inside the creature's own footprint (±0.6 stud), so containment and pen logic are unaffected.

## Scope for the first implementation slice (proposal)
1. Idle + walk + look-at + blink for **all 7 plan templates**.
2. Eat + sleep.
3. Hatch emergence + mutation reaction (needed by the reveal specs).
4. Investigate + social reaction.

Run is only needed if a "follow me" feature is approved later.
