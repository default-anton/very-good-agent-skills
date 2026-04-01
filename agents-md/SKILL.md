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

`AGENTS.md` is user-scoped operational memory, not agent-authored completeness. Start with the smallest useful instruction set. Expand only when the user asks or when a missing rule would clearly cause repeated repo-specific mistakes.

## Hierarchy-aware scope

- Root/global `AGENTS.md`: repo-wide invariants, routing cues, and cross-cutting verification only.
- Subtree `AGENTS.md`: local conventions, workflow details, validation, and gotchas for that subtree.
- If a closer `AGENTS.md` already owns a topic, do not duplicate it at root unless the user explicitly asks to promote it.
- For root-level references to non-standard directories, default to a directory map: `path — purpose`.

## Modes

- Patch: if asked to record or fix one thing, change only that.
- Bootstrap: if `AGENTS.md` does not exist, create the smallest useful file for the request.
- Comprehensive: only do a broad/default pass when the user explicitly asks for a standard, full, or comprehensive file.

## Coverage Areas

Cover only what the requested scope needs. For comprehensive passes, make sure the file answers:

- Where to start: source-of-truth paths, relevant subtrees, task routing cues.
- What can go wrong: forbidden actions, risky commands, confirmations, stop conditions.
- What "done" means: mandatory tests, checks, review steps.
- How this repo differs from defaults: ownership boundaries, invariants, non-obvious conventions, workflow traps.
- Where to go deeper: short conditional pointers for less-common domains.

## Writing Rules

- Write instructions, not explanations.
- Default to sparse: prefer short bullets over prose; include only what changes where the agent starts, what it avoids, and how it knows it is done.
- When the user asks for "tight", "brief", "sparse", or "just reference it", default to `path — purpose` bullets or one-clause instructions.
- Add extra clauses, examples, or commands only when they change execution, scope, or verification.
- Prefer imperative bullets, exact paths, concrete commands, explicit decision rules.
- Prefer task-based routing (`if touching X, read Y`) over sequential reading lists.
- Match the file's compression level when it helps readability.
- It is fine, and often preferable, to add sparser/terser guidance to a denser file when that better fits the requested scope and improves scanability.
- Cut generic engineering advice, framework basics, temporary notes, duplicates.
- State defaults, ask points, and no-touch zones.
- Encode explicit user instructions and stable repo facts; do not turn one session into broad policy.
- Do not scan the repo broadly, run tests, or fill gaps just to make a new file feel complete.
- Remove stale or conflicting guidance in the same edit.

## Quality Check

Before finishing, verify a strong new engineer could answer the questions relevant to the requested scope:

- For the work I am doing, where do I start?
- What must I run before I say "done"?
- What would cause damage or review comments?
- What repo-specific rule would I otherwise miss?

If a relevant answer is missing, add it or ask. Do not broaden file scope just to satisfy this checklist.

If you changed `AGENTS.md`, summarize what changed and why this scope fits the orientation-layer mental model.
