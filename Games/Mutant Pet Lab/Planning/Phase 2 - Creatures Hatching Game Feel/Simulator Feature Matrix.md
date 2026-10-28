---
type: planning
game: "[[Mutant Pet Lab]]"
phase: 2
area: features
status: approved-direction
updated: 2026-10-16
tags:
  - mutant-pet-lab
  - planning
  - phase-2
---
# Simulator Feature Matrix

> [!success] APPROVED DIRECTION (owner, 2026-10-16) — not implemented yet
> Binding decisions: the *Phase 2:* entries in [[Design Decisions]]. Where this spec and a decision differ, the decision wins. Implementation follows [[PHASE2_IMPLEMENTATION_PLAN]] after the owner reviews it.
> Full per-feature scoring is in [[Simulator Feature Research]], and the cross-research priority list in [[Roblox Market Research#Simulator feature priority matrix]]. This note narrows it to what fits MUTANT PET LAB **after** this phase.
>
> **Filter:** a feature must strengthen mutant creatures, the ranch, research, mutation, eggs, habitats, feeding, the Index, discovery or cozy visiting. **"A popular simulator has it" is not a reason.**


## YES (fits, adds depth, low bloat)

| # | Feature | Fit | Player value | Dev cost | Risk | Why it fits |
|---|---|---|---|---|---|---|
| 1 | Hybrid in-world hatch + reactor mutation reveal (this phase) | HIGH | High | MEDIUM | Low | The core "wow" moments of the game's own verbs |
| 2 | Silhouette body plans + visible variants everywhere (this phase) | HIGH | High | HIGH | Low | The biggest gap versus creature games |
| 3 | Creature idle life, look-at, eat/sleep (this phase) | HIGH | High | MEDIUM | Low | Makes specimens feel like organisms |
| 4 | Welcome egg + first-discovery guarantee (this phase) | HIGH | High | LOW | Medium (economy re-sim) | Signature payoff by ~2 min |
| 5 | Direct in-world harvest / collect actions | HIGH | Medium | LOW | Low | Fewer panel steps in the core loop |
| 6 | Rotating "lab requests" built on the assignment system | HIGH | Medium | LOW | Medium (grind if too many) | Research-flavoured goals, optional |
| 7 | Per-family Index milestones → cosmetic lab decor | HIGH | Medium | LOW | Low | Long-term goal without stat creep |
| 8 | Progressive secret hints + Index silhouettes + variant pity | HIGH | Medium | LOW | Low | Rewards experimentation, no wiki dependence |
| 9 | Read-only lab visits + Specimen Showcase of server rarities + Discovery Board | HIGH | Medium | MEDIUM | Medium (griefing; must not interfere) | Cozy social proof |

## MAYBE (good fit, needs a design pass first)

| Feature | Fit | Value | Cost | Risk | Condition |
|---|---|---|---|---|---|
| Valley weather / scheduled reactor surges biasing traits or variants | HIGH | High | HIGH | Medium | Only scheduled and predictable; no FOMO, no admin-only randomness |
| Wild specimen sightings in biomes | HIGH | High | MEDIUM | Low | Gives biomes a function; never stealable |
| Light lineage display (show parents on mutated creatures) | HIGH | Medium | LOW | Low | Store parent species on creation (schema change) |
| Bond meter → cosmetic idle unlock | MEDIUM | Medium | MEDIUM | Medium (chore risk) | No stats from bond |
| Expeditions via the dormant Expedition Arch | MEDIUM | Medium | HIGH | Medium | Only if it adds discovery, not idle income |
| Feeder upgrades (automation inside play) | MEDIUM | Low | LOW | Low | Never auto-play |

## NO (generic, grindy or pay-to-win)
- **Rebirth / prestige resets:** resetting a ranch contradicts the cozy-ownership fantasy; a shallow loop.
- **Trading / gifting (for now):** scam history in [[Adopt Me]]; child safety.
- **Paid hatching:** multi-hatch, luck potions, paid timer skips ([[Anti-Patterns]]).
- **Auto-hatch / AFK-optimal farming.**
- **Daily-login streaks and mandatory chores.**
- **Limited-time-only secrets / fake scarcity / admin-only events.**
- **Wealth leaderboards, PvP, stealing, races.**
- **Pets as pure stat multipliers;** extra currencies beyond Cash + Research.
- **Random outcomes that lower value** (downgrading re-rolls, mutation replacement).
