---
type: topic
tags: [design, loop, currency]
created: 2026-09-28
updated: 2026-09-28
sources: ["[[project-vault-v2]]"]
status: active
---

# Core Loop

A Roblox downhill physics / obby survival game. Players sit visibly inside translucent resin-like geometric shells, avatar visible inside. ([[project-vault-v2]] §1)

**Fantasy:** evolve from a clunky cube into a perfect rolling sphere while surviving as far as possible down chaotic randomized courses. All [[subdivision-tiers]] play together on one shared map ([[map-generation]]).

Tone: simple, readable, replayable, physics-focused, socially chaotic, small scope.

## The loop (v2)
Spawn at top → descend randomized map → survive impacts → shell chips and fractures ([[shell-damage]]) → handling worsens → go as far as possible → shell shatters → die → currency proportional to distance → repeat. (§2)

**Run metric: distance / downward progress.** Not reaching a finish.

> [!danger] Superseded by v2: finish-line goal
> The pre-v2 objective was to reach a designated finish area, with "reach bottom = +1 Win". Do not build that rule unless re-approved. (§2, §6)
>
> **In Studio as of 28 Sept 2026:** this rule *is* built (`RoundService` gives +1 session Win at the finish), along with 46 track coin pickups. See [[studio-build]].

## Currency from distance
Locked: **farther survival = more currency.** (§10) Formula not locked. Candidates named, none approved: studs descended, module depth reached, checkpoints crossed, deepest point reached.

**Track pickups: reopened.** The old design had authored, respawning pickups with bigger bundles on risky shortcuts. Under v2 they may be secondary, redundant, or reworked. Neither required nor deleted; waiting on the human. (§11)

## Player interaction
Shared physical course; players can interfere. **Punch** (knockback) is approved as social physics. Players may inconvenience each other but must never be permanently prevented from playing. Punch values, cooldowns, immunity, and anti-grief are open. No paid mechanical advantage. (§12, see [[monetization-rules]])

## Server authority
Distance rewards, currency awards, and death/shatter state (if exploitable) are server-validated. Never trust client values for rewards. Proportionate, not overbuilt. (§22, see [[prototype-plan]])

## Open questions
1. **What happens after you die?** Players release together and the map regenerates every ~10 min ([[map-generation]]), but death ends the run. Respawn at top immediately, wait for next cycle, or spectate? The Vault only lists "round timing" as open.
2. Distance-to-currency formula.
3. Do track currency pickups stay alongside distance rewards?
4. Role of Wins after v2, and how distance relates to tier progression (see [[subdivision-tiers]]).
5. Punch mechanics and anti-grief rules.
