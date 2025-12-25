---
layout: default
title: Pattern — Structured Outputs
lede: When you need consistency, ask for it explicitly. Structured outputs reduce ambiguity and make automation practical.
---

## When to Use

- Downstream systems must parse the response
- Multiple audiences need the same shape of information
- You are evaluating multiple model runs side-by-side
- You need auditability and diff-friendly outputs

## Core Template

```
You are [role]. Produce output in [format].
Include: [required fields].
Avoid: [irrelevant content or speculation].
Validate that each field is filled before responding.
If data is missing, state "unknown" rather than guessing.
```

## Why It Works

- Forces the model to map reasoning into named slots
- Makes missing data visible instead of hidden in prose
- Simplifies evaluation: you can diff or parse the fields
- Enables guardrails: reject responses that break schema

## Example: Research Summary

```
You are a product manager summarizing user interviews.
Return a JSON array of findings with keys: "theme", "quote", "evidence", "risk".
Avoid speculation or invented quotes.
If a theme lacks a direct quote, mark the quote as "unknown" and add a risk note.
Validate each object for all keys before final output.
```

## Variations

- **Tables for humans.** Markdown tables with fixed columns for fast review.
- **Optional fields.** Use `null` or `"unknown"` instead of omission to reveal gaps.
- **Parser mode.** "Only respond with valid JSON" when paired with a strict parser.
- **Scoring blocks.** Include numeric ratings with definitions to standardize interpretation.

## Implementation Tips

- Prepend a short **schema definition** so the model can self-check.
- Require a **verification step**: "List any fields you cannot populate and why."
- Keep field names short and descriptive; avoid nested objects unless necessary.
- Pair with automated validation to catch drift early.

## Experience Hooks to Build

- **Schema switcher.** Allow readers to toggle between JSON, table, and CSV schema definitions so they can pick the shape that best fits their downstream stack.
- **Field glossary drawer.** Right-rail that defines each field with examples, antipatterns, and failure cases to reduce ambiguity when teams adapt templates.
- **Downloadable contracts.** Buttons that export the schema as JSON Schema or Markdown for QA sign-off, matching the planned settings page export behavior.
- **Diff view.** Example section that shows before/after outputs to illustrate how structured prompts reduce variance compared to freeform answers.

## Quality Checklist

- [ ] Output is parseable on first pass
- [ ] Missing data is explicit, not implied
- [ ] No speculative fields or hallucinated specifics
- [ ] Schema and field order remain stable across runs
