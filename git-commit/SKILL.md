---
name: git-commit
description: >
  Mandatory read before creating git commits. Stages only intended files, groups changes into logical commits, and writes concise Conventional Commits-style subjects.
---

## Format

`<type>(<scope>): <summary>`

- `type` REQUIRED. Use `feat` for new features, `fix` for bug fixes. Other common types: `docs`, `refactor`, `chore`, `test`, `perf`.
- `scope` OPTIONAL. Short noun in parentheses for the affected area (e.g., `api`, `parser`, `ui`).
- `summary` REQUIRED. Short, imperative, <= 72 chars, no trailing period.

## Notes

- One commit = one cohesive, reviewable change.
- Split unrelated changes into multiple commits with selective staging.
- "commit all" means stage all relevant files, not "force one commit".
- If multiple logical groups exist and user did not request a squash, create multiple commits.
- Body is OPTIONAL. If needed, add a blank line after the subject and write short paragraphs.
- Do NOT include breaking-change markers or footers.
- Do NOT add sign-offs (no `Signed-off-by`).
- Only commit; do NOT push (unless explicitly asked).
- If caller provides file paths or globs, limit staging to those files unless explicitly told otherwise.
- By default, do NOT run linters, formatters, tests, builds, or similar pre-commit checks unless the user explicitly asks for them or an `AGENTS.md` requires them.
- If it is unclear whether a file belongs in the commit, ask.

## Steps

1. Parse the prompt for file paths/globs and extra instructions; treat them as commit constraints.
2. Review `git status` and `git diff` to understand the current changes, limited to specified files when provided.
3. Partition changes into the smallest logical commit groups by intent and cohesion.
4. If grouping or file inclusion is ambiguous, ask before committing.
5. Stage only the files for the current logical commit.
6. Run `git diff --cached --name-only` to verify the staged set matches one cohesive change.
7. Run `git commit -m "<subject>"` (and `-m "<body>"` if needed).
8. Repeat for remaining logical groups, if any.
