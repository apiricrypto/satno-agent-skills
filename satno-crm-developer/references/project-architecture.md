# SATNO CRM Project Architecture Reference

This reference summarizes stable facts from the live SATNO CRM repository. The live repository remains authoritative.

## Repository

Primary: `apiricrypto/SATNO-CRM-Private`

## Current platform baseline

- React 19 + TypeScript + Vite
- React Router v7
- TanStack Query
- React Hook Form
- shadcn-admin-kit + ra-core
- Shadcn UI + Radix UI
- Tailwind CSS v4
- Supabase: PostgreSQL, REST, Auth, Storage, Edge Functions
- Vitest for unit tests
- Playwright tooling is present for browser/e2e workflows

## Core CRM domains

- Contacts
- Companies
- Deals / Kanban pipeline
- Tasks
- Notes
- Tags
- Sales/team members
- Activity history
- Settings
- Authentication

## Important architecture rules

### Declarative database source of truth

Schema definitions live under `supabase/schemas/`.

Migrations under `supabase/migrations/` are generally generated from schema changes and should not be treated as the primary design surface.

When changing contact/company structures, also inspect:
- summary views,
- CSV import/export,
- merge logic,
- FakeRest generators/adapters,
- any affected edge functions.

### Two data providers

1. Supabase for real application behavior.
2. FakeRest for demos/development.

Changes to filters, views, or derived fields may require parity work in FakeRest.

### Domain configuration

Many business options are configured through the `<CRM>` component in `src/App.tsx`, including sectors, deal stages/categories, note statuses, task types, branding, and themes.

Prefer configuration over hardcoding when the existing architecture supports it.

### Views and triggers

- Aggregated reads use database views such as contact/company summaries.
- Auth users and CRM sales users are synchronized by database triggers.
- User deletion is intentionally avoided; account disabling is preferred.

### Filters

The project uses `ra-data-postgrest`-style filters such as:

`field_name@operator`

Any new operator must be considered for FakeRest compatibility.

## Agent workflow

Claude Code has repository-specific orchestration rules in `CLAUDE.md`.

For code changes, inspect that file before editing. The repository may route work through an agent harness with planner/developer/reviewer/merger/documentator roles.

Do not bypass the repository's active orchestration rules unless the user explicitly requests direct implementation.

## Validation commands

Prefer the commands documented by the repository. Common checks include:
- unit tests
- typecheck
- lint
- build
- e2e where required

Never report a check as successful unless it actually ran.

## SATNO-specific product expectations

In addition to upstream Atomic CRM behavior, SATNO work commonly requires:
- Persian-first RTL interface
- Jalali date presentation/input
- explicit Rial/Toman semantics
- mobile-friendly staff workflows
- Bale Market lead intake
- Tender Radar opportunity intake
- project/purchasing and finance-oriented extensions

Before implementing one of these, verify what already exists in the current branch.
