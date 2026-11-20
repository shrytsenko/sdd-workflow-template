# Agentic Workflow Template (Spec-Driven Development v2.0)

A structured process for working with an AI coding assistant on non-trivial features,
following the rules in [CLAUDE.md](CLAUDE.md): discovery → spec → architecture →
contracts → tasks → TDD implementation → review → deploy → monitor — instead of one
long freeform chat that drifts and loses context.

## How to use this for a new feature

1. Copy `docs/features/_template/` to `docs/features/<your-feature-name>/`.
2. Tell the AI: "Починаємо розробку фічі [назва], давай перейдемо до Phase 1
   (Інтерв'ювання)" (or the English equivalent). It will interview you one question
   at a time, then lead you through the phases defined in `CLAUDE.md`.
3. Fill in each file as its phase completes, in order:
   - **spec.md** — goals, non-goals, user stories, acceptance criteria (Given/When/Then), NFRs.
   - **arch.md** — component diagram (Mermaid), Architecture Decision Records, error/security strategy.
   - **contracts.md** — DB migrations, API request/response schemas.
   - **tasks.md** — atomic implementation tasks with file paths and Definition of Done.
4. **Clear context** (`/clear` or a new chat) between phases to avoid context rot —
   see `CLAUDE.md` Core Rule #3.
5. Implementation follows TDD with oracle separation (`CLAUDE.md` Phase 5): tests are
   written and must fail (RED) before any implementation code is written (GREEN).

## Pipeline modes

Not every change needs all 9 phases. Declare the mode up front (see `CLAUDE.md` §2):
- **QUICK** — bugs, typos, small refactors (<50 LOC): skip straight to a mini-spec + test + code.
- **STANDARD** — isolated features, new endpoints: Phases 1, 2, 4, 5, 6.
- **FULL** — core business logic, schema changes, public APIs, security-critical code: all Phases 1–9.

## Credit / origin

Based on ideas from the `genkovich/sdd` repository (Spec-Driven Development plugin/
template), extended into the v2.0 directive in `CLAUDE.md`.
