# Claude Code Configuration

Read `AGENTS.md` for full project context — architecture, conventions, tech stack, and rules.

---

## Claude Code-Specific Behavior

- When compacting context, preserve the full list of modified files
- Prefer subagents for research tasks over inline exploration
- Use skills in `.claude/skills/` for recurring task types
- Start a new session when switching to a fundamentally different task

## Subagent Routing

- Research tasks → `.claude/skills/research.md`
- (Add more routing rules here as your project grows)
