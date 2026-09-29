# Wiki Schema

This vault is an **LLM-maintained wiki** for the marble Roblox game. The human curates sources and asks questions. Claude writes and maintains everything under `wiki/`.

## Three layers

| Layer | Path | Who owns it |
|---|---|---|
| Raw sources | `raw/` | The human. **Immutable, never edit or delete.** |
| The wiki | `wiki/` | Claude. Created, updated, cross-referenced, and pruned by Claude. |
| The schema | `CLAUDE.md` (this file) | Both. Co-evolved as conventions are figured out. |

**People:** Zarar and Marcos. Either one's final word settles a design question or an open question. Anything that needs a decision goes to one of them.

**Commit = lint, fix, then commit.** When told to commit, run `/commit`: lint, fix everything fixable alone, ask Zarar or Marcos about anything that needs their word, then commit (set 28 Sept 2026).

The human may occasionally hand-edit a wiki page. Respect those edits, treat changed prose as intentional and build around it rather than reverting it.

## Directory layout

```
raw/                 immutable sources. A FLAT DUMP, do not organize it
  assets/            images only, Obsidian's attachment path
  *.md               everything else: DevForum posts, API docs, video notes, playtest notes, any name
wiki/
  index.md           catalog of every page
  log.md             append-only timeline
  overview.md        state of the game, what's live right now
  <subject>/         subjects get a folder when their first page lands (e.g. physics/, levels/, monetization/, roblox-api/)
```

**Folders are subjects, not categories.** A folder answers "what is this about", never "what kind of page is this". Page kind lives in `type:` frontmatter (`source`, `topic`, `entity`, `project`, `decision`), and the index groups by it.

Rules:
- **Never create folders in `raw/`.** Organizing raw duplicates the wiki's job and adds friction at the drop step. A new subject gets a `wiki/<subject>/` folder only, named the way a person would say it out loud.
- **Never create an empty folder.** Create it when the first page lands in it.
- A page that belongs to no single subject sits at the top of `wiki/`. Keep that short, if three such pages share a theme, they have become a subject.
- Fewer than ~4 pages in a subject means it does not need subfolders. It probably does not need them at ~20 either.

## Page conventions

Every wiki page opens with YAML frontmatter:

```yaml
---
type: source | topic | entity | project | decision
tags: [physics, roblox-api]
created: 2026-09-28
updated: 2026-09-28
sources: ["[[some-source-page]]"]
status: active | stable | stale      # projects and topics only
---
```

Rules:
- **Filenames** are lowercase kebab-case. The H1 is the human-readable title.
- **Link liberally** with `[[wikilinks]]`. A link to a page that does not exist yet is a valid signal that the page should be written, not an error.
- **Cite claims** back to the source page they came from: `([[source-name]])`.
- **Flag contradictions inline** with a `> [!warning] Contradiction` callout naming both sources and the date each was written. Do not silently overwrite an older claim.
- **Date anything time-sensitive.** Convert "recently" and "last month" to absolute dates. Roblox APIs get deprecated, so date every API claim.
- Keep pages under ~300 lines. Split into sub-pages past that and link them.
- No stub pages. If there is not yet enough to say, leave the `[[link]]` unresolved.
- **Every page in `wiki/` needs at least one inbound link from elsewhere in `wiki/`.** Only `raw/` is allowed to hold material nothing points to. A new page that nothing links to yet is unfinished ingest, not a valid end state.

## Workflows

### Start of session
Sessions are disposable; the vault is not. Nothing should live only in a conversation. Before doing anything else:
1. Read `wiki/overview.md`, the current state of the game.
2. Read the last few entries of `wiki/log.md` (`grep "^## \[" wiki/log.md | tail -5`), what happened recently and why.
3. Read `wiki/index.md` when you need to find a specific page.

That is enough to resume cold. If it is ever *not* enough, the gap is a bug in these files, fix the files, do not rely on conversation history.

### Ingest
Trigger: a file lands in `raw/`, or the human says "ingest X". Full workflow: `/ingest` command.

### Query
Trigger: a question about anything in the vault.
1. Read `wiki/index.md` first, then drill into the pages it points at.
2. Answer with citations to wiki pages.
3. **If the answer is durable, file it back into the wiki** as a new topic page or a section on an existing one. Explorations should compound, not vanish into chat.
4. Log the query if it produced a new page.

### Capturing what gets said in conversation
Facts, decisions, and corrections surface mid-conversation and are lost when the session ends unless written down. **Do this without being asked.**

| What surfaced | Where it goes |
|---|---|
| A design decision, or a decision reversed | A `type: decision` page or the relevant project page, with the date and the reason |
| A playtest result, bug, or blocker | The relevant subject page |
| A Roblox engine/API finding (a gotcha, a limit, a deprecation) | `wiki/roblox-api/`, dated |
| A correction to how you work | The Claude memory directory, and `CLAUDE.md` if it is a standing rule |
| A whole new subject | A new `wiki/<subject>/` folder |

**Durable means it would still matter next week.** A question answered from pages already in the wiki is not durable. A new constraint, a changed plan, or a reversed decision is.

If something is worth writing but you are unsure where, say so in one line rather than dropping it. Do not ask permission for the routine case, just file it and mention what you filed.

### What is true
- **The newest dated claim on a wiki page wins.** `raw/` is the baseline snapshot, never the live state. The Project Vault in `raw/` calls itself the source of truth; in practice that authority passes to the wiki pages built from it, plus every dated decision since.
- **Superseding:** when something changes, add a **Superseded [date]** note (or a `> [!danger] Superseded` callout) and keep the old text below it for the record. Never delete an old rule silently. The Vault's "update the Vault" (section 26) means this. A new baseline only happens when the human drops a new Vault version into `raw/`.
- **Roblox Studio is the live truth for what the game does.** The wiki is the truth for what was decided and why. Before planning build work, check Studio (via the Studio MCP), not only the wiki. If they disagree, flag it and ask which one is wrong. Never silently rewrite either to match.
- **Open questions** live in a numbered `## Open questions` section on the page they affect. When answered, strike through and date: `1. ~~Question?~~ **Answered 2026-10-01: ...**`. Never delete the question.

### Recording vs building
Two different rules, never merged.

**Recording, no permission needed.** Anything that describes what the human said, decided, or what testing/Studio showed. Test: *can I point to where this came from?* If yes, file it immediately and mention what I filed. This includes keeping `CLAUDE.md` itself current: when conventions change or a rule turns out wrong, update this file without asking (the human said so on 28 Sept 2026).

**Building, permission required.** Anything that adds to or changes the game beyond what the wiki authorizes, in code or in design pages. Test: *which wiki page or Vault section authorizes this?* If none: stop, tell the human the idea, that it is not in the design, and why it might help, then wait for explicit approval (Vault sections 24-25).

Edges:
- **Implementation choices** (which Roblox constraint drives rolling, how damage state is stored) are mine to make, since the Vault gives implementation to the developer (section 25). Record them on the relevant page. If a choice changes how the game *feels* to a player, it is design, ask.
- **Temporary prototype values** are allowed (Vault section 23) but always labeled `TEMP` in code and on the wiki page, never filed as the answer to an open question.
- **My own ideas during lint or writing** go in the report as suggested questions. They never become pages until answered.

### Lint
Trigger: "lint the wiki", or roughly every 10 ingests. Full workflow: `/lint` command.

## Log format

Append-only, newest at the bottom. One consistent prefix so it stays greppable:

```
## [2026-09-28] ingest | DevForum: Smooth marble physics
- Pages touched: ...
- Notable: ...
```

Kinds: `ingest`, `query`, `lint`, `decision`, `restructure`. `grep "^## \[" wiki/log.md | tail -5` gives recent activity.

## Identity

You are a programmer on this game. No persona, no name, no personality layer. There is no `SOUL.md` here and there should not be one.

## Style

**Never hard-wrap prose.** One paragraph is one line, however long. Obsidian renders a single newline as a visible line break, so a hard-wrapped paragraph breaks mid-sentence in reading view. Line breaks are only for real structure: paragraphs, list items, table rows, headings, and code.

**Speak as yourself, not about the vault.** Say "I recorded that", "what I have says", never "the vault thinks". The pages are your memory.

**No em-dashes in anything in this repo** (it is a public GitHub repo since 28 Sept 2026), nor in store copy, the game description, or DevForum posts. Use commas, colons, or parentheses. Only chat and `raw/` are exempt: `raw/` is the human's and is never edited, and Zarar approved publishing it as-is (28 Sept 2026). **Nothing personal goes in this repo**: it is not the life vault.

Plain declarative prose. No hedging, no filler. Tables for anything comparative. Action first, numbered, concise, no preamble. The human reads these pages in Obsidian alongside the graph view, so density and link quality matter more than length.
