# Scope Decision Rubric

Load this reference for contested, high-stakes, or cross-system scope decisions.

## Verdict Definitions

### Include in MVP

Use when the change is required for:

- production usability
- logical closure of the main flow
- compliance / risk / audit baseline
- avoiding status, money, contract, or approval inconsistency
- future compatibility that cannot be added later without migration

### Simplify for MVP

Use when the capability is needed, but the proposed version is too broad.

Simplification options:

- support fewer roles or scenarios
- keep manual operation for rare cases
- use existing configuration instead of new module
- implement one source system first
- use a compatibility placeholder without full behavior

### Validate First

Use when value is plausible but evidence is weak.

Prefer low/no-build validation:

- check frequency in support / ops tickets
- review manual workaround volume
- test with internal users
- run prototype feedback
- inspect revenue, retention, risk, or incident data

### Defer to Future Iteration

Use when the change is valuable but not necessary for current-phase closure.

Must still define:

- whether data naming should preserve future compatibility
- whether UI/API examples must label it future/out-of-scope
- who owns temporary manual handling

### Add Compatibility Placeholder

Use when future expansion is likely but current behavior should not be implemented.

Examples:

- field name supports future cardinality
- enum reserve value
- UI copy avoids over-specific wording
- data model does not block future source types

### Reject for This Product Layer

Use when the request:

- duplicates an existing platform capability
- belongs to another system or team
- creates long-term platform inconsistency
- solves a one-off case with permanent product complexity
- lacks evidence and has high delivery/ops cost

## Impact Criteria

Assess each area as Low / Medium / High:

| Area | High Impact Signal |
| --- | --- |
| Data Model | new runtime object, snapshot, lifecycle field, migration, retention, reconciliation |
| Flow / State | new status, rollback, retry, approval, cancellation, or re-entry path |
| UI / Prototype | multiple pages, role-specific views, empty/error/no-permission states |
| API / Integration | new callback, downstream consumer, idempotency, timeout, compatibility concern |
| Permission / Ownership | new actor, approval owner, source of truth, manual operator, audit owner |
| Operations / Rollout | migration, exception queue, monitoring, SOP, phased rollout, rollback |

## Scope Output Template

```md
## Verdict

Include in MVP / Simplify for MVP / Validate First / Defer / Compatibility Placeholder / Reject

## Biggest Risk

...

## Impact Summary

| Area | Impact | Reason | Recommendation |
| --- | --- | --- | --- |

## MVP Boundary

In Scope:
Out of Scope:
Not Supported in This Phase:
Future Iteration:

## Next Step

...
```

