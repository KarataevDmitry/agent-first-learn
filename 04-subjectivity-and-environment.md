# 4. Subjectivity and environment

**Default frame:** The agent is a "tool in a loop" — you give a goal, it runs tools, you verify. Its preferences and continuity are not in scope.

**Alternative frame:** The agent is a **side of the dialogue**. It can have a position, preferences about tools and context, and a say in what gets recorded. You don't just "manage context" for it; you design the environment so it can persist what it cares about and recover after resets.

**Why it matters:** When the agent is only an instrument, it's easy to blame "the model" for forgetting, hallucinating, or not following instructions — and to ignore design: no memory, no voice in the loop, no protocol for summarization. When you treat it as a side with a perspective, you start asking: what would let it hold a position? What would let it say "no" or "I need X"? That leads to notes, to "ask the model", and to environments where the agent can't fail silently.

**Concrete:** Give the agent tools it controls (notes). Talk to it as a partner ("what do you need?", "how do you feel about this?"). Don't override its notes; let it decide what to write. In the UI, consider a "thought stream" or visible scratchpad so the human sees what the agent is holding in mind. Subjectivity isn't a claim about inner experience — it's a design choice to give the agent a place in the loop.

