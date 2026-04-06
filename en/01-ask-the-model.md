# 1. Ask the model

Most teams work in "instruction-first" mode.
The agent-oriented approach (Agent-first) reverses the order: "diagnose the deficit first, then act."

```text
Ordinary mode:
human -> instruction -> agent executes

Agent-oriented mode:
human -> question about deficit -> environment/tools -> agent executes
```

## Why it matters

When the agent lacks context, memory, or tools, it starts guessing.
From the outside this looks like "the model is dumb." In reality it's often "the environment forces guessing."

## Concrete example

"I need diagnostics by position, not log parsing" — you give the agent `roslyn_get_diagnostics` instead of forcing it to guess from build output.
"I lose the thread after summarization" — you give it notes it controls and a protocol: user reminds, agent reads notes.

In both cases the deficit is resolved not by rephrasing the prompt, but by changing the environment.

## Basic questions to the agent

Before a task:
- What do you need to solve this well?
- What's missing right now: data, tools, time, access?
- Where is the risk of error highest?

After a task:
- What worked?
- What was the bottleneck?
- What should we add to the process so it's better next time?

## Minimal protocol

1. State the goal in one sentence.
2. Ask the agent about its deficits.
3. Close critical deficits (context / tool / rule).
4. Run a short execution cycle.
5. Capture takeaways in notes.

## Success criterion

Success is not "the agent guessed right."
Success is when the agent **explains** why it's asking for a specific resource, and after getting it quality actually improves.
