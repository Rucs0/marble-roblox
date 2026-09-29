---
type: topic
tags: [levels, map, generation]
created: 2026-09-28
updated: 2026-09-28
sources: ["[[project-vault-v2]]"]
status: active
---

# Map Generation

One shared map for everyone. Lobby at the top, all players released together. ([[project-vault-v2]] §8)

**10 vertically stacked randomized modules.** The whole stack regenerates about every 10 minutes. Inspiration: **Tower of Hell flipped upside down**, the stacked-obby format only, not its content. Focus: descending, falling, rolling, bouncing, surviving physics hazards.

## Module rules (§9)
Every module uses a standard connection / footprint so the stack is coherent. Each must be independently playable, connect cleanly above and below, and work in any stack position. Repeats are fine in the proof of concept.

## Proof-of-concept modules

| Module | What | Focus |
|---|---|---|
| Ramp Maze | Branching downhill maze: route choices, dead ends, drops into the void, safe vs risky paths | Navigation, steering |
| Bounce Yard | Trampoline / bounce obstacles to cross or pass through | Timing, recovery, bouncing, [[jolt]] |
| Pinball Pit | Bumpers, angled walls, ricochets, paddles, funnels | Chaos, social physics |

## What the proof of concept must show
Modules stack correctly, random order works, 10-level generation works, repeats don't break the map, transitions stay playable, and it feels coherent.

**Do not build a large module library before the generator is proven.** Adding a 4th module type needs approval.

**In Studio (28 Sept 2026):** no module generator exists. `MapGenerator` builds one continuous authored spiral track (256 segments, 500-stud drop). The 600 s cycle with a 10 s countdown matches the ~10 min regen. See [[studio-build]].

Map cycle also gates "Kill Everyone", once per generated map ([[monetization-rules]]). Relationship to death/respawn is open, see [[core-loop]].

## Open questions
1. Round timing details (exact regen interval, what the lobby does between cycles).
