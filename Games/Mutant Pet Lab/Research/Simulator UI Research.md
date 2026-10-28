---
type: research
game: "[[Mutant Pet Lab]]"
research_target: "UI/UX patterns"
researched_on: 2026-10-15
category: topic · ui
status: complete
tags:
  - research
  - ui
---
# Simulator UI Research

> Authority: **REFERENCE-level research.** It never overrides [[Design Decisions]] (approved: lab-skin UI, editable-in-Studio UI, drag→release→confirm build placement). Labels: OBS / INF / MPL (see [[Research Sources]]).

> [!warning] Evidence limit
> No game was played first-hand and no screenshots were taken. Per-game UI points are mostly **INF** from genre convention. The strongest UI evidence is the **DevForum community sentiment** (S37).

## Community sentiment
These themes come from several independent DevForum threads, 2020–2025 ([[Research Sources#Community: UI and mobile (DevForum)|S37]]):
1. **Too many buttons.** Advice: merge them into one menu, or use gestures and press-and-hold.
2. **Screen-edge conflicts on mobile.** Top-left has chat, top-right the leaderboard, and the bottom corners the controls. Buttons in the joystick zone can't be pressed.
3. **Oversized displays.** One critic said a third of the screen was spent on three numbers.
4. **Unclear icons.** Use icons that say what they do, or icon plus label.
5. **Cognitive overload.** Split one giant menu into focused screens.
6. **Device-specific UI.** Layouts for mobile, PC and controller.

## Patterns by screen

### HUD
- **What works:**
  - Currency and level grouped in one compact cluster.
  - Most state readable from the world: plants, eggs, pens (INF: [[Grow a Garden]], [[Steal a Brainrot]]).
- **What doesn't:**
  - A new counter or button for every system (INF: [[Pet Simulator 99]]).
  - Buttons at the top edge or in the thumb/joystick zones (S37).
- **Why:** Phones are the majority platform on Roblox (INF), and the edges are already taken.
- **What MPL could adapt:** The approved HUD already does this: status cluster, 7-tile nav bar shifted to clear Jump, Goals panel. Keep it.
- **What MPL should not copy:** Stacks of boost timers and event banners on the HUD.

### Shop
- **What works:**
  - The shop as a **place in the world**: Steal a Brainrot's conveyor, Steal An Egg's biomes ([[Steal a Brainrot]], [[Steal An Egg]]).
  - A shared rotating stock ([[Grow a Garden]]).
- **What doesn't:** Robux items mixed in with soft-currency items. Paid hatch multipliers ([[Bubble Gum Simulator Infinity]]).
- **Why:** In-world shops create something to look at and talk about.
- **What MPL could adapt:**
  - The Egg Shop counter is already in the campus Egg Facility.
  - Make the eggs on display physical models behind the counter, with the panel as the detail view.
- **What MPL should not copy:** Limited-time FOMO stock or paid luck.

### Collection / Index
- **What works:**
  - Grid of cards, silhouettes for undiscovered entries, a completion count, rarity colours.
  - This is the Index Collection Screen reference ([[Index Collection Screen]]).
- **What doesn't:** Index screens with no reward or story for completing them (INF).
- **Why:** The index is the long-term goal list.
- **What MPL could adapt:** Already approved and built: tabs, cards, detail view, discovery banner. Candidate: per-family completion rewards.
- **What MPL should not copy:** Pay-to-complete entries.

### Inventory / pet
- **What works:** The collection shown *in the world*: the following swarm in [[Bee Swarm Simulator]], the pet following you in [[Adopt Me]].
- **What doesn't:** A long list with no visual identity per creature (INF).
- **What MPL could adapt:** The Creatures panel already exists. Candidate: a "favourite follows you" feature in the [[Creature Overhaul]].
- **What MPL should not copy:** Dozens of pets following at once, which costs performance and clarity.

### Upgrade / research
- **What works:**
  - Quest-giver NPCs giving goals a voice ([[Bee Swarm Simulator]]).
  - One stat gating the next area ([[Steal An Egg]]).
- **What doesn't:** Deep trees where you can't see what each node does (INF).
- **What MPL could adapt:** Each Research node should show the *world change* it causes, for example with an icon of the unlocked structure.
- **What MPL should not copy:** Billions-scale requirement numbers.

### Build mode
- **What works:**
  - Place, then confirm on touch ([[Theme Park Tycoon 2]], S36).
  - A separate controller scheme (S35).
- **What doesn't:** Auto-place on release (INF).
- **What MPL could adapt:** **KEEP the approved flow.** Candidate: a controller nudge plus snap.
- **What MPL should not copy:** Free-form deep building tools on phones.

### Mobile UX
- **What works:**
  - One panel at a time.
  - Large tap targets.
  - Thumb-zone placement (S37).
- **What doesn't:** Overlapping panels; buttons under the joystick (S37).
- **What MPL could adapt:** Already enforced by MobileUX (one major panel; HUD and nav hide in panels and Build Mode; 56 px buttons).
- **What MPL should not copy:** Not applicable.

## Takeaway
MPL's approved UI direction already matches the community's best practice. The gap is **world-first information**: showing state on creatures, pens and eggs so players need fewer panels at all.
