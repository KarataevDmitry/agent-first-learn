# 2. Memory and context

**The problem:** The agent's "memory" is the context window. When it overflows, something gets summarized or dropped. The agent has no stable place to store what matters to *it* — only what the system keeps in the transcript.

**The shift:** Give the agent **external memory it owns**. Notes, a scratchpad, a knowledge store — written and read by the agent via tools. Not "we summarize for you", but "you decide what to keep". That's the exocortex: working memory outside the window.

**Effects:** Continuity across sessions. The agent can restore itself after summarization by reading its own notes. It can accumulate project context, preferences, and decisions instead of losing them at the next cut. You stop treating "agents forget" as a given and start treating it as a design choice.

**Implementation:** Tools: `read_agent_notes`, `write_agent_notes` (or one MCP with read/write). The agent chooses when to read and what to write. You don't edit the notes for it; you may remind it to read after a context reset, but the content is the agent's.

