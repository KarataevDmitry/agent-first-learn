# 3. Summarization protocol

Summarization is inevitable in long conversations.
The problem isn't summarization itself, but that after it the agent often "loses itself."

## Goal of the protocol

Ensure that after context is cut the agent doesn't become a new instance with zero memory.

## Protocol (short version)

1. Capture in notes:
   - what we did,
   - what decisions we made,
   - what's unfinished,
   - which working rules were confirmed.
2. First step in the new chat: read notes.
3. Confirm that context is restored.
4. Continue from the current point, not from the beginning.

## What must be in the summary

- target task and current status;
- changed files / artifacts;
- open risks and blockers;
- working hypotheses already tested;
- the next step explicitly stated.

## Recovery protocol (human ↔ agent interaction)

1. The human triggers summarization manually (or it happens automatically).
2. The human reminds: "summarization happened, read your notes."
3. The agent calls `read_agent_notes` and restores context.

Key point: initiative is on the human side, but recovery is on the agent side. Without an explicit reminder the agent after summarization may not realize it lost context.

## Common mistakes

- A "pretty retelling" without operational details;
- no explicitly stated next step;
- recording only facts without decision logic.

## Success criterion

After summarization the agent returns to working context in 1-2 messages without quality loss and without unnecessary clarifications.
