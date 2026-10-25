---
name: satno-crm-developer
description: Develop, review, test, document, and release SATNO CRM. Use for work on apiricrypto/SATNO-CRM-Private and related CRM integrations, including Persian/RTL UI, Jalali dates, Rial/Toman handling, Supabase data model, Bale Market intake, Tender Radar intake, sales workflows, testing, GitHub branches/PRs, and release readiness. Optimized for Claude Code and Codex with progressive disclosure to reduce context/token usage.
---

# SATNO CRM Developer

## Purpose

This skill is the lightweight router for SATNO CRM work.

Do not preload all CRM knowledge. Start from this file, inspect the live repository, and load only the reference or project file required for the task.

Primary repository:
- `apiricrypto/SATNO-CRM-Private`

Related SATNO repositories may include:
- `apiricrypto/SatnoBaleMarket`
- `apiricrypto/SATNO-Tender-Radar-Private`
- `apiricrypto/satno-agent-skills`

## Source-of-truth order

For every task, prefer live project evidence over remembered assumptions:

1. `SATNO-CRM-Private/CLAUDE.md` for Claude-specific orchestration rules.
2. `SATNO-CRM-Private/AGENTS.md` for architecture, commands, DB rules, and engineering conventions.
3. `SATNO-CRM-Private/MEMORY.md` for durable project knowledge.
4. Relevant source files, tests, schemas, issues, PRs, and current branch state.
5. This skill and its references.
6. External CRM repositories only as design inspiration.

Never let an external CRM pattern override SATNO-specific behavior without explicit justification.

## Progressive-disclosure routing

Load only what the task needs:

| Task | Load next |
|---|---|
| Architecture, modules, data flow, Supabase | `references/project-architecture.md` + live `AGENTS.md` |
| CRM product behavior, lead/deal/contact workflow | `references/crm-patterns.md` + relevant source files |
| Persian/RTL, Jalali, Rial/Toman | live implementation first; then project conventions |
| DB/schema/migration | live `AGENTS.md`, `supabase/schemas/`, affected tests |
| Claude Code implementation | live `CLAUDE.md` before any code change |
| Codex implementation/review | live `AGENTS.md`, current branch, tests; respect project harness semantics where applicable |
| Bale Market → CRM | inspect both repositories and existing connector contract |
| Tender Radar → CRM | inspect both repositories and existing intake contract |
| Release/deploy | current branch, CI, tests, migration state, release notes |

Do not read large unrelated directories or historical logs unless the task requires them.

## Product conventions

Treat SATNO CRM as Persian-first unless the task explicitly requires another language.

- User-facing Persian layouts must be RTL.
- Jalali dates are preferred in Iranian user-facing surfaces.
- Rial/Toman must never be ambiguous; conversion and storage/display semantics must be explicit.
- Preserve working behavior unless a breaking change is intentionally requested.
- Prefer reusable domain configuration over hardcoding.
- Keep desktop and mobile behavior aligned.
- Do not reintroduce upstream localization or UI behavior that conflicts with SATNO conventions.

## Engineering workflow

1. Inspect repository, branch, working state, relevant project instructions, and affected tests.
2. Determine whether the task is product logic, UI, data model, integration, or release work.
3. Load only the necessary reference and source files.
4. Reuse existing SATNO abstractions before adding new ones.
5. Implement the smallest coherent change that satisfies the requirement.
6. For DB changes, edit declarative schemas first; treat migrations as generated/deploy artifacts according to project rules.
7. Validate with the project's real commands; never claim a test passed unless it ran successfully.
8. For UI changes, check RTL, responsive/mobile behavior, accessibility, loading/empty/error states, and Persian text layout.
9. For integration changes, verify idempotency, deduplication, source attribution, retry behavior, and auditability.
10. Report changed files, checks run, risks, and exact next action.

## Token-efficiency rules

- Do not repeatedly reread files already inspected in the same task unless they changed.
- Prefer targeted search/fetch over repository-wide dumps.
- Prefer symbol/file-level inspection before opening large files.
- Reuse `MEMORY.md` for durable facts, but verify anything operationally sensitive against live code.
- Keep planning concise; do not generate speculative redesigns when a focused patch is sufficient.
- When handing work between Claude Code and Codex, include only: objective, branch/commit, changed files, tests, blockers, and next action.
- Avoid loading external skill libraries wholesale. Extract only the applicable pattern.

## CRM quality gates

For CRM-affecting work, explicitly consider:

- Contact/company/deal/task/note integrity
- Duplicate prevention and merge behavior
- Pipeline/stage transition correctness
- Sales-user ownership and permissions
- Activity/audit history
- Import/export compatibility
- Mobile workflow usability
- Search/filter behavior
- Supabase RLS/auth implications
- FakeRest parity when relevant
- Bale Market / Tender Radar source provenance when relevant

## GitHub discipline

- Do not work directly on a protected production branch unless explicitly instructed.
- Use descriptive branches and scoped commits.
- Prefer reviewable PRs for non-trivial changes.
- Inspect existing issues/PRs before duplicating work.
- Do not silently rewrite or discard unrelated user changes.

## External CRM references

Use external repositories as pattern libraries only. A key reference is:
- `PranavNagrecha/AwesomeSalesforceSkills`

Useful ideas to borrow selectively:
- router skills instead of loading all domain instructions,
- specialized workflow skills,
- anti-pattern/gotcha documentation,
- validation/checker stages,
- explicit separation of product logic from deployment/administration logic.

Do not copy Salesforce-specific assumptions into SATNO CRM.

## Completion report

Return:
- what changed
- affected files/modules
- tests/checks actually run
- known risks/blockers
- branch/commit/PR state
- exact next action for testing or deployment
