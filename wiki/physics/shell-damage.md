---
type: topic
tags: [physics, shell, damage]
created: 2026-09-28
updated: 2026-09-28
sources: ["[[project-vault-v2]]"]
status: active
---

# Shell Damage

The shell around each player is physically breakable. The heart of the v2 [[core-loop]]. ([[project-vault-v2]] §3-4)

## Breaking
Heavy crashes chip edges, remove chunks, create fractures, make the shell jagged, and finally shatter it. Example: a cube hitting a corner hard chips part of an edge. Repeated hard hits progressively deform and weaken it.

**Shatter = death, run ends.**

**In Studio (28 Sept 2026):** none of this exists yet ([[studio-build]]).

Approved stages: **Intact → Chipped → Fractured → Heavily Damaged → Shattered.**

Damage must be **visually readable**, not only a hidden health bar.

## Damage affects handling
Locked: **damage physically makes the shell harder to control and survive with.** Not cosmetic.

As the shell gets chipped, asymmetric, and jagged, it may worsen: rolling smoothness, balance, stability, trajectory, snagging, bounce, momentum retention. Implementation is a prototyping decision (mine, per `CLAUDE.md`, but how it *feels* is design).

Interaction with [[subdivision-tiers]]: tier sets the starting handling, damage degrades it. Whether tier affects durability is only "if later approved" (§5).

## Server authority
Death/shatter state if exploitable, and major damage validation where practical, go through the server (§22).

## Open questions
1. Durability model.
2. Damage thresholds per stage.
3. Fracture thresholds.
4. How deformation is implemented (mesh swap per stage, CSG, fragment parts, etc.).
5. Does tier affect durability? Not approved yet.
