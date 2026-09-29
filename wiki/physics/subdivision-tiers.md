---
type: topic
tags: [physics, progression, tiers]
created: 2026-09-28
updated: 2026-09-28
sources: ["[[project-vault-v2]]"]
status: active
---

# Subdivision Tiers

**Exactly 5 tiers.** Changing the count needs approval. ([[project-vault-v2]] §5)

| Tier | Shape | Feel |
|---|---|---|
| 1 | Cube | Clunky, snags easily, leans hard on [[jolt]], least efficient roll |
| 2 | Beveled Cube | Less snagging, slightly smoother |
| 3 | Rounded Polyhedron | More consistent roll, better flow |
| 4 | Near-Sphere | Better momentum retention, stable at speed |
| 5 | Perfect Sphere | Smoothest, most fluid |

## Rules
- Every tier must be a **meaningful mechanical improvement**, not just more polygons. Raw subdivision has diminishing returns, so each tier gets deliberately tuned physics.
- Tunable knobs: rolling efficiency, momentum retention, stability, bounce, snag resistance, steering, Jolt dependence, knockback response, and (only if approved) durability.
- **Earned only.** Robux cannot buy tiers, tier progress, Wins, stat progression, skips, or multipliers. (§6, see [[monetization-rules]])
- Subdivision progression is server-validated (§22).
- All tiers share one map ([[core-loop]]). [[shell-damage]] degrades handling on top of the tier baseline.

## In Studio (28 Sept 2026)
Tiers are built on the pre-v2 rule: session Wins thresholds **0 / 3 / 8 / 15 / 25**, friction 0.58 → 0.45, elasticity 0.10 → 0.03 by tier. These are prototype values tied to finish-line Wins, which v2 reopened. See [[studio-build]].

## Open questions
1. **How is a tier earned at all?** Tiers must come from gameplay, but v2 reopened Wins and left the distance-to-tier link unresolved. Right now nothing unlocks Tier 2. Blocks the Progression step in [[prototype-plan]].
2. Physics values per tier.
3. Does durability vary by tier?
