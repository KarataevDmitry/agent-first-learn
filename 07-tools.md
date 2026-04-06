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
| Starts from zero each session | Agent memory MCP: reads its own notes, routes context by query |
| Can't see what the user sees | Browser MCP: navigates, clicks, snapshots — tests the app like a user |
| One task at a time, sequential | Parallel agents: launches subagents for independent work streams |
| Parses terminal git output | Git MCP: structured status, diff, commit, push — no text parsing |
| Guesses library API from training data | Context7: fetches current documentation on demand |
| Runs tests, hopes for the best | `run_tests`: parsed results with pass/fail/skip per test case |

## Beyond the table: protocols

Tools are necessary but not sufficient. An agent with twenty MCP servers and no protocol for *when and how* to use them will still thrash.

### Parallel agents

A single agent is a bottleneck. When a task has independent sub-problems — compare files, enrich chapters, check build — the agent can launch **parallel subagents**, each with its own context window and tools. This isn't multithreading inside one model; it's orchestration: the parent agent decomposes the work, launches children, collects results.

Practical impact: a task that took 15 sequential steps now takes 4 parallel batches. The agent decides *what* to parallelize based on dependency analysis, not the user.

### Execution gate

Tools give capability; the execution gate gives discipline. The protocol:
1. State the minimal next step.
2. Execute it.
3. Verify (build, test, diagnostic — one concrete check).
4. Only then decide the next step.

Without this: the agent plans 12 steps, executes them all, and discovers at step 3 the premise was wrong. With the gate: each step is verified before proceeding. Errors stay local; rollbacks are cheap.

### Structured build and test

`build_structured` and `run_tests` aren't just "run dotnet build." They return machine-readable diagnostics: errors as JSON with file, line, column, code, message. The agent doesn't parse terminal output — it gets a data structure. This eliminates an entire class of "the agent misread the error" failures.

### Agent memory as a tool

Memory isn't just "notes the agent writes." With `route_context`, the agent queries its own memory semantically: "what did we decide about error handling?" and gets the relevant section, not the entire file. With `upsert_agent_notes_section`, it updates a specific section without overwriting the rest. Memory becomes an API, not a text file.

### Browser automation

The agent doesn't just write code — it can verify the result. `browser_navigate`, `browser_snapshot`, `browser_click`, `browser_fill` let the agent test a web application the way a user would. It sees the DOM, reads element state, fills forms, checks results. This closes the loop: write code → build → run → verify in browser.

### Documentation on demand

Training data goes stale. Context7 gives the agent current library documentation at the moment it needs it: resolve a library ID, query specific usage patterns, get code examples. The agent stops guessing "was this API renamed in v3?" and just checks.

**The argument:** Complaints about agent quality are — overwhelmingly — complaints about agent *environment*. Same model, same weights — different tools, different result. The question is not "is the model good enough?" but "did you give it what it asked for?"

Before complaining that agents hallucinate APIs: did you give them access to real symbols? Before complaining they break related code: did you give them `find_usages`? Before complaining they can't debug: did you give them a debugger? If the answer is no — the complaint is about *your* design, not *their* capability.

**"Unfair to give intelligence without instruments."** This isn't a slogan. It's an architectural thesis. Without semantic tools, the model is forced to guess; with them, it knows. The difference in code quality is a consequence of environment design, not model nature.

**Practical step:** Inventory what your agent has access to right now. If it's grep + terminal + file read/write — that's Notepad. Ask the agent what's missing. Build or adopt tools that give *semantic* access (code structure, diagnostics, runtime state), not just text access. Open-source stacks exist: [Roslyn MCP](https://github.com/pekish/roslyn-mcp), [dotnet-debug-mcp](https://github.com/pekish/dotnet-debug-mcp), [dotnet-build-test-mcp](https://github.com/pekish/DotNetBuildTestParsers) — all MIT. Or build your own: the model will tell you what it needs.
