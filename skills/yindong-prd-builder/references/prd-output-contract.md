# PRD Output Contract

Load this reference when building a full PRD, complex platform PRD, migration PRD, configuration UI PRD, API/data change note, or when the user asks for a reusable PRD structure.

## Universal Contract

Every product requirement artifact should make these decisions visible:

- Business problem and why now
- Current-phase goal
- In scope / out of scope / not supported now / future iteration
- Actors and systems
- Main flow and exception flow
- Ownership and source of truth
- User / ops-visible result
- API, data, or configuration impact when relevant
- Acceptance criteria or scenario matrix
- Rollout, rollback, migration, or temporary manual handling when relevant
- Open questions with owner or decision party when known

## Full PRD

Use this structure for complex product or platform work:

1. Background
2. Goal
3. Scope
4. Actors / Systems
5. Overall Flow
6. Flow Details
7. Requirements by System
8. API / Data Changes
9. Scenarios & Edge Cases
10. Rollout / Operations
11. Open Questions
12. Dependencies / Risks

## Short Feature PRD

Use this when the change is local and low-complexity:

1. Background
2. Objective
3. Scope
4. Requirements
5. API / Data Changes, if any
6. Edge Cases
7. Acceptance Criteria
8. Links / Attachments

## 0-to-1 Platform PRD

Add these sections or tables:

- Platform direction and design principles
- Reuse vs new-build decision
- Ownership / source-of-truth matrix
- Configuration objects vs runtime objects
- Lifecycle / state transition
- Snapshot and versioning behavior
- Callback, retry, timeout, idempotency business semantics
- Audit / event log / traceability requirements
- Permission and source-system isolation
- MVP exclusions and future-compatible placeholders
- Rollout, migration, reconciliation, and manual fallback

## Migration PRD

Required sections:

- Source and target systems
- Migration trigger and sequence
- Data mapping
- Validation and reconciliation checklist
- Cutover and rollback
- Retry and manual correction
- Completion criteria
- Owner for each step

## Configuration UI PRD

Required sections:

- Page path / entry
- List fields and filters
- Create / edit / disable behavior
- Validation rules
- Permission and audit
- Runtime effect
- Old-record behavior after config change
- Empty, error, and no-permission states

## API / Data Change Note

Required sections:

- Changed contract
- Field table
- Validation / default behavior
- Backward compatibility
- Downstream consumers
- Examples
- Open questions

Default field table:

| Field | Type | Mandatory | Validation / Value | Owner | Consumer | Change Type | Example |
| --- | --- | --- | --- | --- | --- | --- | --- |

## Final Quality Gate

Before finalizing, check:

- [ ] The artifact can be reviewed by product, engineering, QA, and ops without guessing core behavior.
- [ ] Product decisions are separated from RFC-level implementation.
- [ ] Assumptions are not silently converted into requirements.
- [ ] The output is no larger than the task needs.

