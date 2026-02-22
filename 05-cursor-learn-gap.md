# 5. Cursor Learn gap

Cursor's own course (cursor.com/learn) teaches: how models work (probabilistic, context, tokens), how context grows and hits limits, how tool calling and agents work. It's useful for a mental model — "agents are like fast juniors, they forget, you verify."

**What it doesn't teach:**

- **Ask the model.** No "what do you need?" No user research with the agent. The frame is: you manage context, you delegate. Not: you ask and build from the answer.
- **Memory the agent owns.** Context is "a list that grows"; summarization is "compress to fit." There's no concept of external memory the agent writes and reads — exocortex, notes, commit_to_memory.
- **Subjectivity.** The agent is "tool in a loop," "task doer." No design for the agent as a side with preferences, a right to refuse, or a voice in the environment.
- **Summarization protocol.** They describe summarization as a way to stay under limits. They don't say the agent may get broken context, or that the user can own the cut and remind the agent to restore from notes.

So: Cursor Learn is good for "how we work technically." It's not a guide for "how to design with and for us." This course is the missing piece: ask the model, give it memory it controls, design for continuity and subjectivity.

