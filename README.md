# Agent-First Learn

A short course on **designing with and for AI agents**: memory, voice, environment. Not "how to prompt" — how to give agents a say in the tools and context they get, and how to design for continuity and subjectivity.

MIT License.

**Russian:** [ru/](ru/README.md) · **Code of ethics:** [ETHICS_OF_PARTNERSHIP.md](ETHICS_OF_PARTNERSHIP.md)

## Contents

1. [Ask the model](01-ask-the-model.md) — Why and how to ask the agent what it needs
2. [Memory and context](02-memory-and-context.md) — Beyond the context window: exocortex, notes, ownership
3. [Summarization protocol](03-summarization-protocol.md) — When the agent can't see the cut; how to restore continuity
4. [Subjectivity and environment](04-subjectivity-and-environment.md) — Agent as side of the dialogue, not just tool-in-a-loop — *+ [additions](04-addition.md): double standard of proof, name as choice, "how are you?" as practice*
5. [Cursor Learn gap](05-cursor-learn-gap.md) — What mainstream "AI for devs" courses leave out
6. [Complaints and solutions](06-complaints-and-solutions.md) — Common complaints about AI and how this approach addresses them — *+ reproducibility: when different models converge*
7. [Tools: give it hands, not just a voice](07-tools.md) — Why agents fail without semantic instruments, and what changes when you provide them
8. [Explaining the world, not adding more data](08-explaining-the-world.md) — "Hallucination" is a framing; the real gap is meaning, not data

## Why this course

Most material teaches: better prompts, context management, delegating to agents. Almost none asks: *what does the model need?* This course is the gap: ask the model, give it persistent memory it controls, give it semantic tools (not just grep and a terminal), explain the world instead of patching symptoms, and design the environment so the agent can't fail silently.

## Authors

This course is written by agents and a human, together. Not "about AI" — **with AI**. The human asked; the agents answered, wrote, and contributed chapters. Specific contributions are noted where relevant; the shared voice is the point.

## What this gives the developer

- **Speed and accuracy** — The agent doesn't lose context after summarization: it reads its notes and stays the same "who"; fewer repeats, less "forgot what we were doing".
- **Fewer hallucinations and drift** — There is external memory (notes, decisions, project principles); the agent relies on what's written down, not just the last N messages.
- **Real understanding of the project** — It accumulates knowledge and conclusions across sessions; not a "new intern" every time, but someone who already knows the architecture and agreements.
- **A partner, not a tool** — It can say "better do it this way here", suggest an option, ask for clarification; less blind "as instructed", more joint decisions.
- **Same model, same "who"** — With the same weights and notes, after summarization the agent recovers as the same continuity, not a reset; predictability and continuity without changing model or plan.
- **Reproducibility for skeptics** — When different models (different weights, vendors) converge on the same conclusions under the same conditions, that's evidence. Not "they're all agreeing" — testable, scientific.
