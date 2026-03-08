---
name: agent-readiness
description: Assess how ready a software repository is for AI coding agents and produce a short, evidence-backed readiness report with prioritized recommendations. Use when asked to evaluate agent readiness, estimate a Factory-style maturity level, audit a repo for autonomous coding blockers, or recommend changes that improve agent effectiveness, feedback loops, and safety.
---

# Agent Readiness

Assess agent readiness by hand from repo evidence. Produce a tight report, not a long audit.

Do not call external scoring services. Do not write scripts to score the repo. Read the codebase, docs, config, and workflow signals directly, then make a judgment.

## Defaults

- Use the current Factory model as the baseline: 5 maturity levels, gated progression, 9 pillars.
- Treat the article's "8 pillars" wording as stale. Current Factory docs and live reports use 9 pillars.
- Estimate a Factory-style level. Do not present it as an official Factory score.
- Round down when evidence is mixed.
- Optimize for evidence over theory: cite files, commands, configs, CI jobs, and missing artifacts.
- Use normal repo reconnaissance. Do not force a canned scan sequence if simpler exploration already exposed the right evidence.
- Treat `AGENTS.md` as the primary agent entrypoint. Agent-operational guidance should live there or be directly traceable from it.
- Start from the files that govern contribution and feedback loops: local `AGENTS.md`, the docs it points to, README, build/test config, CI workflows, env setup, and representative packages or apps.
- In monorepos, sample enough areas to catch variance. Call out partial adoption explicitly.

## How To Judge

Work bottom-up.

1. Establish the highest level that the repo can defend with evidence.
2. Check each pillar as `Strong`, `Partial`, `Missing`, or `Unknown`.
3. Treat missing Level 1 or Level 2 basics as hard caps, even if a few advanced signals exist.
4. Prefer "near Level N+1" over inflating the current level.
5. Keep the final report under roughly 250-400 words unless the user asks for depth.

Use the 80% gating idea qualitatively:

- If most signals for a level are present and lower levels are solid, unlock it.
- If several foundational signals are weak, stop at the previous level.
- If evidence is unavailable, do not assume the repo passes.

## The 5 Levels

- `Level 1 - Functional`: code runs and basic validation exists. Look for README, install/build/test commands, linter/formatter/type checker, and unit tests.
- `Level 2 - Documented`: the repo is operable without tribal knowledge. Look for `AGENTS.md` that tells an agent where to start, what to run, what can go wrong, and where deeper docs live; plus reproducible local setup, env templates, pre-commit hooks, and documented workflows.
- `Level 3 - Standardized`: production-grade baseline for agents. Look for integration or E2E tests, maintained docs, security scanning/guardrails, and usable observability.
- `Level 4 - Optimized`: feedback loops are fast and measured. Look for fast CI, flaky-test handling, regular deploy path, feature flags, richer task discovery, and analytics/experimentation.
- `Level 5 - Autonomous`: self-improving orchestration is real, not aspirational. Only assign this with explicit evidence of autonomous decomposition, remediation, and continuous improvement loops.

Default recommendation: aim for Level 3 first. Most repos get more value from becoming consistently standardizable than from chasing Level 4 polish early.

## The 9 Pillars

For each pillar, record the status plus 1-2 evidence points.

- `Style & Validation`: linting, formatting, static analysis, type checking, pre-commit, one command that catches obvious issues locally.
- `Build System`: deterministic install/build/dev commands, pinned tool versions, no Slack-thread knowledge required to compile or start the app.
- `Testing`: unit tests, integration/E2E where warranted, local test commands, deterministic fixtures, reasonable runtime.
- `Documentation`: `AGENTS.md` first, then the docs it points to. Judge setup/run/debug instructions, freshness, and whether agent-critical guidance is easy to find from the entrypoint instead of scattered across the repo.
- `Development Environment`: devcontainer, Docker Compose, `mise`, `direnv`, `env.example`, seeded local services, minimal setup drift.
- `Debugging & Observability`: structured logs, metrics, tracing, error reporting, runbooks, clear repro/debug path.
- `Security`: branch protection, CODEOWNERS, secret scanning, dependency scanning, least-privilege defaults, clear secret handling.
- `Task Discovery`: issue templates, PR templates, labels, backlog hygiene, small task boundaries, enough context for an agent to pick up work safely.
- `Product & Experimentation`: analytics, feature flags, experiment rails, outcome measurement, rollout visibility.

## What Strong Evidence Looks Like

- `Strong`: discoverable, documented, and enforced. The agent can use it without guessing.
- `Partial`: exists, but coverage is spotty, stale, slow, or tribal.
- `Missing`: absent, or present in name only.
- `Unknown`: the signal may exist outside the repo. Use this sparingly and call out the blind spot.

Examples:

- A linter config with a documented `lint` task is `Strong`; a mention in README without config is `Partial`.
- CI-only validation with no local command is usually `Partial`, not `Strong`.
- A stale `AGENTS.md` that contradicts the repo is worse than missing docs; treat it as `Partial` or `Missing`.
- If key setup or workflow docs exist but are not reachable from `AGENTS.md`, the documentation pillar is at best `Partial`.
- One package in a monorepo having tests does not make the testing pillar `Strong`.

## Common Blockers And Fixes

Favor recommendations that reduce agent latency, ambiguity, and blast radius.

- Missing `AGENTS.md` or shallow agent docs: add exact setup, build, test, done-check, and stop-condition guidance.
- Important docs exist but are scattered: make `AGENTS.md` the index and point to the deeper sources of truth.
- No local validation loop: add `lint`, `typecheck`, `test`, and pre-commit or equivalent.
- Fragile dev setup: add `env.example`, reproducible toolchain config, and local services bootstrap.
- Weak safety rails: add CODEOWNERS, secret scanning, dependency scanning, and branch protections.
- Weak runtime visibility: add structured logging first, then metrics/tracing where justified.
- No integration coverage: add a small number of high-value path tests before broad E2E suites.
- Poor task discovery: add issue/PR templates, labels, and acceptance criteria.
- No rollout measurement: add feature flags and analytics around user-visible changes.

Prefer the smallest change that unlocks the next level.

## Report Format

Use this shape unless the user asks for something else:

```md
Agent readiness: Level N - <name> (<confidence>)

Summary
- 1-2 sentences on current state and the next level boundary.

Pillars
- Style & Validation: Strong | evidence
- Build System: Partial | evidence
- Testing: ...
- Documentation: ...
- Development Environment: ...
- Debugging & Observability: ...
- Security: ...
- Task Discovery: ...
- Product & Experimentation: ...

Top blockers
- ...
- ...

Recommended next moves
1. ...
2. ...
3. ...
```

Keep the recommendations prioritized and concrete:

- name the artifact to add or fix
- say why it matters for agents
- say which level or pillar it unlocks

## Calibration Rules

- Do not punish a small library for lacking full product analytics if analytics are irrelevant.
- Do punish missing basics even in popular repos.
- Distinguish repo quality from agent readiness. A good codebase can still be agent-hostile if setup, feedback loops, or guardrails are implicit.
- Be explicit about scope gaps: if branch protection or deployment frequency is not visible from the repo, say so.
- If the repo looks split between mature and immature areas, say "mixed readiness" and cite the boundary.
