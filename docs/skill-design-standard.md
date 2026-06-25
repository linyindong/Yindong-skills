# Yindong Skills Design Standard

This standard keeps Yindong-skills consistent as the library evolves.

## Core Rules

1. A skill is a workflow, not a long prompt.
2. Frontmatter should contain only `name` and `description`.
3. The `description` must include trigger conditions because it is the main discovery surface.
4. Every skill should define when to use it, when not to use it, operating modes, workflow, output contract, quality checklist, and routing.
5. Put detailed rubrics, templates, examples, and long checklists in `references/`.
6. Keep `SKILL.md` focused on execution behavior.
7. Avoid private system names and company-specific examples in public skills.
8. Separate product decisions from RFC or engineering implementation details.

## Recommended `SKILL.md` Structure

```md
---
name: skill-name
description: What this skill does. Use when...
---

# Skill Name

## Overview
## When NOT to Use
## Operating Modes
## First Move
## Workflow
## Output Contract
## Quality Checklist
## Routing
## Guardrails
## References
```

## Output Contract Pattern

Every product skill should tell the agent what shape the answer should take.

Default structure:

1. Conclusion or recommendation
2. Evidence / assumptions
3. Main analysis or artifact
4. Risks / tradeoffs
5. Open questions
6. Next step or routing target

Review skills should include readiness judgment.

Scope skills should include a verdict.

Builder skills should include the artifact structure.

Operating-system skills should include the selected mode and next collaboration path.

## Routing Pattern

Use the smallest useful skill first:

- Direction unclear: `yindong-product-operating-system`
- Ready to write: `yindong-prd-builder`
- Unsure whether to include something now: `yindong-scope-governor`
- Existing artifact needs assessment: `yindong-prd-reviewer`

Do not force every request into a full PRD.

## Quality Checklist for Skill Updates

Before finalizing any skill update, verify:

- [ ] Trigger description is clear.
- [ ] Non-use boundary is clear.
- [ ] Modes cover common request types.
- [ ] Workflow is executable.
- [ ] Output contract is visible.
- [ ] Quality checklist is present.
- [ ] Routing to adjacent skills is explicit.
- [ ] Detailed reference material is not duplicated unnecessarily in `SKILL.md`.

