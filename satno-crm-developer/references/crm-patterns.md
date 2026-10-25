# CRM Pattern Library for SATNO

Use this document as a selective design checklist, not as a source of truth for implementation.

## External reference

Primary inspiration:
- https://github.com/PranavNagrecha/AwesomeSalesforceSkills

Why it is useful:
- decomposes a large CRM domain into focused skills,
- uses routing/progressive disclosure instead of loading everything,
- documents anti-patterns and gotchas,
- separates implementation, administration, review, and validation concerns.

Salesforce-specific objects, APIs, permissions, and deployment assumptions do not apply automatically to SATNO CRM.

## Recommended SATNO domain slices

When a task grows beyond one focused change, reason in these slices:

### Lead and intake

For Bale Market or Tender Radar sourced records:
- preserve source identity and source URL/id,
- make ingestion idempotent,
- prevent accidental duplicates,
- record import/processing status,
- keep operator-visible provenance,
- define retry/failure behavior.

### Contacts and companies

Check:
- deduplication,
- merge semantics,
- multiple phones/emails,
- company association,
- import/export compatibility,
- ownership and visibility.

### Deals and opportunities

Check:
- pipeline/stage transitions,
- owner,
- value and currency semantics,
- next action / follow-up,
- source,
- history of important state changes,
- won/lost outcome.

### Tasks and follow-up

Check:
- assignee,
- due date/time,
- Jalali display vs stored timestamp,
- status transitions,
- reminders,
- relation to contact/company/deal,
- mobile usability.

### Data quality

Useful audit patterns:
- missing owner,
- stale leads/deals,
- duplicated contacts/companies,
- invalid phone/email formats,
- missing source attribution,
- inconsistent currency fields,
- records without next action.

### Security and permissions

Always consider:
- Supabase Auth,
- RLS,
- role/ownership boundaries,
- server-side enforcement,
- edge-function authorization,
- sensitive financial/customer data.

Do not rely on hidden UI controls as authorization.

## Validation patterns

For substantial CRM changes, consider a two-stage validation:

1. Engineering validation
   - typecheck
   - lint
   - unit/e2e tests
   - DB/schema validation

2. CRM behavior validation
   - duplicate behavior
   - permissions
   - audit/history
   - mobile workflow
   - import/export
   - source provenance
   - currency/date correctness

## Anti-patterns

Avoid:
- loading a huge CRM skill library into every session,
- creating new concepts without checking existing SATNO abstractions,
- copying Salesforce terminology directly,
- making schema changes only in migrations,
- fixing UI without checking mobile/RTL,
- creating integration records without deterministic deduplication,
- changing money/date semantics without explicit migration/backward-compatibility review,
- declaring release readiness from build success alone.
