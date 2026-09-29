---
description: Lint the wiki for contradictions, stale claims, orphan pages, and stale decisions
allowed-tools: Read, Grep, Glob, Bash(date:*)
---

Lint the wiki for contradictions, stale claims, orphan pages, and stale decisions. On its own this is a read-only report: surface what needs attention, do not edit. When run as step 1 of `/commit`, the fixes happen in `/commit` step 2.

## Check for, and report as a ranked list

1. **Contradictions between pages.** Two pages making incompatible claims about the same fact, without either flagging it.
2. **Claims superseded by newer sources.** A page still stating something a more recent ingest or conversation already corrected.
3. **Orphan pages with no inbound links.** Use `wiki/index.md` as the page list and grep for `[[wikilinks]]` across the vault to check inbound references. `raw/` is exempt: everything in `wiki/` is not, per `CLAUDE.md`. A new page with zero inbound links is unfinished ingest, not an acceptable end state.
4. **Concepts referenced repeatedly but with no page of their own.** A term or idea that keeps coming up across multiple pages without ever getting its own topic page.
5. **Open decisions in projects that have gone stale.** A page's "Open" section listing a question that's actually been answered elsewhere and never closed out, or one that's sat unresolved long enough to flag.


## Output

Rank by how much it matters, not by which check found it. **End with concrete suggestions**: specific questions worth investigating, specific sources worth finding, specific pages worth writing. Don't just list problems, name the next action for each one that has an obvious one.
