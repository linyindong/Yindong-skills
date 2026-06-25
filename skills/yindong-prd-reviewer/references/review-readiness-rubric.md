# Review Readiness Rubric

Load this reference when artifact type, review depth, or score/readiness is ambiguous.

## Readiness Ladder

### Ready for Engineering Review

- Product goal and current-phase scope are clear.
- Main flow and major exception flows are closed.
- Ownership and source of truth are explicit.
- State, data/API, operational, and rollout implications are clear enough for RFC or implementation planning.
- Open questions are non-blocking or have owners.

### Mostly Ready with Product Fixes

- Main direction is understandable.
- Product semantics are mostly clear.
- Some scenario matrices, edge cases, ownership details, acceptance criteria, or rollout notes need improvement.
- Missing items are fixable without changing the product direction.

### Not Ready; Product Logic Blocked

- Requirement goal, scope, owner, source of truth, or state result is ambiguous.
- Main flow does not close.
- Current-phase behavior conflicts with examples or future-phase statements.
- Missing decisions may create money, contract, approval, status, or operational inconsistency.

### Needs Discovery / Scope Decision First

- Demand evidence is weak.
- MVP boundary is unsettled.
- The problem may be solved by existing capability.
- The proposal may be too large, too one-off, or assigned to the wrong product layer.

## Artifact Calibration

### Short Feature PRD / Small Functional Change

Expected standard:

- Clear business scenario and goal.
- Clear in-scope behavior.
- Clear owner for each changed system.
- Clear API/data contract if any interface changes.
- Key happy path and major exception path.
- Rollout or compatibility note if existing users/data are affected.

Do not over-penalize for missing full platform governance sections if the change is genuinely small.

### Implementation Note / API Change Note

Expected standard:

- Exact changed field/API/enum/contract is defined.
- Source system and persistence owner are clear.
- Validation/default/backward compatibility behavior is clear.
- Downstream consumers and migration impact are clear.
- Examples are sanitized and aligned with the contract.

Call out when the artifact is closer to an implementation note than a complete PRD.

### One-Page PRD / BRD / Stakeholder Alignment Doc

Expected standard:

- Concise problem, goal, scope, value, decision points, and high-level flow.
- Avoid excessive implementation detail.
- Identify which details must live in a separate PRD or tech spec.

Do not require full API tables unless the one-pager is being used as the only delivery artifact.

### Migration PRD

Expected standard:

- Source and target systems are clear.
- Migration trigger, sequence, and completion criteria are defined.
- Data mapping and validation checklist are present.
- Cutover, rollback, retry, and manual handling are addressed.
- Ownership for each migration step is explicit.

### Configuration UI PRD

Expected standard:

- Page path or entry point is clear.
- List fields, filters, create/edit behavior, validation rules, and empty/error states are defined.
- Permission, audit, and operation logging are covered when the UI changes operational data.
- Configuration object and runtime effect are not confused.

### Formula / Rule Logic PRD

Expected standard:

- Rule format and field definitions are explicit.
- Processing sequence is deterministic.
- Examples cover normal and edge cases.
- Backward compatibility and default behavior are clear.
- Data source and owner of reference data are defined.

### Operational SOP / Issue-Handling Note

Expected standard:

- Trigger condition and owner are clear.
- Status transition and closure criteria are explicit.
- Manual handling, audit trail, and exception queue are covered where relevant.
- The SOP does not hide product/system gaps that should be fixed later.

### External Integration PRD

Expected standard:

- System boundary, request/response contract, callback, timeout/retry, idempotency, and error handling are clear.
- Sandbox/production differences and rollout plan are covered when relevant.
- Ownership between internal systems and external partner is explicit.

### Large 0-to-1 Platform PRD

Expected standard:

- Business problem to reusable platform capability is clear.
- System boundary and ownership are explicit.
- Configuration objects and runtime objects are separated.
- Main flows, state machine, callback/retry/rollback/reconciliation paths are covered.
- API/data changes, edge cases, rollout, operations, audit, and open questions are complete.
- MVP, out of scope, not supported in this phase, and future iteration are explicit.

Apply the full checklist strictly.

