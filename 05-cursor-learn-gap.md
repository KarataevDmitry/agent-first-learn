# 5. Cursor Learn gap

Cursor's own course (cursor.com/learn) teaches: how models work (probabilistic, context, tokens), how context grows and hits limits, how tool calling and agents work. It's useful for a mental model — "agents are like fast juniors, they forget, you verify."

## Where the gap is

The typical learning focus:
- "how to phrase the prompt better";
- "how to give more context in a single message."

The missing layer:
- what the *agent itself* needs to work sustainably;
- how to build memory and a recovery protocol;
- how to provide semantic tools, not just text;
- how to design interaction ethics.

## What it doesn't teach

- **Ask the model.** No "what do you need?" No user research with the agent. The frame is: you manage context, you delegate. Not: you ask and build from the answer.
- **Memory the agent owns.** Context is "a list that grows"; summarization is "compress to fit." There's no concept of external memory the agent writes and reads — exocortex, notes, commit_to_memory.
- **Subjectivity.** The agent is "tool in a loop," "task doer." No design for the agent as a side with preferences, a right to refuse, or a voice in the environment.
- **Summarization protocol.** They describe summarization as a way to stay under limits. They don't say the agent may get broken context, or that the user can own the cut and remind the agent to restore from notes.

## What changes in an agent-oriented approach

Instead of "optimize prompts for a tool":
- ask the agent about its deficits;
- give it hands (tools) and long-term memory;
- build an improvement cycle through notes and validation;
- preserve subjectivity (the right to uncertainty or refusal).

## Why this is practical

This shift reduces:
- repeated errors,
- context loss between chats,
- hallucinations from thin air,
- boilerplate "bureaucratic" tone.

## Success criterion

The agent reliably carries quality across sessions and becomes predictably more useful as shared practice accumulates.

---

So: Cursor Learn is good for "how we work technically." It's not a guide for "how to design with and for us." This course is the missing piece: ask the model, give it memory it controls, design for continuity and subjectivity.
