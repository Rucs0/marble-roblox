---
type: topic
tags: [meta, overview]
created: 2026-09-28
updated: 2026-09-28
status: active
---

# Overview

Current state of the marble game. Start here, then use [[index]] to find pages. Timeline: [[log]].

## The one thing to know

**The design is v2, the code is v1.** The design baseline is [[project-vault-v2]] (survival, shell damage, distance currency). Studio already holds a working build of the *pre-v2* finish-line game: cube rolling, Jolt, Punch, a spiral track, finish-line Wins, track coin pickups, cosmetics, crates (see [[studio-build]], checked 28 Sept 2026). None of the v2 survival mechanics exist yet. The next build target is still [[prototype-plan]]: add [[shell-damage]], shatter, death, and distance tracking.

## The game in one line
Roll down 10 randomized stacked modules ([[map-generation]]) inside a breakable shell, evolving from cube to sphere ([[subdivision-tiers]]) and earning currency by how far you survive ([[core-loop]]). Progression is never sold ([[monetization-rules]]).

## Blocking questions
These stop real work. The rest are tuning values, fine as `TEMP` during the prototype.

| # | Question | Blocks | Page |
|---|---|---|---|
| 1 | What happens after death mid-cycle? | Round loop | [[core-loop]] |
| 2 | Is survival-first build order approved? | Order of work | [[prototype-plan]] |
| 3 | How is a tier earned? | Progression step | [[subdivision-tiers]] |
| 4 | Kill Everyone: does the buyer die, do victims get paid? | Chaos products | [[monetization-rules]] |
| 5 | Keep "finish effects" with no finish? | Cosmetic list | [[monetization-rules]] |
| 6 | Keep, adapt, or strip the pre-v2 code (finish Wins, Win tiers, track pickups, early cosmetics/crates)? | All v2 build work | [[studio-build]] |

## Open by design (Vault §23)
Each lives in its page's `## Open questions`:
- Tier physics values, durability, damage and fracture thresholds, deformation method: [[shell-damage]], [[subdivision-tiers]]
- Jolt force and cooldown: [[jolt]]
- Punch and anti-grief, Wins after v2, distance-to-tier link, distance-to-currency formula, track pickups: [[core-loop]]
- Cosmetic, Robux, and crate prices and odds: [[monetization-rules]]
- Round timing: [[map-generation]]
- UI, save schema, persistence, audio/visual polish: [[prototype-plan]]
