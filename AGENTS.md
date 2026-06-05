# Project Context

> This file is the single source of truth for all AI coding agents.
> It follows the AGENTS.md open standard (Agentic AI Foundation / Linux Foundation).

---

## Project Overview

<!-- Replace with your project description -->
**Name:** My Project  
**Purpose:** What this project does and why it exists.  
**Status:** Active development  

---

## Tech Stack

<!-- List your actual stack -->
- **Language:** e.g. TypeScript / Python / Go
- **Framework:** e.g. Next.js / FastAPI / Gin
- **Database:** e.g. PostgreSQL / SQLite
- **Testing:** e.g. Vitest / pytest
- **Package Manager:** e.g. pnpm / uv / go mod

---

## Repository Structure

```
/
├── src/           # Application source code
├── tests/         # Test files (mirror src/ structure)
├── docs/          # Architecture decisions, references
├── scripts/       # Build, deploy, and utility scripts
└── templates/     # Reusable code/doc templates
```

---

## Architecture Decisions

<!-- Document key decisions so agents don't second-guess them -->
- e.g. "We use server-side rendering for all pages — do not suggest switching to CSR."
- e.g. "Authentication is handled by X — do not introduce a second auth system."
- e.g. "All database access goes through the repository layer."

---

## Coding Conventions

- **Naming:** camelCase for variables/functions, PascalCase for types/components
- **Imports:** absolute paths only (no relative `../../../`)
- **Error handling:** always explicit — no silent catches
- **Comments:** explain *why*, not *what*
- **Tests:** every new function needs at least one test

---

## Testing Approach

- Run tests with: `<your test command>`
- Tests live next to source files OR in `/tests` mirroring `/src`
- Do not modify test files unless explicitly asked to fix tests

---

## What NOT to Do

<!-- Prevent common agent mistakes specific to your project -->
- Do not add dependencies without asking first
- Do not refactor files that aren't related to the current task
- Do not change the database schema without creating a migration
- Do not commit secrets or API keys

---

## Key Commands

```bash
# Install dependencies
<install command>

# Run development server
<dev command>

# Run tests
<test command>

# Build for production
<build command>
```

---

## Current Focus

<!-- Update this section as the project evolves -->
- Active branch / milestone: `main`
- In progress: (describe current task if relevant)
- Blocked on: (anything the agent should know)
