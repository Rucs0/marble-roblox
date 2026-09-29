---
type: topic
tags: [monetization, cosmetics, crates]
created: 2026-09-28
updated: 2026-09-28
sources: ["[[project-vault-v2]]"]
status: active
---

# Monetization Rules

**The law: progression cannot be bought.** ([[project-vault-v2]] §16)

Robux goes to three things only: direct cosmetic purchases, cosmetic expression, and temporary server-wide chaos events.

## Banned outright
Mechanically advantaged Gamepasses are dismissed. Never build paid: shorter [[jolt]] cooldown, shorter/stronger Punch, better rolling physics, more progression rewards, multipliers, subdivision boosts, progression skips. Robux cannot buy Wins or [[subdivision-tiers]]. (§6, §16)

## Cosmetics (§13)
The translucent shell is the main canvas. Approved categories: shape colors, shape materials, shape patterns, auras, trails, inner-character effects, core effects, titles, nameplates, Jolt / Punch / collision / finish / spawn effects. Variants allowed.

Rarity: Common, Uncommon, Rare, Epic, Legendary, Mythic. **Rarity is presentation only, never gameplay strength.**

## Store (§14)
In-game store. Items sold for earned currency, Robux, or either, per item. Robux never buys progression or competitive advantage.

## Crates (§15)
- **Earned currency only. Never Robux.** No Robux-funded random crates.
- Reel-style opening UI showing rewards and odds as "1 in 5", "1 in 25", "1 in 200", "1 in 1000".
- **Displayed odds must match the real odds.**
- **Server picks the reward.** Client never chooses.

## Chaos developer products (§17)
Temporary, repeatable, server-wide, Robux. No permanent progression. Discussed: Low Gravity, Super Bounce, Shockwave, Launch Everyone, Marble Storm, Kill Everyone. **Build only when specifically approved**, each one.

**Kill Everyone:** once per generated map cycle ([[map-generation]]), regardless of who buys it.

Chaos activation limits and purchases are server-validated (§22).

## Build order
Cosmetics, crates, and monetization come after core survival physics is proven ([[prototype-plan]]).

## Open questions
1. **Kill Everyone vs "no paid advantage".** A buyer who times it ends every other run, costing them distance currency. Same for Launch Everyone. Does the buyer die too? Do victims still get paid for distance reached?
2. **"Finish effects" with no finish.** v2 removed the finish line ([[core-loop]]). Drop the category, or keep it for reaching the bottom module?
3. Cosmetic prices.
4. Robux prices.
5. Crate prices, drop tables, odds, duplicates, pity, animations.
