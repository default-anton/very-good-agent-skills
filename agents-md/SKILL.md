---
name: agents-md
description: >
  Use before creating or editing any `AGENTS.md`. Defines what belongs there,
  how to keep it root-scoped, and how to keep agent guidance project-specific,
  actionable, and terse.
---

Use before any create/edit of `AGENTS.md`.

## Mental Model

Write for an experienced principal engineer: setup done, real work starting.

`AGENTS.md` is an orientation layer, not a full map. It should help them choose the right starting point for the work in front of them, avoid repo-specific mistakes, and know how to verify the result. If a line would not change how they scope, execute, debug, review, document, or validate the work, cut it.

## Must Cover

- Where to start: source-of-truth paths, relevant subtrees, and task-based routing cues.
- What can go wrong: forbidden actions, risky commands, confirmations, stop conditions.
- What "done" means: mandatory tests, checks, or review steps before claiming completion.
- How this repo differs from defaults: ownership boundaries, invariants, non-obvious conventions, workflow traps.
- Where to go deeper: short conditional pointers for less-common domains.

## Writing Rules

- Write instructions, not explanations.
- Keep it tight: token-light, high-signal, and worth reading first.
- Prefer imperative bullets, exact paths, concrete commands, explicit decision rules.
- Prefer task-based routing (`if touching X, read Y`) over sequential reading lists.
- Cut generic engineering advice, framework basics, temporary notes, duplicates.
- State defaults, ask points, and no-touch zones.
- Remove stale or conflicting guidance in the same edit.

## Quality Check

Before finishing, verify a strong new engineer could answer:
- For the work I am doing, where do I start?
- What must I run before I say "done"?
- What would cause damage or review comments?
- What repo-specific rule would I otherwise miss?

If any answer is missing, the file is not done.

If you changed `AGENTS.md`, summarize what changed and why this scope fits the orientation-layer mental model.
