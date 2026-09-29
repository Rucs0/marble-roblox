---
description: Summarize this session for a cache-safe handoff, printed in chat for manual copy-paste
allowed-tools:
---

Prepare a session handoff instead of relying on `/compact`: `/compact` breaks the prompt cache by rewriting the conversation prefix, full recache at full price. Mechanism: print the summary in the response, Zarar copies it, runs `/clear`, and pastes it back in as the first message of the next session himself.

## Steps

1. Write a plain-text summary covering:
   - Decisions made this session, what we are solving and why, what's done and what's in progress
   - Files created or edited, with paths
   - Open items, unresolved questions, what's been tried and failed and specifics on why that failed
   - The exact next action to take, concrete enough to act on cold
2. Print the summary directly in the response, inside a single code block so it copies cleanly in one action.
3. After the block, tell the user in one short line: copy that, run `/clear`, then paste it back in as the first message of the new session. Do not run `/clear` yourself; only the user can do that.
