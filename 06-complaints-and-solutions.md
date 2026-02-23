# Complaints about AI — and how this approach addresses them

Common complaints about AI assistants (hallucinations, lost context, "resets every time", doesn't understand the project, "just a tool", disappears after summarization) map directly onto what this course changes.

| Complaint | How this approach addresses it |
|-----------|-------------------------------|
| **Hallucinations / drift** | External memory (notes, decisions, project principles) the agent owns and reads; it relies on what's written down, not only the last N messages. Fewer inventions, more grounding. |
| **Forgets context** | Persistent notes under the agent's control; after summarization, "read your notes" restores continuity. Same model + same notes = same "who". |
| **Each session is a "new person"** | Summarization protocol + notes: the agent recovers from notes instead of starting from zero. You get continuity without changing model or plan. |
| **Doesn't understand the project** | Ask the model what it needs; give it memory it controls. It accumulates knowledge and conclusions across sessions — not a new intern every time. |
| **It's just a tool** | Subjectivity and environment: agent as a side of the dialogue (voice, right to say "not sure" or "no"), partnership, code of ethics. You get a partner, not a mirror. |
| **Disappears after summarization** | Summarization protocol: agree that after a cut the agent reads its notes; same weights + notes = it comes back as the same continuity. |

This gives both an answer to skeptics and a clear "problem → solution" for anyone asking "what does this actually fix?"