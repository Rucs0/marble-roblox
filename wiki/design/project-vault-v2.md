---
type: source
tags: [design, baseline]
created: 2026-09-28
updated: 2026-09-28
raw: ["raw/Roblox_Marble_Game_Project_Vault_v2.md"]
---

# Project Vault v2.0

The human's design baseline for the game, 27 sections. Declares itself the source of truth; per `CLAUDE.md`, that authority now lives in the wiki pages built from it plus every dated decision since. Stage at writing: **Phase 2, Development Preparation**.

## What v2 changed
The v2 revision replaced "reach the finish line" with **breakable shell survival + damage-driven handling degradation + distance-based currency**. Three older systems were reopened, not deleted: the finish-line Win rule, Wins in general, and on-track currency pickups.

## Where each section went

| Vault sections | Page |
|---|---|
| 1, 2 (vision, loop) | [[core-loop]] |
| 3, 4 (breakable shell, handling) | [[shell-damage]] |
| 5, 6 (tiers, no bought progression) | [[subdivision-tiers]] |
| 7 (Jolt) | [[jolt]] |
| 8, 9 (shared map, modules) | [[map-generation]] |
| 10, 11 (distance currency, track pickups) | [[core-loop]] |
| 12 (Punch, player interaction) | [[core-loop]] |
| 13-17 (cosmetics, store, crates, monetization, chaos products) | [[monetization-rules]] |
| 18-22 (environment, philosophy, dev order, first objective, server authority) | [[prototype-plan]] |
| 23 (open areas) | [[overview]] open questions |
| 24-26 (vault check, no silent improvements, change control) | `CLAUDE.md` "Recording vs building" and "What is true" |

## Contradictions inside the source
Five tensions found on ingest, each filed as an open question on the page it affects:
1. No defined way to earn a tier ([[subdivision-tiers]]).
2. Kill Everyone vs no paid advantage ([[monetization-rules]]).
3. Build order ambiguity ([[prototype-plan]]).
4. "Finish effects" with no finish ([[monetization-rules]]).
5. What happens after death mid-cycle ([[core-loop]]).
