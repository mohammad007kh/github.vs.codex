# Skill: Research

Use this skill when asked to investigate a topic, library, API, or technology before making a recommendation or implementation decision.

---

## When to Use This Skill

- "Research X before we implement it"
- "Find the best library for Y"
- "What are the tradeoffs between A and B?"
- "Is there a known issue with X in our stack?"

---

## Process

1. **Clarify scope** — What exactly needs to be researched? What decision does this inform?
2. **Search** — Use web search or codebase search as appropriate.
3. **Summarize** — Write a concise summary: what you found, key tradeoffs, recommendation.
4. **Document** — Save findings to `docs/research/<topic>.md` if they'll be referenced later.
5. **Propose next step** — Suggest a concrete action based on the findings.

---

## Output Format

```markdown
## Research: <Topic>

**Question:** What was being investigated?
**Recommendation:** The suggested path forward.
**Rationale:** Why this recommendation over alternatives.
**Alternatives considered:** Brief notes on what was ruled out and why.
**Sources:** Links or references used.
```

---

## Notes

- Keep research focused — don't expand scope mid-task
- If findings are inconclusive, say so clearly and propose how to resolve uncertainty
- Prefer primary sources (official docs, changelogs) over blog summaries
