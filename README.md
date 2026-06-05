# 🤖 AI Agent Project Structure
### A tool-agnostic scaffold for Claude Code & OpenAI Codex

> **Read this in:** [فارسی](./README.fa.md)

This repository is a reference implementation and teaching guide for structuring projects that work seamlessly with **both** Claude Code and OpenAI Codex — without duplicating your logic or locking yourself into one tool.

---

## 🧠 The Core Idea

Most developers write their project context *for one agent*. When they switch tools, they start over. This repo shows you how to write it **once** and have every major AI coding agent understand it.

The secret: **three layers, one source of truth.**

---

## 📐 The Three-Layer Architecture

| Layer | What Goes Here | Location |
|---|---|---|
| **① Shared Knowledge** | Docs, references, templates, core logic | `/docs`, `/scripts`, `/templates` |
| **② Workflows (Skills)** | Reusable task guides, how-tos | `.claude/skills/` and `.agents/` |
| **③ Tool Config** | Agent-specific settings only | `.claude/` and `.codex/` |

---

## 🗂️ Full Project Structure

```
your-project/
│
├── AGENTS.md                  ← 🌐 Universal source of truth (read by ALL agents)
├── CLAUDE.md                  ← Claude-specific overrides only (references AGENTS.md)
│
├── docs/                      ← Shared: architecture, decisions, references
├── scripts/                   ← Shared: build, deploy, utility scripts
├── templates/                 ← Shared: reusable code/doc templates
│
├── .claude/
│   ├── settings.json          ← Claude Code local settings
│   └── skills/
│       └── research.md        ← Claude-flavored skill definition
│
├── .codex/
│   ├── config.toml            ← Codex CLI configuration
│   └── agents/
│       └── researcher.toml    ← Codex sub-agent definition
│
└── .agents/
    └── research.md            ← Mirrored skill (same content, universal format)
```

---

## 📄 The Two Key Files

### `AGENTS.md` — The Universal Standard
This is your **single source of truth**. As of late 2025, `AGENTS.md` is an open standard under the Linux Foundation's Agentic AI Foundation (AAIF). It is read natively by:

- ✅ OpenAI Codex CLI
- ✅ Claude Code
- ✅ GitHub Copilot CLI (since Aug 2025)
- ✅ Google Gemini CLI
- ✅ Cursor, Windsurf, Zed, RooCode, Factory, Amp

**What to put in it:** project overview, tech stack, architecture decisions, coding conventions, testing approach, and how the repo is organized.

### `CLAUDE.md` — Claude-Specific Overrides
Keep this **minimal**. Since Claude Code also reads `AGENTS.md`, avoid duplicating content here. Use it only for Claude-specific behavior like compaction rules, permission hints, or subagent routing preferences.

**Recommended `CLAUDE.md`:**
```markdown
Read AGENTS.md for full project context.

## Claude Code-Specific
- When compacting, preserve the full list of modified files
- Prefer subagents for research tasks over inline exploration
- Use the skills in .claude/skills/ for recurring task types
```

---

## 🔄 File Format Differences

| Aspect | Claude Code | OpenAI Codex |
|---|---|---|
| Primary instruction file | `CLAUDE.md` | `AGENTS.md` |
| Agent/skill format | `.md` (Markdown) | `.toml` |
| Config format | `settings.json` | `config.toml` |
| Invocation style | Auto-triggered by rules | Explicit routing |
| Runs | Locally in terminal | Cloud sandbox (async) |

---

## ⚡ The Session Handoff Trick

If one agent gets stuck or you want to switch tools mid-task:

1. Ask the current agent: *"Generate a session summary with: current state, modified files, and next steps."*
2. Copy the output.
3. Paste it into the other agent as your first message.

No context is lost. No starting over.

---

## 🚀 Fast Conversion Prompt

Already have a Claude Code project and want to add Codex support? Run this inside Codex:

```
I built this project in Claude Code and want it to work in Codex too.
Please inspect the project and create the necessary Codex adapter files.
Create an AGENTS.md based on CLAUDE.md, set up a .codex/config.toml,
and mirror the existing skills into the .agents/ folder.
Ensure no logic is duplicated — just adapted.
```

---

## ⚠️ Common Pitfalls

| Problem | Fix |
|---|---|
| Agent ignores instructions mid-session | Keep files short; put critical rules at the top; start fresh sessions for new tasks |
| Stale structure references mislead the agent | Don't document folder structure in detail — it goes out of date fast |
| Duplicating AGENTS.md and CLAUDE.md | Keep CLAUDE.md as a pointer, not a copy |
| Codex can't find your skills | Mirror `.claude/skills/` content into `.agents/` |

---

## 📁 Template Files in This Repo

| File | Purpose |
|---|---|
| [`AGENTS.md`](./AGENTS.md) | Example universal project context file |
| [`CLAUDE.md`](./CLAUDE.md) | Example minimal Claude override file |
| [`.claude/skills/research.md`](./.claude/skills/research.md) | Example Claude skill |
| [`.codex/config.toml`](./.codex/config.toml) | Example Codex config |
| [`.codex/agents/researcher.toml`](./.codex/agents/researcher.toml) | Example Codex sub-agent |
| [`.agents/research.md`](./.agents/research.md) | Universal mirrored skill |

---

## 🌐 Further Reading

- [AGENTS.md Specification — Agentic AI Foundation](https://github.com/agentic-ai-foundation/agents-md)
- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [OpenAI Codex CLI](https://github.com/openai/codex)

---

<p align="center">Made for builders who don't want to be locked in.</p>
