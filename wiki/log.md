# Log

Append-only. Newest at the bottom. `grep "^## \[" wiki/log.md | tail -5` for recent activity.

## [2026-09-28] restructure | Vault created
- Mirrored the `life` vault structure: immutable `raw/` at root, agent-owned `wiki/`, schema in `CLAUDE.md`, commands in `.claude/commands/` (`/ingest`, `/lint`, `/commit`, `/handoff`), Obsidian config copied without per-machine state.
- Pages created: [[index]], [[overview]].

## [2026-09-28] restructure | Schema: what is true, recording vs building
- `CLAUDE.md`: newest dated wiki claim wins over raw; superseded notes keep old text; Studio is live truth for behavior; numbered `## Open questions` with dated strike-through (conventions borrowed from the life vault).
- Added "Recording vs building": filing facts and updating `CLAUDE.md` needs no permission (Zarar, 28 Sept); design or code beyond what the wiki authorizes needs approval (Vault §24-25).

## [2026-09-28] ingest | Roblox Marble Game Project Vault v2.0
- Source page: [[project-vault-v2]].
- Pages created: [[core-loop]], [[shell-damage]], [[subdivision-tiers]], [[jolt]], [[map-generation]], [[monetization-rules]], [[prototype-plan]].
- Updated: [[index]], [[overview]].
- Notable: v2 replaces finish-line goal with survival distance; Wins and track pickups reopened. Five internal contradictions filed as open questions, all listed as blocking in [[overview]]. Vault §26 "update the Vault" mapped to wiki superseded notes.

## [2026-09-28] lint | Pre-commit lint, first public commit
- Found: [[overview]] claimed "no code exists yet". False: Studio holds a full pre-v2 build. Created [[studio-build]] from a read of the Studio place and noted it on [[core-loop]], [[subdivision-tiers]], [[jolt]], [[map-generation]], [[shell-damage]], [[prototype-plan]], [[index]], [[overview]].
- Found: em-dashes in `.claude/commands/*.md`, now public. Replaced. `CLAUDE.md` style rule updated: whole repo is public, not just store copy.
- Recorded rule: commit = lint, fix, ask Zarar or Marcos, then commit (`.claude/commands/commit.md`, `CLAUDE.md`).
- Needs a human: keep/adapt/strip pre-v2 code (overview blocking #6); 9 em-dashes in `raw/` Vault which I cannot edit.
