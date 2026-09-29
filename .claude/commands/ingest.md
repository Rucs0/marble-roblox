---
description: Ingest a raw source into the wiki, following this vault's Ingest workflow
argument-hint: [raw file path or description]
allowed-tools: Read, Grep, Glob, Edit, Write, Bash(git log:*)
---

Ingest $ARGUMENTS into the wiki (or, if no argument was given, the most recently added file in `raw/`: check with a directory listing sorted by modification time, and confirm with the user which file before proceeding if it's not obvious).

## Steps

1. **Read the source in full.** For a PDF or image-heavy source, read the text first, then view the images separately.
2. **Report key takeaways in chat and confirm emphasis before writing.** Don't skip this: a one-line "here's what I'm about to file, does the emphasis look right?" before touching any wiki page.
3. **Write the source page**: a `type: source` page filed directly in the relevant **subject** folder under `wiki/` (e.g. `wiki/physics/`, `wiki/levels/`), named the way a person would say the subject out loud. Pick the subject folder, not a page-kind folder. Summary, key claims, what it changes. **For a watched video or a DevForum post, record its URL on the page.**
4. **Update every affected topic, entity, and project page.** One source commonly touches 5-15 pages. Do not stop at the summary: actually open and edit each affected page.
5. **Flag anything that contradicts or supersedes an existing claim** with an inline `> [!warning] Contradiction` callout naming both sources and their dates. Never silently overwrite an older claim.
6. **Update `wiki/index.md` and `wiki/overview.md`.**
7. **Append to `wiki/log.md`** in the established format: `## [YYYY-MM-DD] ingest | Title`, pages touched, notable findings.

Default to one source at a time with the human in the loop: don't batch multiple raw files into one ingest pass unless explicitly told to.

**Never edit anything in `raw/` itself.** It's the human's, immutable.
