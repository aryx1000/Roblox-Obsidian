---
tags: [knowledge, localization, roblox]
sources: [Shift From Hell]
---

# Localization

Back to [[Knowledge/Index|Knowledge]].

Pattern from [[Shift From Hell]] 0.14.0 (English plus 555 Spanish strings):
- **Language:** `LocalizationService.RobloxLocaleId` (the app language), falling back to `Player.LocaleId`. English is the source text and the fallback, so a raw key is never shown.
- **One table per language:** `Strings_<code>.lua`. Adding a language never needs a UI rewrite.
- **Server text:** sent as an English template plus variables and translated on each client. Plurals go through `T.plural`.
- **In-world text:** tagged `SFH_L10n` and handled by a `WorldText` controller.
  - **Race bug (0.14.1):** when an attribute and its `Text` update in the same frame, re-read the live `Text` instead of a cached source.
- Handle **accented uppercase** properly (`UIKit.upper`).
- **CI check:** `tools/check_strings.py` fails on a missing translation or a placeholder mismatch.
- **Testing:** a Studio-only `SFH_StudioLocale` attribute forces a language. It's ignored live and removed after testing.
- Owner-only admin text can stay English.
