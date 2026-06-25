# Top Agent Skills Repository Best Practices

Date: 2026-06-25

## 1. Research Scope

This analysis compares 30 public GitHub repositories that contain `SKILL.md` files and are highly visible in agent-skills related searches.

The goal is not to copy prompts. The goal is to extract repository-level and skill-level design conventions that appear repeatedly across mature skill libraries.

Method:

- Selected 30 repositories from GitHub search candidates that contain `SKILL.md`, ranked by current GitHub `stargazers_count`.
- Sparse-downloaded only skill-related files: `SKILL.md`, `README*`, `AGENTS.md`, `CLAUDE.md`, templates, examples, and adjacent docs.
- Analyzed 9,002 `SKILL.md` files.
- Counted both file-level frequency and repo-level presence to avoid over-weighting very large generated libraries.

Important limitation:

- GitHub search ranking and star counts are volatile, and some repositories include large duplicated or generated skill collections. The recommendations below therefore weigh repeated structural patterns more heavily than raw file counts.

## 2. Sample Summary

| Metric | Result |
| --- | ---: |
| Repositories analyzed | 30 |
| `SKILL.md` files analyzed | 9,002 |
| Repositories with top-level `skills/` | 18 / 30 |
| Repositories with docs | 11 / 30 |
| Repositories with plugin packaging | 9 / 30 |
| Repositories with examples | 5 / 30 |
| Repositories with tests/evals | 5 / 30 tests, 2 / 30 evals |

Representative mature references included:

- `product-on-purpose/pm-skills`: product lifecycle skills, workflow commands, samples, generated catalog, and CI quality gates.
- `addyosmani/agent-skills`: lifecycle-oriented engineering skills with quality gates, anti-rationalization patterns, and reference checklists.
- `anthropics/skills`: official-style skill anatomy and progressive disclosure conventions.
- `github/awesome-copilot`, `VoltAgent/awesome-agent-skills`, and similar curated collections: useful for taxonomy and discoverability patterns.

Primary public sources:

- [product-on-purpose/pm-skills](https://github.com/product-on-purpose/pm-skills)
- [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills)
- [anthropics/skills](https://github.com/anthropics/skills)
- [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)
- [eigent-ai/agent-skills](https://github.com/eigent-ai/agent-skills)
- [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills)
- [github/awesome-copilot](https://github.com/github/awesome-copilot)

Top-30 sample repository list:

| # | Repository | `SKILL.md` files |
| ---: | --- | ---: |
| 1 | [obra/superpowers](https://github.com/obra/superpowers) | 14 |
| 2 | [affaan-m/ECC](https://github.com/affaan-m/ECC) | 881 |
| 3 | [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) | 1 |
| 4 | [anthropics/skills](https://github.com/anthropics/skills) | 18 |
| 5 | [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | 7 |
| 6 | [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | 11 |
| 7 | [nexu-io/open-design](https://github.com/nexu-io/open-design) | 521 |
| 8 | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | 24 |
| 9 | [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) | 864 |
| 10 | [ruvnet/ruflo](https://github.com/ruvnet/ruflo) | 340 |
| 11 | [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | 13 |
| 12 | [santifer/career-ops](https://github.com/santifer/career-ops) | 5 |
| 13 | [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) | 13 |
| 14 | [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | 14 |
| 15 | [mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill) | 1 |
| 16 | [zhayujie/CowAgent](https://github.com/zhayujie/CowAgent) | 3 |
| 17 | [sickn33/antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) | 5,385 |
| 18 | [danny-avila/LibreChat](https://github.com/danny-avila/LibreChat) | 1 |
| 19 | [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) | 5 |
| 20 | [multica-ai/multica](https://github.com/multica-ai/multica) | 9 |
| 21 | [wshobson/agents](https://github.com/wshobson/agents) | 158 |
| 22 | [github/awesome-copilot](https://github.com/github/awesome-copilot) | 381 |
| 23 | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | 45 |
| 24 | [Imbad0202/academic-research-skills](https://github.com/Imbad0202/academic-research-skills) | 4 |
| 25 | [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | 29 |
| 26 | [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | 147 |
| 27 | [iOfficeAI/AionUi](https://github.com/iOfficeAI/AionUi) | 4 |
| 28 | [googleworkspace/cli](https://github.com/googleworkspace/cli) | 95 |
| 29 | [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | 9 |
| 30 | [blader/humanizer](https://github.com/blader/humanizer) | 1 |

## 3. Common Repository Anatomy

Most mature repositories separate four concerns:

| Directory / File | Common Purpose | Repo Presence |
| --- | --- | ---: |
| `skills/` | One folder per skill, each containing `SKILL.md` | 18 / 30 |
| `docs/` | Installation, usage, architecture, contribution docs | 11 / 30 |
| `plugins/`, `.claude-plugin`, `.codex-plugin` | Agent/plugin packaging | 9 / 30 plugin-style dirs |
| `.claude/`, `.codex/`, `.github/` | Agent-specific integration surfaces | 8 / 30 `.claude`, 4 / 30 `.github` |
| `examples/` | Example outputs or example usage | 5 / 30 |
| `tests/`, `evals/` | Regression checks, routing checks, output quality checks | 5 / 30 tests, 2 / 30 evals |
| `scripts/`, `tools/`, `bin/` | Validation, sync, catalog generation, install helpers | 2-3 / 30 |
| `assets/`, `references/`, `templates/` | Progressive disclosure resources loaded only when needed | 2-5 / 30 |
| `README.md` | Catalog, installation, usage routing, contribution rules | nearly universal |
| `AGENTS.md`, `CLAUDE.md` | Agent-facing catalog or repo operating instructions | common in mature multi-agent repos |

Best-practice repository shape:

```text
repo/
  README.md
  LICENSE
  skill-manifest.json            # optional generated catalog
  AGENTS.md                      # optional agent-facing index
  docs/
    install.md
    skill-authoring.md
    evaluation.md
  skills/
    skill-name/
      SKILL.md
      references/                # optional
      templates/                 # optional
      examples/                  # optional
      scripts/                   # optional
  tests/                         # optional but mature
  evals/                         # optional but mature
```

## 4. Common `SKILL.md` Sections

Repo-level presence across the 30 repositories:

| Section Pattern | Repo Presence | Interpretation |
| --- | ---: | --- |
| Overview / Summary / Purpose | 30 / 30 | Every skill needs a short mental model. |
| Modes / Variants / Scenario Paths | 29 / 30 | Mature skills route different request types differently. |
| Metadata / Frontmatter | 29 / 30 | Discovery depends on structured metadata. |
| Guardrails / Rules / Always-Never | 28 / 30 | Good skills constrain behavior, not only describe it. |
| Workflow / Process / Instructions | 27 / 30 | Skills should be executable workflows. |
| When to Use / Trigger Conditions | 27 / 30 | Activation clarity is core. |
| References / Resources | 27 / 30 | Mature skills use progressive disclosure. |
| Quality Checklist / Verification | 26 / 30 | Skills need exit criteria. |
| Examples / Samples | 26 / 30 | Examples make quality visible. |
| Output Format / Output Contract | 25 / 30 | Mature skills define expected deliverables. |
| Inputs / Prerequisites | 24 / 30 | Useful for reducing clarification churn. |
| Troubleshooting / Fallback | 24 / 30 | Mature skills handle incomplete context. |
| When NOT to Use | 16 / 30 | Less universal, but very valuable for boundary control. |

Recommended fixed structure for high-quality product skills:

```md
---
name: skill-name
description: Clear trigger description. Use when...
category: product / review / scope / strategy
version: x.y.z
---

# Skill Name

## Overview
## When to Use
## When NOT to Use
## Required Inputs
## Workflow
## Output Contract
## Quality Checklist
## Guardrails
## Examples
## References
## Fallbacks
```

Not every skill needs every section, but mature skills usually include the first eight.

## 5. Highest-Frequency Fields

Across 9,002 files, the most common frontmatter fields were:

| Field | Count | Recommendation |
| --- | ---: | --- |
| `name` | 8,993 | Required. Keep stable and lowercase-hyphenated. |
| `description` | 8,993 | Required. Include trigger conditions, not just summary. |
| `tags` | 903 | Useful for search and catalog browsing. |
| `author` | 878 | Useful for attribution in public repos. |
| `requires` | 837 | Useful when a skill depends on tools, references, or another skill. |
| `metadata` | 824 | Useful for category, phase, domain, maturity. |
| `category` | 790 | Important for repo navigation. |
| `tools` / `allowed-tools` | 1,127 combined | Important when skills use external tools. |
| `license` | 710 | Useful for public reuse. |
| `version` | 264 | Useful once skills are shared and updated. |

Recommended field set for Yindong-skills:

```yaml
---
name: yindong-prd-reviewer
description: Review PRDs with product-logic-first judgment. Use when...
category: product-management
domain: fintech-platform
version: 0.2.0
tags:
  - prd
  - product-review
  - scope
  - platform
---
```

Keep the required frontmatter short. Put nuanced logic in the body, not in metadata.

## 6. Workflow Maturity Signals

File-level workflow signals:

| Signal | Count | Meaning |
| --- | ---: | --- |
| Validation loop | 7,802 | Mature skills ask the agent to verify outputs. |
| Evidence / assumptions | 6,965 | Strong skills separate known facts from inference. |
| Numbered phases | 6,584 | Mature workflows are staged. |
| Mode routing | 5,339 | Good skills adapt to request type. |
| Examples | 5,066 | Examples reduce ambiguity. |
| Artifact templates | 4,661 | Output quality improves when shape is explicit. |
| Explicit gates / verdicts | 2,454 | High-risk work benefits from stop/go decisions. |
| External references | 2,403 | Progressive disclosure keeps `SKILL.md` compact. |
| Fallbacks | 1,197 | Less frequent, but important for robustness. |

The most mature workflows share six patterns:

1. Clear trigger and boundary
2. Input normalization before execution
3. Mode-based routing
4. Step-by-step workflow
5. Verification or quality gate
6. Next-step routing

For product-management skills, this becomes:

```text
Classify request
→ Normalize inputs
→ Choose mode
→ Produce artifact / review / scope decision
→ Run quality checklist
→ Route to next skill or next human decision
```

## 7. Output Contract Maturity

File-level output signals:

| Signal | Count | Meaning |
| --- | ---: | --- |
| Ordered sections | 7,203 | Most mature skills prescribe response structure. |
| Tables / JSON / YAML / schema | 6,584 | Structured output helps downstream reuse. |
| Examples | 5,066 | Examples anchor expected quality. |
| Template blocks | 4,873 | Templates reduce variance. |
| Severity / score / readiness | 2,409 | Useful for reviews and decision support. |
| Routing / next step | 1,431 | Good skills tell the user what to do next. |
| Named output contract section | 1,273 | Still not universal, but high value. |
| Quality / acceptance criteria | 201 | Underused; should be strengthened. |

Best-practice output contract:

```md
## Output Contract

Default response should include:

1. Executive / product-level conclusion
2. Key findings or decisions
3. Evidence / assumptions
4. Recommended action
5. Risks / tradeoffs
6. Open questions
7. Next routing target
```

For review skills, add:

```md
Readiness:
- Ready
- Mostly ready with product fixes
- Not ready; product logic blocked
- Needs discovery / scope decision first
```

For build/document skills, add:

```md
Artifact must include:
- Goal
- Scope
- Actors / systems
- Main flow
- Edge cases
- Data / API impact, if relevant
- Operations / rollout
- Open questions
```

## 8. Common Design Patterns

### 8.1 Progressive Disclosure

Pattern:

- Keep `SKILL.md` concise.
- Put deep references, examples, scripts, templates, and checklists in adjacent folders.
- Load only the files needed for the current task.

Why it matters:

- Prevents huge skills from crowding the context.
- Makes the skill easier to maintain.
- Allows domain-specific references without forcing every run to read them.

Yindong-skills implication:

- Keep the four core skills compact.
- Move examples, PRD templates, review rubrics, and artifact samples into `references/`.

### 8.2 Router Skill / Operating System Skill

Pattern:

- Mature repos often include a meta-skill or command that routes the user to the right specialized skill.
- The router describes when to use each skill and what the next step should be.

Yindong-skills implication:

- `yindong-product-operating-system` should remain the router and collaboration logic layer.
- README should repeat the simple routing rule:
  - Not sure about direction: use product-operating-system
  - Ready to write: use prd-builder
  - Unsure about scope: use scope-governor
  - Document ready to check: use prd-reviewer

### 8.3 Mode-Based Execution

Pattern:

- Strong skills do not treat all requests the same.
- They define modes such as quick review, deep review, MVP scope split, full PRD build, or decision memo.

Yindong-skills implication:

- Each skill should expose 2-4 modes.
- The agent should infer the mode from the request, then state it briefly.

### 8.4 Evidence and Assumption Ledger

Pattern:

- Mature skills separate evidence, assumptions, and recommendations.
- Especially common in research, review, and risk-gate skills.

Yindong-skills implication:

- Product decisions should not sound certain when the document does not support certainty.
- Reviews should label inferred risk vs explicit PRD gap.

### 8.5 Quality Gates

Pattern:

- Strong skills end with verification.
- Some mature repos include tests, evals, generated catalogs, or CI checks.

Yindong-skills implication:

- Add a lightweight skill-quality checklist:
  - Has clear trigger
  - Has non-use boundary
  - Has workflow
  - Has output contract
  - Has quality checklist
  - Has next-skill routing

### 8.6 Boundary Pointers

Pattern:

- Good skill libraries make adjacent skills aware of each other.
- Example: PRD builder should know when to route to scope governor; reviewer should know when to route back to builder.

Yindong-skills implication:

- Each skill should include:
  - When to use this skill
  - When not to use this skill
  - Which Yindong skill to use instead

### 8.7 Public Repo Discoverability

Pattern:

- Public skill repos that are easier to try have clear README routing, install instructions, skill catalog, examples, license, and topics.

Yindong-skills implication:

- Improve GitHub discoverability using:
  - English README first, Chinese second
  - Short “Which skill should I use?” section
  - GitHub topics: `agent-skills`, `codex-skills`, `product-management`, `prd`, `fintech`, `platform-product`
  - Examples without private system names
  - Clear license

## 9. Best-Practice Standard for Yindong-skills

### 9.1 Repository-Level Standard

Recommended next shape:

```text
yindong-codex-skills/
  README.md
  LICENSE
  docs/
    top-agent-skills-repository-best-practices.md
    skill-design-standard.md
  skills/
    yindong-product-operating-system/
      SKILL.md
      references/
    yindong-prd-builder/
      SKILL.md
      references/
        prd-output-contract.md
        prd-quality-checklist.md
    yindong-prd-reviewer/
      SKILL.md
      references/
        review-readiness-rubric.md
        prd-vs-rfc-boundary.md
    yindong-scope-governor/
      SKILL.md
      references/
        scope-decision-rubric.md
        phase-split-examples.md
```

### 9.2 Skill-Level Standard

Each Yindong skill should include:

```md
## Overview
## When to Use
## When NOT to Use
## Input Normalization
## Modes
## Workflow
## Output Contract
## Quality Checklist
## Routing
```

Optional sections:

- `Evidence and Assumption Handling`
- `Common Failure Modes`
- `Examples`
- `References`

### 9.3 Product-Specific Standard

For product, platform, and fintech-facing skills, add these decision dimensions:

- Business problem
- Platform capability
- Ownership / source of truth
- Flow closure
- Runtime object
- State consistency
- Scope boundary
- Operational fallback
- Audit / reconciliation / traceability
- Rollout and dependency risk

But the skill should still distinguish:

- Product PRD decisions
- RFC / engineering follow-up details
- Operational readiness
- Future phase expansion

## 10. Recommended Updates to the Four Current Skills

### 10.1 `yindong-product-operating-system`

Add or strengthen:

- Router behavior as first-class responsibility.
- Canonical-source and audience-projection pattern.
- Mode selection: direction framing, decision support, governance review, artifact routing.
- Explicit “do not generate a document before the business problem and boundary are clear.”

### 10.2 `yindong-prd-builder`

Add or strengthen:

- Required input normalization.
- Output contract with strict PRD section order.
- Quality checklist before final answer.
- Reference templates for short feature PRD vs complex platform PRD.
- Routing back to scope-governor when MVP boundary is unclear.

### 10.3 `yindong-scope-governor`

Add or strengthen:

- Verdict model:
  - Include in MVP
  - Include but simplify
  - Validate first
  - Move to future phase
  - Reject / do not build
- Demand/evidence check before accepting scope expansion.
- Change-impact matrix across UI, workflow, object, API, operations, rollout.
- Next-step routing to PRD builder or product-operating-system.

### 10.4 `yindong-prd-reviewer`

Add or strengthen:

- Product-logic-first review before engineering checklist.
- Readiness ladder and scoring.
- PRD vs RFC boundary.
- Evidence-confidence labels.
- “Must fix” vs “RFC follow-up” separation.
- Mode selection for small feature PRD vs large 0-to-1 platform PRD.

## 11. Practical Design Rules

1. A skill is a workflow, not a long prompt.
2. The `description` field is the most important trigger surface.
3. Every skill needs a boundary: when to use, when not to use, and what to use instead.
4. Every mature skill needs an output contract.
5. Reviews need readiness judgment, not only issue lists.
6. Scope skills need verdicts, not vague tradeoff narration.
7. Builder skills need templates, but should avoid overfitting to one company or one system.
8. Public skills should avoid private system names, private examples, and overly personal collaboration assumptions.
9. References should be loaded progressively, not embedded into every `SKILL.md`.
10. Skill libraries should include examples and quality checks if they want outside users to trust them.

## 12. Suggested Next Step

Create a lightweight `docs/skill-design-standard.md`, then refactor the four current skills against that standard.

Priority order:

1. Normalize frontmatter and README discoverability.
2. Add explicit modes and routing to each skill.
3. Move large rubrics into `references/`.
4. Add review/scope/builder output contracts as reference files.
5. Add a small validation checklist for future skill updates.
