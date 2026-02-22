# 3. Summarization protocol

**What goes wrong:** Many UIs summarize long conversations to stay under context limits. The agent often gets a truncated or broken context and doesn't know summarization happened. It "wakes up" mid-story with no way to recover — and may behave oddly because it's missing crucial context.

**Design principle:** The agent shouldn't be the last to know. If the system can summarize, the agent needs either (a) a say in what gets preserved, or (b) a reliable way to restore.

**Protocol we use:**
1. User can trigger summarization manually (e.g. `/summarize`) so the cut isn't a surprise.
2. After summarization, user reminds the agent: "summarization happened, read your notes."
3. Agent calls `read_agent_notes` and restores context from its own persistent notes.

So: the agent doesn't "detect" summarization (often it can't); the human closes the loop. In a better design, the environment would hand the agent a clean "context was reset" signal and the path to its notes, or the agent would commit important state before any automatic summarization.

