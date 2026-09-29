---
type: project
tags: [studio, code, engineering]
created: 2026-09-28
updated: 2026-09-28
sources: ["Roblox Studio place 'Untitled Marble Game' (placeId 93657953836512), read 2026-09-28"]
status: active
---

# Studio Build

What actually exists in Roblox Studio, checked 28 Sept 2026 via the Studio MCP. Studio is the live truth for behavior (`CLAUDE.md`). Script comments cite Vault section numbers, so this was built by a coding AI against the Vault.

**Headline: it implements the pre-v2 (finish-line) design, not [[project-vault-v2]].** Steps 1-9 of the old build order in [[prototype-plan]] exist in some form. None of the v2 survival mechanics do.

## What's there

| System | Scripts | State vs v2 |
|---|---|---|
| Cube body, rolling, camera-relative steering | `CubeServer`, `CubeClient`, `PhysicsConfig` | Matches the first objective |
| [[jolt]] | `CubeServer`, `CubeClient` | Built. Server-limited. `JoltVelocity = 48`, `JoltCooldown = 2.5` s |
| Map | `MapGenerator`, `MapRuntime` | **One continuous authored spiral track** (256 segments, drops 500 studs), not 10 stacked random modules ([[map-generation]]) |
| Round loop | `RoundService`, `RoundConfig` | 600 s cycle incl. 10 s countdown. **Finish +1 session Win** (the rule v2 says not to build, [[core-loop]]) |
| Tiers | `ProgressionService`, `SubdivisionConfig` | 5 tiers by session Wins: **0 / 3 / 8 / 15 / 25**. Friction 0.58 → 0.45, elasticity 0.10 → 0.03 ([[subdivision-tiers]]) |
| Currency | `CurrencyService`, `CurrencyConfig` | **46 authored track pickups** (40 singles worth 1, 6 bundles worth 5), respawn 15 s. The system v2 reopened. No distance reward |
| Punch | `PunchService`, `PunchRuntime`, `PunchConfig` | Built |
| Cosmetics, store | `CosmeticService`, `CosmeticRuntime`, `CosmeticClient`, `CosmeticCatalog`, `PaidCosmeticStore` | Built. Earned items session-only, Robux items saved |
| Crates | `CrateService`, `CrateConfig` | Built |
| Robux | `MonetizationService`, `MonetizationConfig` | Cosmetics only, `LiveEnabled = false`, product IDs are 0 |
| HUD | `HudView`, `UITheme` | Shows Wins, coins, tier progress, Jolt/Punch cooldowns |

## What's missing vs v2
- [[shell-damage]]: no impact detection, chipping, fracture, shatter, or death (no match for "shatter" anywhere in code).
- Damage-driven handling degradation.
- Distance tracking and distance-based currency.
- Chaos developer products, including Kill Everyone ([[monetization-rules]]).
- Persistence: Wins and coins are session-only ("persistence remains an unresolved Vault decision", `RoundService` line 2).

## Open questions
1. **Keep, adapt, or strip the pre-v2 systems?** Finish-line Wins, Win-based tier thresholds, and track pickups contradict v2's reopened rules. Changing them is building, so it needs Zarar's or Marcos' word.
2. The spiral track vs 10 stacked modules: replace it, or keep it as a test course until the generator exists?
3. The cosmetics, crates, and store were built before survival physics was proven, which v2 §21 says not to do. Leave them dormant or remove them?
