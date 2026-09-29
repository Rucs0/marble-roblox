# Roblox Marble Game — Project Vault v2.0

This file is the authoritative design and development baseline for the Roblox Marble Game.

Any AI, developer, or coding agent working on this project must treat this Vault as the source of truth.

## Governance Rules
- Do not silently add, alter, reinterpret, or expand the game beyond this Vault.
- Every meaningful implementation decision must trace back to an approved rule in this document.
- If an AI or developer thinks of an idea that is not explicitly covered here, they must stop before implementing it, tell the user what they thought of, explain briefly why it may help, ask for explicit approval, and only implement it after approval.
- Balancing variables explicitly left open may be tuned during prototyping.
- Locked design rules may not be changed without explicit user approval.
- New approved decisions that supersede older rules should be reflected in the Vault.

## 1. Core Game Vision
The game is a Roblox downhill physics / obby survival game.

Players are visibly encased inside translucent, resin-like geometric shells. The player's normal Roblox avatar remains visible inside the shell.

The central fantasy is:

**Evolve from a clunky cube into a perfect rolling sphere while surviving as far as possible down chaotic randomized courses.**

All progression tiers play together on the same shared map.

The game should remain simple, readable, replayable, physics-focused, socially chaotic, and streamlined in scope.

## 2. Current Core Gameplay Loop
**Spawn at the top → descend the randomized map → survive impacts → shell chips and fractures → handling worsens as damage accumulates → continue as far as possible → shell shatters → player dies → receive currency proportional to distance → repeat.**

The primary objective is no longer simply to reach a designated finish area.

The primary objective is:

**Reach as far down the course as possible without your shell shattering.**

Distance / downward progress is now the core run-performance metric.

## 3. Breakable Shell System
The geometric shell surrounding each player is physically breakable.

Heavy crashes and impacts can chip edges, remove chunks, create fractures, make the shell increasingly jagged, and eventually shatter the shell completely.

A cube crashing hard into a corner can chip away part of an edge. Repeated hard impacts progressively deform and weaken the shell.

When the shell shatters:
- the player dies
- the current run ends

Damage must be visually readable and should not rely only on a hidden health bar.

Approved damage progression concept:

**Intact → Chipped → Fractured → Heavily Damaged → Shattered**

Exact thresholds remain open for prototyping.

## 4. Damage Must Affect Handling
Shell damage is not purely cosmetic.

As the shell becomes chipped, fractured, asymmetric, and jagged, its rolling and handling characteristics should become progressively worse.

This may affect rolling smoothness, balance, stability, trajectory, snagging, bounce behavior, and momentum retention.

The exact implementation is a prototyping decision.

Locked design principle:

**Damage should physically make the shell harder to control and survive with.**

## 5. Subdivision Progression
There are exactly 5 core subdivision tiers.

### Tier 1 — Cube
- clunky
- gets caught more easily
- relies heavily on Jolt
- least efficient rolling form

### Tier 2 — Beveled Cube
- reduced snagging
- slightly smoother rolling

### Tier 3 — Rounded Polyhedron
- more consistent rolling
- better flow

### Tier 4 — Near-Sphere
- improved momentum retention
- better stability at speed

### Tier 5 — Perfect Sphere
- maximum intended rolling smoothness
- most fluid movement

Every subdivision tier must provide meaningful mechanical improvement.

Progression must not rely only on increasing polygon count.

Raw geometric subdivision has diminishing gameplay returns, so each tier should use deliberately tuned physics and mechanics.

Possible tunable properties include rolling efficiency, momentum retention, stability, bounce behavior, resistance to snagging, steering/control, Jolt dependence, knockback response, and—if later approved for tier balancing—durability or damage behavior.

Exact values are open for prototyping.

Do not change the number of tiers without explicit approval.

## 6. Progression Cannot Be Purchased
Permanent gameplay progression cannot be bought.

Robux cannot purchase Wins, subdivision tiers, permanent subdivision progress, permanent gameplay-stat progression, progression skips, or progression multipliers.

If a player reaches Tier 5, that progression must be earned through gameplay.

Important: the previous finish-line-based Win system has been reopened by the new survival/distance-based loop.

Do not implement the old rule of **“reach bottom = +1 Win”** unless the user explicitly re-approves or replaces it.

The exact future relationship between Wins, subdivision progression, survival distance, and map completion is currently unresolved and must be re-reviewed before implementation.

## 7. Jolt Mechanic
Jolt is a permanent core mechanic.

Purpose:
- help players recover when stuck
- regain traction
- escape awkward positions
- recover from poor orientation

Jolt should create a useful physical impulse, likely upward.

Jolt exists at every subdivision tier.

Exact cooldown, force, animation, and visual feedback remain open balancing variables.

Do not remove Jolt.

## 8. Shared Map Structure
All players use the same map.

Players begin in a lobby at the top of the map and are released together.

The map contains:

**10 vertically stacked randomized modules.**

The entire stack regenerates approximately every 10 minutes.

The structural inspiration is:

**Tower of Hell flipped upside down.**

This refers to the vertically stacked obby format, not copying Tower of Hell's exact content.

The game is focused on descending, falling, rolling, bouncing, navigating, and surviving physics hazards.

## 9. Modular Map Generation
Every map module should follow a standardized connection / footprint system so modules stack coherently.

Each module should be independently playable, connect cleanly to modules above and below, support the shared descent format, and work in multiple stack positions.

Modules may repeat during the proof-of-concept.

The initial proof-of-concept uses 3 module concepts:

### Ramp Maze
A branching downhill maze with multiple paths, route choices, dead ends, routes that fall into the void, and safer or riskier routes.

Primary focus: **navigation and steering**

### Bounce Yard
A trampoline / bounce-focused level where players must bounce across or through obstacles to survive and descend.

Primary focus: **timing, recovery, bouncing, Jolt**

### Pinball Pit
A chaotic pinball-style module that may include bumpers, angled walls, ricochets, paddles, funnels, and chaotic physics interactions.

Primary focus: **chaotic movement and social physics**

The proof-of-concept should first prove that modules stack correctly, randomized order works, 10-level generation works, repeated modules do not break the map, transitions remain playable, and the design feels coherent.

Do not build a large module library before the generator is proven.

## 10. Distance-Based Currency
Currency is now awarded proportional to distance / downward progress achieved during a run.

This is the primary approved reward change introduced by the survival-loop revision.

The exact formula is not yet locked.

Possible future implementation variables include studs descended, module depth reached, checkpoints crossed, or deepest point reached.

These are not yet approved as final formulas.

Locked design rule:

**Farther survival = more currency.**

## 11. Previous Track Currency System — Reopened
The earlier design approved currency spawning directly on the track, fixed authored pickup locations, respawning pickups, and larger currency bundles on risky shortcuts.

Because the new survival loop now awards currency based on distance, the old track-pickup system may become secondary, optional, redundant, or reworked.

This system is reopened for explicit review.

Do not assume that respawning track currency remains mandatory.

Do not delete the concept either.

Wait for explicit user approval on how track pickups should coexist with distance-based currency.

## 12. Player Interaction
Players occupy the same physical course and may interfere with each other.

A Punch / knockback-style interaction is approved as part of the game's social physics concept.

Players may inconvenience one another.

However, interactions should not permanently prevent another player from playing.

Detailed Punch mechanics, cooldowns, knockback values, immunity rules, and anti-grief protections remain open.

Do not introduce paid mechanical advantages to these systems.

## 13. Cosmetic System
Cosmetics are an important customization and monetization system.

The translucent shell surrounding the avatar is a major cosmetic canvas.

Approved cosmetic categories may include:
- shape colors
- shape materials
- auras
- trails
- inner-character effects
- titles
- nameplates
- Jolt visual effects
- Punch visual effects
- collision effects
- finish effects
- spawn effects
- shape patterns
- core effects

Cosmetics may have variants.

Cosmetics should have rarity classifications.

Possible rarity structure:
- Common
- Uncommon
- Rare
- Epic
- Legendary
- Mythic

Rarity represents collectibility and presentation.

Rarity must not provide gameplay strength.

## 14. Cosmetic Store
The game contains an in-game cosmetic store.

Selected cosmetics may be purchasable with earned in-game currency, Robux, or either depending on the item.

Direct Robux purchases must not grant permanent gameplay progression, subdivision advantages, or competitive mechanical advantages.

Exact prices remain open.

## 15. Cosmetic Crates
Cosmetic crates are approved.

Crates may only be purchased with:

**earned in-game currency**

Crates must not be purchased with Robux.

Crates use a rolling / reel-style opening UI.

The UI should visually present possible rewards and rarity / odds in understandable terms such as:
- 1 in 5
- 1 in 25
- 1 in 200
- 1 in 1000

Displayed rarity information must correspond to the actual reward probabilities.

Crate rewards must be server-authoritative.

The client must not be trusted to choose its own reward.

Exact crate prices, drop tables, odds, duplicate handling, pity systems, and animations remain open unless later approved.

Do not add Robux-funded random crates.

## 16. Monetization Law
The core monetization law is:

**Progression cannot be bought.**

Mechanically advantaged Gamepasses have been explicitly dismissed.

Do not implement paid features such as shorter Jolt cooldown, shorter Punch cooldown, stronger Punch, better rolling physics, more progression rewards, progression multipliers, subdivision boosts, or progression skips.

Robux monetization should focus on direct cosmetic purchases, cosmetic expression, and temporary server-wide chaos events.

## 17. Chaos Developer Products
Temporary server-wide chaos effects may be sold for Robux.

These are repeatable monetization products.

They must not grant permanent progression.

Approved / discussed concepts include:
- Low Gravity
- Super Bounce
- Shockwave
- Launch Everyone
- Marble Storm
- Kill Everyone

Not every example must automatically be implemented.

Implement only when specifically approved for development.

### Kill Everyone Rule
"Kill Everyone" is approved.

However:

**Kill Everyone may only activate once per generated map cycle.**

After one successful activation, nobody may activate it again until the next map is generated.

This applies regardless of purchaser.

Exact Robux pricing remains open.

## 18. Development Environment
Primary development environment:

**Roblox Studio**

Development is intended to be performed with Codex or another coding AI connected to Roblox Studio through MCP.

The project is intentionally relatively small.

Code should remain streamlined, readable, efficient, practical, easy to debug, and appropriately modular.

Avoid unnecessary frameworks, excessive abstraction, speculative architecture, premature optimization, unnecessary dependencies, duplicated systems, and scope creep.

## 19. Development Philosophy
Build the smallest correct implementation that satisfies the approved design.

Prefer simple modules with clear responsibilities.

Do not create elaborate architecture for hypothetical future features.

Do not rewrite working systems solely because a more sophisticated pattern exists.

Only introduce abstraction when it clearly reduces duplication, improves maintainability, or helps this specific project.

All meaningful code should map back to a Vault requirement.

## 20. Approved Development Order
The previously approved high-level development order was:

1. Physics
2. Map Generation
3. Round Loop
4. Progression
5. Currency
6. Player Interaction
7. Cosmetics
8. Crates
9. Monetization
10. Polish

Because the core gameplay loop has changed to survival / damage / distance, the earliest development priorities should now emphasize:
- rolling physics
- shell damage
- fracture / chipping feedback
- damage-driven handling degradation
- death on shatter
- distance tracking

Any broader reordering should be explicitly approved if it changes the overall workflow.

Development should occur through playable vertical slices.

Every stage should leave the game in a testable state.

## 21. First Development Objective
The original first development objective remains valid:

**Make the player become a cube and make rolling downhill feel good.**

It now expands to include the survival mechanic.

The first meaningful prototype should validate:
- encased avatar presentation
- cube physics
- player movement/control
- camera behavior
- Jolt
- downhill interaction
- impact detection
- chipping/fracture behavior
- damage-driven handling degradation
- shell shattering
- death
- distance tracking

Do not jump ahead to cosmetics, crates, monetization, or large-scale map content before the core survival physics experience is proven.

## 22. Server Authority / Security Principle
Important gameplay outcomes should be validated by the server.

Examples include:
- distance rewards
- currency awards
- progression awards
- crate rewards
- purchases
- subdivision progression
- chaos-event activation limits
- death / shatter state if exploitable
- major damage validation where practical

Do not trust client-supplied values for progression or rewards.

Keep the implementation proportionate to the size of the project.

Do not overbuild security infrastructure.

## 23. Open / Unresolved Areas
The following are intentionally not fully locked:
- exact physics values for each subdivision tier
- exact durability model
- exact damage thresholds
- exact fracture thresholds
- exact shell-deformation implementation
- exact Jolt force and cooldown
- exact Punch behavior
- exact anti-griefing mechanics
- exact subdivision reward structure after the survival-loop revision
- exact role of Wins after the survival-loop revision
- exact relationship between distance and subdivision progression
- exact distance-to-currency formula
- whether track currency pickups remain in addition to distance rewards
- exact cosmetic prices
- exact Robux prices
- exact crate odds
- exact crate prices
- exact UI design
- exact save-data schema
- exact persistence behavior
- exact round timing details
- exact audio / visual polish

Do not invent permanent answers to these areas without approval.

Temporary prototype values may be used when necessary, but must be clearly identified as temporary.

## 24. Mandatory Vault Check
Before implementing any meaningful feature or structural code change, ask:

**Which Project Vault requirement authorizes this change?**

If there is a clear answer:
Proceed.

If there is no clear answer:
Do not implement it.

Tell the user:
- what idea occurred
- that it is not currently in the Vault
- why it may improve the game

Then request explicit approval.

## 25. No Silent Improvements
No AI or developer may silently improve, extend, redesign, or reinterpret the game beyond this Vault.

This includes ideas that appear obviously beneficial.

The user controls the product vision.

The AI / developer controls implementation within the approved product vision.

## 26. Change Control
When the user explicitly approves a new design decision:

1. Update the Vault.
2. Mark superseded rules clearly.
3. Preserve the newest approved direction as authoritative.
4. Do not remove unrelated approved systems unless explicitly instructed.
5. Keep the implementation synchronized with the latest Vault.

## 27. Project Identity
Project:

**Roblox Marble Game**

Current stage:

**Phase 2 — Development Preparation**

Current Vault version:

**v2.0**

Primary gameplay revision in v2.0:

**Breakable shell survival + damage-driven handling degradation + distance-based currency rewards**

The Vault is the project source of truth.
