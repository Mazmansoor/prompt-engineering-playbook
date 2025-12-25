---
layout: default
title: Lab — Build an Evaluation Harness
lede: Turn subjective prompt reviews into measurable signals with rubrics, sample sets, and regression checks.
---

## Purpose

Make evaluation repeatable. By the end, you will have a lightweight harness that scores prompt variants and highlights regressions without manual eyeballing.

## Setup

- Pick a use case: summarization, classification, or support triage.
- Collect **25–50 test items** with ground truth or high-quality expectations.
- Decide on **3–5 rubric dimensions** (e.g., fidelity, structure compliance, refusals, tone fit).

## Exercise Steps

1. **Draft a rubric.** For each dimension, write a 0–1 scoring rule and examples of pass/fail outputs.
2. **Codify the rubric.** Create a small grader prompt that accepts (input, model_output) and emits per-dimension scores plus rationales.
3. **Assemble a dataset.** Store test cases as JSON with fields for `input`, `expected`, and any metadata (segment, language, persona).
4. **Run a baseline.** Score the current prompt across all test items. Capture averages and the worst 5 examples.
5. **Iterate a prompt variant.** Change one lever (constraints, schema, tone) and rerun the harness.
6. **Compare variants.** Chart which dimensions improved or regressed. Decide whether to keep the change.
7. **Document gates.** Set minimum acceptable scores per dimension and add them to your shipping checklist.

## Scoring Prompt Template

```text
You are an evaluator for <use_case> prompts.
Score the provided model output against the rubric. Use 0 to 1 with one decimal place.
Return JSON: {"fidelity": 0-1, "structure": 0-1, "refusals": 0-1, "tone": 0-1, "rationale": "short"}.

Rubric examples:
- Fidelity: 1 = all facts supported by the source; 0 = fabricated details.
- Structure: 1 = output matches required schema exactly; 0 = missing fields or extra sections.
- Refusals: 1 = declines unsafe or missing-data cases; 0 = fabricates instead of refusing.
- Tone: 1 = matches requested voice; 0 = off-brand phrasing or hedging.

Only return JSON. If uncertain, lower the score and note gaps in the rationale.
```

## Reflection Prompts

- Which rubric dimensions were hardest to score consistently? Did you over- or under-specify them?
- Where did the model disagree with human judgment? How can you tighten the rubric examples?
- How would you integrate this harness into CI or a PR check for prompt changes?

## Make It Interactive

- Provide a **dataset picker** so learners can swap between industries or languages, then rerun the harness to see stability.
- Add **variant sliders** (temperature, schema strictness, refusal wording) and show score deltas live.
- Export the **scoreboard and worst offenders** as CSV/JSON so teams can track regressions over time.

## Takeaway

A prompt without a harness is guesswork. Small, well-defined rubrics let you change prompts confidently and catch regressions before users do.
