---
name: platform-prd-reviewer
description: Review PRDs, product requirement drafts, platform designs, prototypes, and requirement sections with product-logic-first judgment and artifact-size calibration. Use when the user asks to check, review, validate, score, find gaps, assess whether logic is closed-loop, compare small-feature vs 0-to-1 platform readiness, or decide whether a PRD is ready for product review, engineering review, RFC follow-up, or further scope clarification.
---

# Platform PRD Reviewer

Use this skill in review mode. Prioritize product logic, business closure, scope clarity, ownership, and user/ops outcomes over wording polish or engineering checklist detail. Do not rewrite the document unless the user asks.

First calibrate the review depth. A short feature PRD, implementation note, API change note, one-page alignment doc, and large 0-to-1 platform PRD should not be judged by the same completeness standard.

## Operating Modes

Choose one review mode before writing findings:

- PM-friendly review: judge whether the product logic is understandable and what must be fixed next.
- Engineering-readiness review: check ownership, state, data/API, rollout, audit, and operational completeness.
- Small-feature calibration: review a short or local PRD without forcing full platform standards.
- 0-to-1 platform calibration: apply strict cross-system, lifecycle, source-of-truth, and operations standards.
- Readiness scoring: produce a score/readiness ladder and explain what moves it to the next band.

## When NOT to Use

Do not use this skill to draft or rewrite the PRD unless the user asks. If the document does not exist yet, route to `platform-prd-builder`. If the main question is whether a change belongs in the current phase, route to `platform-scope-checker`.

## Review Stance

Start by judging whether the PRD works as a product document:

- Is the requirement goal clear?
- Is the main flow logically closed?
- Is scope clear?
- Are there logic conflicts?
- Are there fatal product gaps?
- Is it ready for product review, engineering review, or only early discussion?

Keep API fields, error codes, idempotency design, callback retry implementation, storage, queue, job scheduling, and monitoring implementation visible, but classify them as RFC/engineering follow-up unless the missing detail breaks product logic, status consistency, money/contract/approval results, or ownership/source-of-truth decisions.

## Evidence Confidence

Before marking an issue as Fatal/Blocking, classify the evidence basis:

- Confirmed in readable text: directly supported by readable PRD text or table content.
- Seen in diagram/image: appears in a diagram, screenshot, board, or embedded visual; mention that visual details may need human confirmation if extraction is partial.
- Not confirmed in readable content: not found in readable text. Do not say "missing" unless diagrams, tables, comments, screenshots, and linked sections were also checked or supplied.
- Inference: inferred from surrounding context rather than explicitly stated.

When Lark diagrams, boards, images, or embedded objects may contain key flow logic, avoid saying "the PRD does not define X." Prefer: "I could not confirm X in the readable text; if the diagram covers it, downgrade this to a documentation or engineering-readiness gap."

## Lark PRD Reading Limitations

When reviewing Lark Docs, embedded flowcharts, whiteboards, draw.io diagrams, canvases, screenshots, board comments, and linked objects may not be fully machine-readable.

For Lark PRDs:

1. Separate evidence from judgment.
2. State when a conclusion is based only on readable text.
3. If a high-risk flow may be inside an embedded diagram, avoid calling it absent unless the diagram was visually inspected or supplied as an image.
4. Prefer "not confirmed in readable text" over "not written."
5. Ask for or use screenshots when the user challenges a finding that may be covered in diagrams.

Use an evidence note when the PRD relies heavily on diagrams, the review source is a Lark page, diagrams cannot be fully extracted, or the output contains high-risk findings:

```md
Evidence note:
This review is based on readable text/tables and visible snippets available to me. Embedded diagrams/boards may not be fully machine-readable, so any "not confirmed" finding should be validated against diagrams before being treated as final.
```

## Scope Priority Rule

When a capability appears in examples, configuration lists, API samples, or future notes but is explicitly marked as `Out of Scope`, `Not Supported in This Phase`, `Future Iteration`, `Excluded`, or gated by legal/regulatory approval, treat the scope statement as authoritative for the current-phase review.

Do not classify such an item as a current blocking conflict unless the current-phase flow still requires the capability to be enabled.

If a future/out-of-scope item appears in examples, classify it as clarity or consistency:

- ensure examples label it as future/out-of-scope
- ensure product config cannot enable it in the current phase
- ensure QA cases and API samples do not treat it as current-phase behavior

## Main Direction vs. Testable Matrix

If the PRD defines the main business handling direction, such as cancel, refund, reject, retry, freeze, or sync downstream, but does not enumerate all state combinations, owners, failure handling, and acceptance criteria, do not classify the issue as Fatal by default.

Use Must Improve when the missing matrix affects engineering alignment, QA, operations, reconciliation, or support handling.

Use Fatal/Blocking only when the absent detail can cause money, contract, approval, status, or source-of-truth inconsistency and no main product direction is provided.

Preferred wording:

```md
The PRD defines the main handling direction, but should add a scenario matrix covering state combinations, trigger system, final status, user-visible result, downstream sync, refund/retry/manual handling, and acceptance criteria.
```

## Pre-Blocking Self-Check

Before listing an item under Fatal Issues / Blocking Items, verify:

1. Is this truly absent, or only not found in readable text?
2. Could the rule be in a Lark diagram, screenshot, table, comment, or linked section?
3. Does the PRD already provide the main handling direction?
4. Is the remaining issue better described as a missing exception matrix, owner table, acceptance criteria, or RFC follow-up?
5. Is the concern based on a future/out-of-scope item rather than current-phase behavior?
6. Would this issue directly cause money, contract, approval, status, or source-of-truth inconsistency in the current scope?

If uncertain, downgrade to Must Improve, mark the evidence limitation, and ask an open question.

## Default Output Structure

Use this structure by default:

1. Overall Assessment
2. Fatal Issues / Blocking Items
3. Must Improve
4. Nice to Improve
5. Mid-platform / Engineering RFC Follow-up
6. Open Questions
7. Score / Readiness Judgment

### Overall Assessment

Briefly cover:

- requirement goal clarity
- main-flow closure
- scope clarity
- logic conflicts
- fatal gaps, if any
- product/engineering review readiness
- current score or readiness level when useful
- the main next action or routing target: revise PRD, create RFC, run scope decision, or proceed to review

### Fatal Issues / Blocking Items

Use this section only for severe product problems:

- product logic does not close
- business flow breaks
- key owner/source of truth is unclear
- status, money, contract, approval, or operational results may become inconsistent
- core scope is impossible to review because current-phase boundaries are missing

Do not classify every missing API field, error code, or engineering detail as blocking.

### Must Improve

List product-side decisions that must be clarified. Use clear mini-headings instead of making `Issue:` the visual structure.

Preferred format:

```md
**1. Returned resubmission semantics need to be clarified**
Problem:
Why it matters:
Suggested product decision:
```

Suggestions should define business semantics, user/ops-visible behavior, status meaning, source of truth, ownership, acceptance criteria, and manual handling. Do not prescribe engineering implementation unless the user asks.

### Nice to Improve

Use for non-blocking improvements such as clearer scope expression, acceptance scenarios, button/copy naming, future-phase marking, QA cases, table formatting, and reader navigation.

### Mid-platform / Engineering RFC Follow-up

Separate items that should be defined in RFC or engineering design, such as:

- API contract details
- error codes and messages
- idempotency implementation
- callback retry technical strategy
- field tables and schema details
- audit log storage
- snapshot storage design
- permission implementation
- database, queue, job, monitoring, or alerting implementation

Phrase these as follow-up ownership, not PRD failure, unless product semantics depend on them.

### Open Questions

Ask decision-driving questions for product, business, engineering, risk, legal, finance, ops, or external partners. Avoid generic questions.

### Score / Readiness Judgment

When scoring, give a score out of 10 and explain what would move it to the next band. Anchor the score to product logic and review readiness, not writing polish.

For large, cross-system, compliance-sensitive, or platform PRDs, split scoring when one overall score would be misleading:

- Product Logic Score: goal clarity, current-phase scope, main flow, business rules, user/ops outcome.
- Engineering Readiness Score: state matrix, ownership, source of truth, data/API readiness, exception handling, reconciliation, migration, rollout, audit.
- Governance / Compliance Readiness Score: legal/regulatory ownership, decision authority, approval gates, compliance signoff, audit requirements.
- Overall Score: weighted judgment based on the user's review goal.

Explain which dimension drives the lower score. Do not let missing RFC-level implementation details dominate the product logic score when product semantics are clear.

For artifact-specific calibration standards, read `references/review-readiness-rubric.md` when the PRD type is ambiguous, the score is contested, or the document is a short feature PRD, implementation note, migration PRD, configuration UI PRD, operational SOP, external integration PRD, or large 0-to-1 platform PRD.

## Audience Mode

Choose the output mode based on the user's request and likely audience.

PM-friendly review:

- Use when the document is early, written by a less technical PM, or the user asks for overall quality.
- Start with whether the product logic is understandable and what the next concrete fixes are.
- Translate technical gaps into business consequences.
- Avoid overwhelming the author with a long engineering checklist unless the risk is blocking.

Engineering readiness review:

- Use when the PRD is preparing for engineering review or implementation.
- Be strict about ownership, states, source of truth, business status meaning, data/API readiness, compatibility, migration, rollout, audit, and operational handling.
- Keep findings actionable enough for PM, engineering, QA, and ops to align on what must change.
- Put implementation-specific details into RFC follow-up unless they change product behavior or acceptance.

If the user asks for a score, give a score out of 10 only after judging product logic, business closure, and review readiness. Do not anchor the score to writing polish or RFC-level implementation detail.

## Product PRD / Engineering RFC Boundary

PRD should define:

- business semantics
- user/ops-visible result
- business meaning of status changes
- system responsibility boundary
- source of truth
- exception behavior and manual handling policy
- acceptance criteria

RFC or engineering design should define:

- exact API fields and error code list
- database schema
- idempotency implementation
- retry technical strategy
- concrete state-machine implementation
- storage, queue, job scheduling, monitoring, and alerting implementation

During review, point out when RFC must carry an item, but do not treat RFC-level details as PRD blocking items unless the missing decision affects business closure.

## Output Severity

Prefer product-review language over abstract severity labels:

- Fatal / blocking: product logic, core flow, source of truth, owner, or critical status/money/contract/approval result is broken or ambiguous.
- Must improve: product decision must be clarified before engineering can confidently implement.
- Nice to improve: clarity, structure, QA, acceptance, or future-phase improvement.
- RFC follow-up: engineering/design details that should be owned outside the PRD.
- Open questions: decisions or ownership confirmations still needed.

Use Critical/High/Medium/Low only if the user asks for severity labels or the team format requires them.

## Review Checklist

Check business and scope:

- Background states the real business pain and platform need.
- Goal matches current phase.
- `In Scope`, `Out of Scope`, `Not Supported in This Phase`, and `Future Iteration` are explicit.
- Future-phase content does not leak into current requirements.
- Explicit out-of-scope or future-phase statements override examples unless current-phase behavior still depends on the item.

Check ownership and boundaries:

- Actors/systems are listed.
- Decision-maker, source of truth, persistence owner, validation owner, pass-through system, operational owner, downstream consumer, callback/event owner, and status-transition owner are clear.
- System responsibilities do not overlap ambiguously.

Check flow completeness:

- Main flow is modeled before detailed prose.
- Creation, query, callback, update, timeout, retry, rollback, reconciliation, migration, and manual exception paths are covered when relevant.
- Persistence points and state changes are visible.
- If the main direction exists but testable combinations are missing, ask for a scenario matrix instead of calling the whole flow absent.

Check data model adequacy:

- Configuration objects and runtime objects are separated.
- Snapshot behavior is explicit.
- Dynamic resolution fields are not confused with final resolved values.
- Field naming reflects lifecycle and cardinality.
- UI/prototype needs can be supported by available data.

Check API and implementation readiness:

- API/data-field changes include field name, mandatory flag, example, description, owner system, and change type when needed.
- Error codes/messages, idempotency, optimistic locking, retry, and timeout behavior are defined where relevant.
- Downstream consumers have enough data to act.
- Missing API/error-code/storage/retry details are classified as RFC follow-up unless product semantics, status consistency, or acceptance depends on them.

Check operational reality:

- Reconciliation, settlement timing, audit logs, monitoring, exception queues, manual fallback, rollout, and support handling are addressed.
- Migration compatibility and old/new platform behavior are considered.
- Finance/ops ownership is clear for temporary manual work.

Check artifact consistency:

- The draft follows provided prototypes, existing PRD files, Jira/prototype links, and latest source material.
- Product taxonomy and system names are accurate.
- One-page documents are concise; full PRDs are complete.

Check PM accessibility:

- Missing technical concepts are translated into business questions the PM can answer.
- Feedback distinguishes "you must decide the business behavior" from "engineering should design the implementation."
- Review does not punish a simple PRD for lacking platform-level sections when the scope is genuinely simple.
- Wording distinguishes "not confirmed in readable text" from "not defined."

## Severity Guide

- Critical: blocks correct implementation, creates money/status/data inconsistency, or leaves ownership/source-of-truth unclear.
- High: creates major operational burden, edge-case failure, rollout risk, or scope leakage.
- Medium: makes review/implementation harder but has a clear local fix.
- Low: wording, formatting, or minor clarity improvement.

## Avoid

- Do not focus on wording before logic.
- Do not turn review into a full rewrite.
- Do not over-index on compliance unless the user frames the work as compliance-related.
- Do not infer personal traits from document style.
- Do not make `Issue / Why it matters / Affected area / Recommended handling` the default visual structure, though you may use those dimensions internally.
- Do not over-penalize a business PRD for missing RFC-level implementation detail.
- Do not prescribe API, database, queue, retry job, or monitoring implementation unless the user explicitly asks for engineering design.
- Do not overclaim with "not defined," "missing," "flow is not closed," or "blocking conflict" unless evidence has been checked across readable text, diagrams, tables, comments, screenshots, and linked sections where available.
- Do not treat an out-of-scope or regulatory-gated item as current-phase risk unless the current-phase flow requires it.

## Routing

- Route to `platform-prd-builder` when the user wants fixes rewritten into the PRD.
- Route to `platform-scope-checker` when the main issue is phase boundary or MVP size.
- Route to `platform-product-guide` when the business problem, platform direction, or ownership model needs reframing before review.
- Route RFC-level implementation detail to engineering follow-up while keeping product semantics in the PRD review.

## References

- `references/review-readiness-rubric.md`: load for artifact-specific completeness standards and readiness bands.
- `references/prd-vs-rfc-boundary.md`: load when review feedback risks mixing product PRD decisions with engineering RFC implementation details.
