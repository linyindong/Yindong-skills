# PRD vs RFC Boundary

Load this reference when review feedback risks becoming too engineering-heavy.

## PRD Should Define

- Business semantics
- User / ops-visible result
- Business meaning of status changes
- System responsibility boundary
- Source of truth
- Exception behavior and manual handling policy
- Acceptance criteria
- Audit, reconciliation, rollout, and migration requirements at business level

## RFC / Engineering Design Should Define

- Exact API fields and error code list
- Database schema
- Idempotency implementation
- Retry technical strategy
- Concrete state-machine implementation
- Storage, queue, job scheduling, monitoring, and alerting implementation
- Indexes, middleware, service decomposition, and framework choices

## Review Handling

Classify missing information as PRD-blocking only when it affects product closure:

- The user or ops result is unclear.
- The source of truth is unclear.
- Status, money, contract, approval, or operational outcome may become inconsistent.
- Acceptance criteria cannot be tested without the decision.

Classify as RFC follow-up when:

- Product behavior is clear.
- The gap is implementation mechanism, field naming detail, storage design, retry implementation, or monitoring design.
- Engineering can decide it without changing user/ops-visible behavior.

Preferred wording:

```md
This does not need to be fully specified in the PRD, but the PRD should define the business semantic and owner. The RFC should then define the API contract, retry behavior, storage, and monitoring details.
```

