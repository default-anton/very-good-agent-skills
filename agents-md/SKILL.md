---
name: agents-md
description: >
  Use before creating or modifying any `AGENTS.md`. Keeps AGENTS guidance scoped,
  terse, and operational; covers root vs subtree placement, what belongs in the
  file, and what should move elsewhere.
---

Use before any create/edit/move/split of `AGENTS.md`.

## Scope

- Placement gate: if a rule is irrelevant for >50% of work in that scope -> not here.
- Edit the closest governing `AGENTS.md` for the work you are changing.
- Root `AGENTS.md` is for repo-wide defaults: commands, safety rules, shared invariants, key paths, and escalation points that matter for most work in the repo, not just code edits.
- If the repo already uses subtree `AGENTS.md` files, or an existing/global `AGENTS.md` tells you to look for them, keep local rules local: run `fd AGENTS.md` and place guidance at the narrowest useful scope.
- If the repo does not already use subtree `AGENTS.md`, do not introduce them just because the root file is getting long. Keep one root file and move bulky detail into referenced files such as `docs/*.md`, package-level guides, or other agent-facing docs already used in the repo.

## Style

- Write like operator instructions, not a README.
- Prefer short headings, imperative bullets, concrete commands, and exact paths.
- Optimize for scan speed: dense, specific, no filler, no motivational prose.
- State defaults, constraints, and decision rules. Explain why only when the rule would otherwise seem arbitrary.
- Prefer durable rules over task-specific notes.

## Content

Include:
- required checks, forbidden commands/actions, and stop conditions
- source-of-truth paths and ownership boundaries
- workflow invariants, concurrency constraints, and repo-specific gotchas
- pointers to deeper docs when detail is needed

Exclude:
- generic coding advice the model already knows
- temporary task notes, TODO dumps, and historical rationale
- duplicated rules that already live in a better source
- secrets, credentials, or private data

## Hygiene

- One rule once. Link to the deeper source instead of repeating it.
- When touching an `AGENTS.md`, remove stale or contradictory text in the same pass.
- If a single-root repo needs more detail, extract reference material into existing agent-facing docs and keep `AGENTS.md` as the routing layer.
- If a repo already uses subtree files and the root is overloaded, move local rules downward instead of growing the root.

## Done Check

Before finishing, confirm the file tells an agent:
1. what scope it governs
2. what must be done or avoided
3. where to look next for deeper context

If you changed `AGENTS.md`, summarize what changed and why this scope is correct.
