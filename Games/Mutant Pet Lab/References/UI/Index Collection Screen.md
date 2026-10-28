---
type: reference
game: "[[Mutant Pet Lab]]"
category: ui
status: active
strength: reference
source: user
source_detail: "Screenshot of another Roblox game's Index (game not identified)"
original_note: "[[These are some cool UI referenses]]"
date_added: 2026-10-15
tags:
  - reference
  - ui
applies_to: [index, ui]
reviewed: 2026-10-20
decision_status: approved-in-part (Direction C, UI-C1)
---
# Index Collection Screen

## Image
![[44032124-4FFF-48EB-9CBB-5B27576ECA02_1_201_a.jpeg]]

## Owner's original comment
> "These are some cool UI referenses" (note title)
>
> "but whenever making a ui make it fully customizable in Studio"

This comment covers both screenshots in the original note. See *Claude interpretation* and [[Design Decisions#Candidates to confirm (not approved decisions)]]. It is **not** an approved decision yet.

## What I like
Extracted from the image:
- **One framed modal with a strong title plate.** Icon + big bold "Index" title on a tab that sits on the frame, and a large red **X** close button in the corner (easy tap target).
- **Vertical category tabs on the left** (Pets / Eggs / Mutations), each a big icon tile with a short label. One screen covers the whole collection.
- **Card grid**, three across. Each card has the name above, the creature render on a colour-coded background, and **rarity odds as "1 in 25K"** text at the bottom.
- **Undiscovered entries are silhouettes with "???"**, which teases what is left to find without spoiling it.
- **Completion progress bar** ("8/10") with a reward icon beside it: a clear goal and payoff.
- **Hover/tap detail card** next to the grid: name, rarity line, large render on a light tile, and **"Hatches from"** with each egg and its percentage.
- Chunky outlined text, high contrast, and few words: readable at phone size.

## What I do NOT want copied
- The exact wooden-frame and parchment art, fonts, icons and colours of this game.
- Its creatures, names, egg names or numbers.
- Its HUD elements (money counter, hotbar, "EXCLUSIVE" tag) or any branding.
- The layout pixel-for-pixel. Take the structure, not the skin.

## Apply this to MUTANT PET LAB
MPL already has the data for this screen; the reference is about presenting it.
- **Tabs map directly:** Species ([[Species]], 36), Eggs ([[Egg Families]], 6), Mutations ([[Mutation Recipes]], 30, including 4 secret).
- **Odds text:** MPL's hatch tables already define per-egg chances ([[Egg Families]]). Show them as readable odds on cards and in the detail card's "Hatches from" list. Mutation-only species would show their recipe instead of an egg.
- **Silhouettes + "???"** for undiscovered species. For secret mutations, show the existing **hint** before discovery and the reveal after, as the game already does ([[Mutation Recipes]]).
- **Progress bar per tab:** for example "Discovered 12/36". It fits the first-discovery rewards in [[Economy]].
- **Card background colour by rarity** (Common…Mythic), plus variant badges from [[Traits and Variants]].
- **Theme is open:** MPL is a lab, so the frame could become lab materials (metal, glass, hazard trim) instead of wood. No visual direction is approved yet ([[Design Decisions]]).

## Relevant systems
- [[UI - Figma TODO]] (Index redesign is already on the backlog)
- [[Species]] · [[Egg Families]] · [[Mutation Recipes]] · [[Traits and Variants]]
- [[Architecture#Client controllers]] (`IndexController` builds the current Index)
- [[Responsive Mobile UI]] (tap targets, the 4 test viewports)

## Claude interpretation
Build the Index as one framed modal: left icon tabs (Species / Eggs / Mutations), a card grid with a rarity-coloured background, silhouette + "???" for undiscovered entries, odds text on each card, a per-tab completion bar with its reward, and a tap-to-open detail card listing where the creature comes from (egg odds or mutation recipe/hint). Big title plate, large close button, short outlined text. Keep MPL's own theme and data; never reuse this game's art, names or numbers. If the owner's "customizable in Studio" rule is confirmed, lay the screen out as editable Studio UI rather than generating it in code.
