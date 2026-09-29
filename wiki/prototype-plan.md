---
type: project
tags: [roadmap, prototype, engineering]
created: 2026-09-28
updated: 2026-09-28
sources: ["[[project-vault-v2]]"]
status: active
---

# Prototype Plan

**First objective: make the player become a cube and make rolling downhill feel good**, now expanded to include survival. ([[project-vault-v2]] §21)

## First prototype must validate
1. Encased avatar presentation
2. Cube physics, movement/control, camera
3. [[jolt]]
4. Downhill interaction and impact detection
5. Chipping/fracture, handling degradation, shatter, death ([[shell-damage]])
6. Distance tracking ([[core-loop]])

Nothing cosmetic, no crates, no monetization, no large map content until this is proven.

> [!warning] Contradiction
> [[project-vault-v2]] §21 says cosmetics, crates, and monetization wait until survival physics is proven. Studio already has all three, built against the pre-v2 order ([[studio-build]], checked 28 Sept 2026). Items 1-3 and downhill interaction exist in Studio. Impact detection and items 5-6 do not.

## Build order (§20)
Original: 1 Physics, 2 Map Generation, 3 Round Loop, 4 Progression, 5 Currency, 6 Player Interaction, 7 Cosmetics, 8 Crates, 9 Monetization, 10 Polish.

v2 says early priority should emphasize: rolling physics, shell damage, fracture feedback, damage-driven handling, death on shatter, distance tracking. Build through **playable vertical slices**; every stage leaves the game testable.

## Engineering rules (§18-19, §22)
- Built in **Roblox Studio** by a coding AI over MCP.
- Smallest correct implementation. Simple modules, clear responsibilities. No speculative architecture, frameworks, premature optimization, or rewrites of working code for style.
- All meaningful code maps back to a wiki/Vault requirement (see `CLAUDE.md` "Recording vs building").
- Server validates rewards, currency, progression, crates, purchases, chaos limits, and exploitable death state. Proportionate, not overbuilt.

## Open questions
1. **Is the survival-first order approved, or only suggested?** §20 keeps Progression (4) before Currency (5), then prioritizes distance tracking (currency-side work), and says any "broader reordering" needs approval.
2. Tier unlock rule is undefined, blocking step 4 ([[subdivision-tiers]]).
3. Save-data schema and persistence behavior.
4. UI design.
5. Audio / visual polish.
