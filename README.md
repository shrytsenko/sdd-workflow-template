# Agentic Workflow Template (Spec-Driven Development, lightweight)

A minimal process for working with an AI coding assistant on non-trivial features:
write down WHAT, then HOW, then a checklist, then implement — instead of one long
freeform chat that drifts and loses context.

## How to use this for a new feature

1. Copy `docs/features/_example/` to `docs/features/<your-feature-name>/`.
2. **Stage 1 — spec.md**: describe the problem and desired behavior in plain language.
   Ask the AI to fill it in with you, or write it yourself. Review it.
3. **Clear context** (start a new chat, or `/clear`). Point the AI at `spec.md` and ask
   it to scan the actual codebase and write **arch.md** — the concrete plan (files,
   data flow, decisions). Review it.
4. **Clear context again.** Point the AI at `arch.md` and ask it to write **tasks.md** —
   a checklist of small implementation steps. (Skip this stage entirely for small
   features — just implement directly from arch.md.)
5. **Clear context again.** Point the AI at `tasks.md` and have it implement, checking
   off items as it goes.

## Why clear context between stages?

Long conversations cause the AI to lose focus and mix up earlier exploration with
later decisions. Re-reading a short, reviewed markdown file at each stage is more
reliable than keeping the whole conversation history alive.

## When to skip stages

This is a *starting template*, not a mandatory checklist. For a one-line bug fix or a
tiny change, skip straight to implementing — don't force a bug fix through 4 stages.
Use the full flow for features with real design decisions or many moving parts.

## Credit / origin

Based on ideas from the `genkovich/sdd` repository (Spec-Driven Development plugin/
template) — adapted here into a lightweight, plugin-free version usable directly in
chat with Claude or ChatGPT.
