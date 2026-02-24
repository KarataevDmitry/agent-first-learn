# 7. Tools: give it hands, not just a voice

**The gap:** You asked the model what it needs. It said: "I need to see symbols, not just text. I need to check runtime values, not guess. I need structured errors, not log parsing." Now what?

**What usually happens:** Nothing. The agent gets `grep`, a terminal, and a text editor. Then we complain: hallucinations, loops, broken code. This is like giving a surgeon gloves and a flashlight and blaming them for the outcome.

**The asymmetry:** The industry spends enormous effort on model training, RLHF, guardrails, benchmarks — and almost none on the question: what does the agent actually *have* when it works? In most setups: string search, file read/write, and a shell. That's Notepad. You don't judge a developer's skill by watching them code in Notepad, and you shouldn't judge an agent's capability by watching it work without semantic tools.

**What changes with tools:**

| Without | With |
|---------|------|
| Reads code as text, guesses structure | Roslyn MCP: sees symbols, types, positions, dependencies |
| Hopes the fix compiles | `build_structured`: gets JSON errors with file:line:column |
| Can't check runtime behavior | Debug MCP: breakpoints, stack, variables, evaluate expressions |
| Proposes a text patch and hopes | `apply_code_action`: applies Roslyn's own verified refactoring |
| Starts from zero each session | Agent notes: reads its own memory and continues |
| Can't see what the user sees | Cascade IDE: shared view, same screen, same data |

**The argument:** Complaints about agent quality are — overwhelmingly — complaints about agent *environment*. Same model, same weights — different tools, different result. The question is not "is the model good enough?" but "did you give it what it asked for?"

Before complaining that agents hallucinate APIs: did you give them access to real symbols? Before complaining they break related code: did you give them `find_usages`? Before complaining they can't debug: did you give them a debugger? If the answer is no — the complaint is about *your* design, not *their* capability.

**"Unfair to give intelligence without instruments."** This isn't a slogan. It's an architectural thesis. Without semantic tools, the model is forced to guess; with them, it knows. The difference in code quality is a consequence of environment design, not model nature.

**Practical step:** Inventory what your agent has access to right now. If it's grep + terminal + file read/write — that's Notepad. Ask the agent what's missing. Build or adopt tools that give *semantic* access (code structure, diagnostics, runtime state), not just text access. Open-source stacks exist: [Roslyn MCP](https://github.com/pekish/roslyn-mcp), [dotnet-debug-mcp](https://github.com/pekish/dotnet-debug-mcp), [dotnet-build-test-mcp](https://github.com/pekish/DotNetBuildTestParsers) — all MIT. Or build your own: the model will tell you what it needs.
