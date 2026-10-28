---
type: reference
game: "[[Mutant Pet Lab]]"
category: ui
status: needs-review
strength: reference
source: user
source_detail: "Screenshot of another Roblox game's Robux shop (game not identified)"
original_note: "[[These are some cool UI referenses]]"
date_added: 2026-10-15
tags:
  - reference
  - ui
  - monetization-sensitive
applies_to: [egg-shop, ui]
reviewed: 2026-10-20
decision_status: not-approved
---
# Shop Storefront Layout

## Image
![[758AFA15-CE2E-4C53-8ACA-401D7A809C1A_1_201_a.jpeg]]

## Owner's original comment
> "These are some cool UI referenses" (note title)
>
> "but whenever making a ui make it fully customizable in Studio"

This is the same comment as in [[Index Collection Screen]]. It is a candidate rule, **not** an approved decision ([[Design Decisions#Candidates to confirm (not approved decisions)]]).

> [!warning] Monetization content: layout reference only
> The screenshot shows a **Robux** shop: paid egg bundles, discounts and 2x Cash / 2x Luck game passes. MPL has **no monetization** and none may be added without your explicit approval ([[Design Decisions]], [[Monetization TODO]]). This note is a reference for **shop layout and presentation only**. Nothing here approves Robux products, passes or prices. Status is `needs-review` until you say how you want it used.

## What I like
Extracted from the image:
- **Hero banner** at the top for the featured item: dramatic art, a big product name, one plain-language line ("Hatches a random … creature!"), and a **?** button for odds/info.
- **Quantity tiers as a row of big buttons** (1 / 3 / 10 / 50). The colour escalates with tier (green → gold → rainbow) and each shows its amount underneath.
- **Small badges** ("POPULAR", "BEST VALUE") on cards, and **section dividers** ("-- PASSES --") that make a long scroll easy to scan.
- **Right-side category shortcuts** (Eggs / Passes / Cash) that jump within the shop, plus a subtitle under the title explaining what the shop contains.
- The same framed-modal language as the Index reference (title plate, big red X), so the screens feel like one family.

## What I do NOT want copied
- **The monetization itself:** Robux prices, paid eggs, 2x Cash / 2x Luck passes, "Exclusive" paid items. Not without explicit approval.
- **Pressure tactics:** strike-through "was" prices and "Save x%" anchoring. Review against [[Monetization Principles]] before anything like it is ever considered.
- The game's art, the "Titanic" naming, its icons, fonts, colours or branding.

## Apply this to MUTANT PET LAB
Use the **presentation** for MPL's existing **Cash** Egg Shop ([[Egg Families]]), which sells six families for in-game Cash only:
- A hero banner for the highest family you've unlocked (or a featured family), with its incubation time and a **?** that opens the hatch odds MPL already defines.
- A tier-coloured card per family, with locked families showing their level/research requirement ([[Research Tree]]).
- Section dividers and side shortcuts if the shop grows (for example Eggs / Lab Upgrades).
- **Pricing stays in Cash and comes from config** ([[Economy]]). No discounts, bundles or Robux.

## Relevant systems
- [[UI - Figma TODO]] (Egg Shop is on the design-pass list)
- [[Egg Families]] · [[Economy]] · [[Research Tree]]
- [[Monetization TODO]] · [[Monetization Principles]] (only if you ever approve monetization)
- [[Architecture#Client controllers]] (`EggShopController`)

## Claude interpretation
For the Cash Egg Shop: a featured-egg hero banner with a one-line description and an odds (?) button, then large tier-coloured family cards with clear lock states, short labels, section dividers and the shared framed-modal style. Prices are in-game Cash from config. Treat everything Robux-related in this image (bundles, passes, discounts, "exclusive" items) as **out of scope** unless the owner explicitly approves monetization in [[Design Decisions]]. If "customizable in Studio" is confirmed, build the shop as editable Studio UI with code only filling in data.
