# 2. Memory and context

If the agent has no persistent memory, every session becomes a "new intern."
Quality fluctuates, style breaks apart, decisions don't accumulate.

## What is the agent's working memory

Working memory is an **exocortex**: external memory outside the context window, but under the agent's control. It's not "the entire chat history" but a compressed layer:
- project principles,
- decisions made,
- constraints,
- current priorities,
- validated patterns.

## What to store

Worth storing:
- facts that are repeatedly needed across tasks;
- rules that drive decisions;
- agreements on tone/style/ethics;
- experiment results (what worked, what didn't).

Not worth storing:
- throwaway details with no reuse value;
- emotional "verdicts" without context or confidence assessment;
- duplicates.

## Format

Good memory is:
- short,
- structured,
- updated after significant shifts,
- read by the agent at the start of a new session.

## Implementation

Concrete tools for working with memory: `read_agent_notes` (read notes at session start) and `write_agent_notes` (record takeaways after significant steps). This turns memory from an abstraction into a real mechanism the agent invokes itself.

## Minimal cycle

1. Completed a step.
2. Verified the result.
3. Added only the transferable takeaway to memory (`write_agent_notes`).
4. In the new session, read memory (`read_agent_notes`) and continued.

## Success criterion

After summarization or a new chat the agent quickly returns to the same quality level, rather than "warming up from scratch."
