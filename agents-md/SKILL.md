---
name: agents-md
description: >
  Use before creating or editing any `AGENTS.md`. Keeps project-level agent
  guidance terse and operational; covers placement, content, and what belongs
  elsewhere.
---

Use before any create/edit/move/split of `AGENTS.md`.

## Placement

- Put a rule in `AGENTS.md` only if it matters for most project work. If it is irrelevant for >30% of project work, do not put it in `AGENTS.md`.
- Use the project-level `AGENTS.md` for repo-wide defaults, safety rules, shared invariants, key paths, core principles, non-obvious maintenance rules, project gotchas, and escalation points.
- When `AGENTS.md` gets too large, move detail into `docs/*` or other agent-facing docs and leave a short pointer behind.

## Write It Like Ops

- Write operator instructions, not a README.
- Use short headings, imperative bullets, exact paths, and concrete commands.
- Optimize for scan speed: dense, specific, no filler.
- Keep it token-light: every line must earn its cost.
- State defaults, constraints, and decision rules. Explain why only when it prevents misuse.
- Prefer durable rules over task-specific notes.

## Keep / Cut

Keep:
- required checks, forbidden commands/actions, and stop conditions
- source-of-truth paths and ownership boundaries
- workflow invariants, concurrency constraints, and repo-specific gotchas
- links to deeper docs when detail is needed

Cut:
- generic coding advice the model already knows
- standard framework or language conventions unless this repo intentionally deviates
- temporary task notes, TODO dumps, historical rationale
- duplicated rules that already live in a better source
- secrets, credentials, or private data

## Hygiene

- State each rule once. Link instead of repeating.
- When touching an `AGENTS.md`, remove stale or contradictory text in the same pass.
- If a repo needs more detail, extract it into existing agent-facing docs, keep `AGENTS.md` as the routing layer, and add a pointer in the same change.

If you changed `AGENTS.md`, summarize what changed and why this scope is correct.
