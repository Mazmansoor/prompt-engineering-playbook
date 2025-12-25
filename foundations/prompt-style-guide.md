---
layout: default
title: Prompt Style Guide
lede: House rules for writing prompts that stay readable, auditable, and production-friendly.
---

## Core Principles

- **Prefer explicit roles.** Bad: “Write an analysis.” Better: “Act as a policy analyst evaluating…”
- **Declare constraints early.** Length, format, assumptions, uncertainty, and refusal conditions.
- **Separate task from context.** Keep instructions out of narrative background text.
- **Force structure in outputs.** Lists, tables, schemas reduce ambiguity and make evaluation simple.
- **Anticipate failure.** Ask for uncertainty, limits, references, and alternative actions.

## Standard Prompt Sections

1. **Role** — who the system is acting as and what authority it has.
2. **Task** — the explicit deliverable, framed as an outcome not an action.
3. **Context** — only the inputs that matter; avoid noise.
4. **Constraints** — scope, safety requirements, allowed/blocked behaviors.
5. **Output Shape** — schema, ordering, and formatting rules.
6. **Evaluation** — acceptance criteria, refusal policy, and when to escalate.

## Formatting Conventions

- Use headings or separators (`## Task`, `## Constraints`) when prompts get long.
- Keep examples distinct from live inputs. Label them `EXAMPLE` vs `LIVE INPUT`.
- Use bullet lists for constraints and fields. Models follow explicit lists better than prose.
- Prefer ISO-like conventions for dates, numbers, and IDs to avoid locale variance.

## Voice and Tone

- Be direct, not chatty. The model is executing policy, not role-playing unless specified.
- State uncertainty policies: “If confidence < 0.7, flag and provide next steps.”
- In safety-critical contexts, instruct the model to refuse gracefully and cite why.

## Presentation and Experience Standards

- Pair prompts with **display presets**: teaching mode (show rationale), delivery mode (hide scaffolding), and audit mode (surface acceptance criteria and references).
- Define **design tokens** for accent color, surface color, spacing, and typography scale so a future settings page can re-skin the playbook without rewriting content.
- Include **accessibility defaults**: minimum 16px body text, focus outlines, high-contrast links, and alt text rules for any generated visuals.
- Offer **export hooks**: every pattern and template should be downloadable as JSON/Markdown bundles for client handoff.

## Quality Gates

- Add a brief **self-review** step: before the final answer, list assumptions, missing data, and confidence.
- Restate **acceptance criteria** in the prompt so the model echoes the success conditions before responding.
- Require **format validation**: instruct the model to check for empty fields or schema mismatches.
- Preserve an **audit trail**: capture rationale, source references, and recommended follow-ups for each response.

## Example Template

```
You are [role] with the mandate to [responsibility].

## Task
[Deliverable and boundaries]

## Inputs
- [Key data elements or references]

## Constraints
- [Safety, compliance, budget, latency]

## Output
Return [format/schema]. If data is missing, state "unknown" explicitly. Include rationale.

## Quality Checks
- Validate fields before final output.
- Flag low confidence and propose next steps.
```

## Ready-to-Ship Checklist

- [ ] Role and task are unambiguous and non-overlapping.
- [ ] Context is scoped to what the model truly needs.
- [ ] Constraints cover safety, formatting, and refusal behavior.
- [ ] Output format is parseable and ordered.
- [ ] Evaluation criteria are explicit enough for another reviewer to audit.
- [ ] Presentation mode (teaching/delivery/audit) is defined, with a path to export tokens for a future settings panel.
