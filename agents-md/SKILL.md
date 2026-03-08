---
name: agents-md
description: >
  Use before creating or editing any `AGENTS.md`. Defines what belongs there,
  how to keep it root-scoped, and how to keep agent guidance project-specific,
  actionable, and terse.
---

Use before any create/edit of `AGENTS.md`.

## Mental Model

Write for a day-one principal engineer: setup done, first real task starting.

`AGENTS.md` is the first file they read. It must give enough project-specific guidance to finish that task without hidden repo mistakes or predictable review comments. If a line would not change first-task behavior, cut it.

## Must Cover

- Where to start: source-of-truth paths, relevant subtrees, and deeper docs worth opening next.
- What can go wrong: forbidden actions, risky commands, confirmations, stop conditions.
- What "done" means: mandatory tests, checks, or review steps before claiming completion.
- How this repo differs from defaults: ownership boundaries, invariants, non-obvious conventions, workflow traps.
- Where to go deeper: short pointers for real but less-common domains.

## Writing Rules

- Write instructions, not explanations.
- Keep it tight: token-light, high-signal, and worth reading first.
- Prefer imperative bullets, exact paths, concrete commands, explicit decision rules.
- Cut generic engineering advice, framework basics, temporary notes, duplicates.
- State defaults, ask points, and no-touch zones.
- Remove stale or conflicting guidance in the same edit.

## Quality Check

Before finishing, verify a strong new engineer could answer:
- What do I read next?
- What must I run before I say "done"?
- What would cause damage or review comments?
- What repo-specific rule would I otherwise miss?

If any answer is missing, the file is not done.

If you changed `AGENTS.md`, summarize what changed and why this scope fits the first-task mental model.
