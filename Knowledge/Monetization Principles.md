---
tags: [knowledge, monetization, roblox]
sources: [Shift From Hell, Mutant Pet Lab]
---

# Monetization Principles

Back to [[Knowledge/Index|Knowledge]]. The full proposal is in [[MONETIZATION]] (SFH).

## Rules
- **Cosmetic only.** Nothing sold changes speed, score, rewards or difficulty, and free players lose nothing.
- **No paid random rewards.** No loot boxes; Roblox restricts them.
- **Server-authoritative ownership:** `UserOwnsGamePassAsync` or the server `PromptGamePassPurchaseFinished`, never the client.
  - Developer products are granted only in `ProcessReceipt`, idempotently: save the receipt id with the grant, and return `NotProcessedYet` while data can't be saved.
- **Sell only what the game actually renders today.** Emotes waited until custom animations existed.
- **Nothing gets created or bought without explicit owner approval.** Claude never spends Robux. MPL Build B shipped with no monetization by design.

## Roblox facts learned
- Roblox **disabled cross-experience pass sales on 2026-05-30**. Sell passes in the experience where the shop lives; ownership checks still work from other experiences.
- The **group owner automatically owns** the group's passes, so test perks with another account.
- You can't create a bundle that "includes" other passes; it has to be a separate pass.

## SFH reference prices
VIP 199, Uniforms 99, MopSkins 75, CheckoutFX 99, NameTags 49 R$. Plan: launch low for about 2 weeks, compare conversion, then raise the best seller one step.

Related: [[Server Authority and Anti-Exploit]], [[Economy and Progression Design]]
