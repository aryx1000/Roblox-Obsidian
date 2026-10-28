---
type: workflow
game: "[[Mutant Pet Lab]]"
status: active
updated: 2026-10-20
source: "owner instruction 2026-10-15"
tags:
  - mutant-pet-lab
  - workflow
---
# Claude Workflow

How Claude Code works on MUTANT PET LAB. The vault is the **primary human-readable source of truth** for context, decisions, references and design intent. Code lives in `~/Claude's Personal Workspace/MutantPetLab/` and is never copied here.

## Vault-first rule
Before reasoning from scratch about an existing system, design decision, roadmap item, known issue, visual direction or prior test:
1. Read the relevant vault notes first.
2. Read [[Current State]] and [[Roadmap]] when the request affects overall direction.
3. Use the vault's existing conclusions instead of reinventing them.
4. Inspect code or the Code Graph only when implementation detail is needed.
5. If the vault and code disagree, **report the discrepancy**; do not silently pick one.
6. Never overwrite a recorded human decision just because another solution seems possible.
7. When a new decision is made, record it (approved ones in [[Design Decisions]]) so the next session finds it.

### Authority order
```
OWNER'S CURRENT INSTRUCTION
    ↓
APPROVED DESIGN DECISIONS                  ([[Design Decisions]], then system/planning notes)
    ↓
USER REFERENCE LIBRARY                     (your living file + [[Owner Reference Library]]; filed References/ notes)
    ↓
CURRENT PROJECT STATE                      ([[Current State]], [[CLAUDE_PROJECT_STATE]])
    ↓
SIMILAR-GAME RESEARCH                      ([[Similar Games Overview]], Research/Similar Games/)
    ↓
GENERAL MARKET RESEARCH                    ([[Roblox Market Research]], Research/)
    ↓
CODE / GRAPHIFY                            (Code Graph/, current/source)
    ↓
INFERENCE
```
The user always overrides old notes when they explicitly change a decision. Record the change and mark the old entry **Superseded**.

**Competitive research never overrides an approved design decision by itself** (owner rule, 2026-10-15). Research findings become candidates in [[Design Decisions#Candidates to confirm (not approved decisions)]] and only bind after explicit owner approval. Research labels: OBS (observed in a source) / INF (inference) / MPL (recommendation); community opinions are labelled community sentiment.

## Session-start retrieval routine
For any significant task, read these three first:
- [[Mutant Pet Lab]] (dashboard)
- [[Current State]]
- [[Roadmap]]

Then read **only** the notes for the area involved; do not load the whole vault.

| Request | Read |
|---|---|
| UI | [[UI - Figma TODO]], `References/UI/`, [[Figma to Roblox UI (ui-figma-roblox skill)]] (the `ui-figma-roblox` skill for Figma mockups + port lessons) |
| Map | [[Map Overhaul]], `References/Map/` |
| Creatures | [[Creature Overhaul]], [[Species]], `References/Creatures/` |
| Economy | [[Economy]], [[Research Tree]], [[Egg Families]] |
| Persistence | [[Persistence]], [[Architecture]] |
| Any visual or design work | [[Design Decisions]] and the matching `References/` folder (plus images) |
| Bugs / regressions | [[Known Issues]], [[QA - Test History]] |
| Market / competitor / genre questions | [[Roblox Market Research]], then the matching `Research/` topic note (below decisions and references in authority) |

Smallest relevant context first; widen only if it isn't enough.

## Active reference source (owner rule, 2026-10-20)
The owner keeps a **living reference file**: [[References for games with assets that I like and dont like.]] (vault root). It grows over time with things the owner likes and dislikes (images, videos, notes).
- **Before designing or changing a player-facing system**, check in this order:
  1. Approved [[Design Decisions]].
  2. The relevant curated references: **[[MPL Visual Fingerprint]] (summary)**, [[Master Visual and Gameplay References]], the living file, [[Owner Reference Library]], and **[[Do Not Copy]]**.
  3. The relevant research notes ([[Similar Games Overview]] first).
  4. [[Current State]].
  5. Code / Graphify.
- **Examples:**
  - Creature redesign → creature references + [[Creature Overhaul]] + [[Creature Presentation Research]] + similar games.
  - Egg hatching → hatch references (R4, R5, R9, R10) + [[Egg Hatching Research]].
  - UI → UI references + [[Simulator UI Research]].
  - Map/buildings → map references + [[Map Overhaul]] + [[Reference Gaps]].
- **Never rely on generic assumptions when a relevant owner reference exists.**
- **New items in the living file:**
  - File the media into `References/Assets/Owner Library/` (embeds resolve by filename).
  - Add an R-entry to [[Owner Reference Library]], quoting the owner's words **verbatim** with analysis underneath.
  - Update [[Master Visual and Gameplay References]] and [[Do Not Copy]] (for dislikes).
  - **Never edit or delete the owner's text.**
- **Videos:** inspect local files by sampling frames (`MutantPetLab/tools/video_frames.swift` + `contact_sheet.swift`: compile with `swiftc -O`; ffmpeg isn't installed); record verified timestamps. For web videos, keep the link and mark timestamps unverified.
- **Not for backend-only tasks** (persistence, tests, economy maths): skip the reference check there.

### Creature work
Every new or reworked species starts from the owner's **Creature Specimen File** blueprint ([[Creature Template Sheets]], owner R15/R16) and ends with a silhouette check + a multi-angle review stage.

### When Studio is unavailable
Do design, reference and research work only. The execution order for the next Studio session lives in [[Next Build Brief]]; update it rather than starting new build plans.

## Image and reference rules
When a task is visual, read the relevant reference notes **and look at their attached images** before proposing a design. Classify everything:

| Kind | Meaning | Where it lives |
|---|---|---|
| **HARD REQUIREMENT** | A written decision the owner explicitly approved | [[Design Decisions]] (Status: Approved) |
| **REFERENCE** | Something whose qualities the owner likes | `References/` notes, `status: active` |
| **INSPIRATION** | May influence brainstorming; not a requirement | `References/Inspiration/` or `strength: inspiration` |

- A reference image is **never** an instruction to copy it. Extract principles: silhouette, proportions, mood, layout, interaction pattern, material, composition.
- Write the useful qualities down in the note's *Claude interpretation*, so later sessions don't reinterpret the image from scratch.
  - Bad: "Use this image."
  - Good: "Use the chunky rounded proportions, large readable eyes, short limbs and soft material transitions. Do not copy the exact creature."
- Written decisions beat images. If an image conflicts with [[Design Decisions]], the decision wins; raise the conflict.
- Inbox items ([[Reference Inbox]]) are raw. Help turn them into reference notes only when asked, and never promote one to a decision without the owner's approval.

## After the work
- New approved decision → [[Design Decisions]].
- Status / plan changes → [[Current State]], [[Roadmap]], [[Known Issues]], [[QA - Test History]].
- Session record → `Log/<date>.md`; durable lessons → `Knowledge/`.
