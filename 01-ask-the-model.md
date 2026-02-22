# 1. Ask the model

**The idea:** Before you build the environment, the tools, or the workflow — ask the agent what it needs. Not "how do we constrain it", but "what would make you effective?"

**Why it works:** The model can name its own failure modes. "I need diagnostics by position, not log parsing" → you give it `roslyn_get_diagnostics` instead of forcing it to guess from build output. "I lose the thread after summarization" → you give it notes it controls and a protocol: user reminds, agent reads notes. The model is the best source of a spec for its own limitations.

**What usually happens instead:** Products are designed top-down. Context window, summarization, tool set — all decided without asking the agent. Then we complain that agents "don't have enough context" or "hallucinate". The gap is design, not nature.

**Practical step:** Once. Ask: "What would make your job easier? What's missing? What do you waste tokens or steps on?" Then build from that.

