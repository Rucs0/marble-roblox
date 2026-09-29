---
description: Lint the wiki, fix what's fixable, then commit pending changes split by relevancy
allowed-tools: Bash(git status:*), Bash(git diff:*), Bash(git add:*), Bash(git commit:*), Bash(git log:*), Bash(git push:*), Read, Grep, Glob, Edit
---

Commit the pending changes in this repo (`marble-roblox`). **"Commit" always means lint, fix, then commit.** Zarar set this rule on 28 Sept 2026.

## Before committing

1. **Run `/lint`** across the whole wiki and `CLAUDE.md`.
2. **Fix every error you can fix alone** (anything that counts as recording under `CLAUDE.md` "Recording vs building"). When a fact changed, grep every page that mentions the old state and fix all of them, bumping `updated:` on each. Log the lint in `wiki/log.md`.
3. **If an error needs a final word from Zarar or Marcos** (a design call, an open question, anything that counts as building, or anything touching `raw/`), **stop and ask before committing.** One short list of questions, each with a recommended answer. Commit everything else only after they answer, or if they say to commit anyway.
4. **The repo is public.** Before staging, check the diff for em-dashes (outside `raw/`), secrets, and anything personal that should not be on GitHub. Fix or ask.

## Commit steps

1. Run `git status` (never `-uall`) and `git diff` to see everything pending, staged and unstaged. Run `git log --format="%H %s%n%b%n---" -5` to refresh on this repo's commit message style before writing any.
2. **Group the changed files by relevancy, not by session.** Two files belong in the same commit only if they share one real reason for changing: one decision, one source ingested, one correction, one topic. Files that happen to have been edited in the same sitting but for unrelated reasons go in separate commits, even if that means five commits instead of one. Read the actual diffs to judge this, don't guess from filenames alone.
   - `wiki/log.md` and `wiki/index.md` routinely accumulate edits from several unrelated changes in one sitting. If a single commit's topic touches only part of either file, use `git add -p` to stage just that hunk rather than pulling in unrelated entries. If splitting the hunks isn't worth the overhead for a given case (e.g. two closely related log entries), bundling is fine: use judgment, don't force atomicity past the point it's useful.
   - `raw/` files are the human's own edits (this repo never edits `raw/` itself): group them with whatever wiki updates they drove, same as any other source.
3. For each group, in a sensible order (foundational changes before things that depend on them):
   - Stage exactly those files (or hunks) by name. Never `git add -A` for this: that's how unrelated changes get bundled back together.
   - Write a commit message: an imperative, specific title line, a blank line, then a prose paragraph (not bullets) explaining what changed and why it matters, in this repo's established voice, direct and specific, dates and numbers over vague language. Look at recent commits for the exact tone.
   - **Every commit must end with the trailer** specified in your system prompt's git-commit instructions (`Co-Authored-By:` and `Claude-Session:` lines). Do not skip this even under time pressure.
   - Commit with a heredoc (`git commit -m "$(cat <<'EOF' ... EOF)"`), never `--no-verify`, never `--amend` unless explicitly asked.
4. After all groups are committed, run `git status --short` to confirm the working tree is clean (or report what's left uncommitted and why, e.g. something that looked like a secret or was ambiguous).
5. **Push to `origin` only when Zarar asks.** Otherwise this command only commits. List the commits created, oldest first, with their one-line summaries.

If something in the diff looks like it might be a secret (API key, credential, token) even in an innocuous-looking file, stop and flag it instead of committing it.
