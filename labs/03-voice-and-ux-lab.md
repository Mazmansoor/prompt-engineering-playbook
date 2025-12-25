---
layout: default
title: Lab — Brand Voice and UX Guardrails
lede: Stress-test tone, clarity, and refusal behavior so prompts feel on-brand and safe across audiences.
---

## Purpose

Design prompts that stay on-brand even when users push edge cases. This lab uses persona toggles and refusal policies to keep outputs consistent across audiences.

## Setup

- Define **two target personas** (e.g., executive summary vs. developer deep-dive).
- Write **brand guardrails**: voice adjectives, banned phrases, and required disclaimers.
- Collect **tricky inputs**: ambiguous requests, unsafe topics, and multilingual variants.

## Exercise Steps

1. **Draft a base prompt** with role, tone, and refusal rules. Include a table schema for clarity.
2. **Create persona overlays** that adjust tone and detail without changing safety rules.
3. **Run both personas** against the same tricky inputs. Log where tone or safety drifts.
4. **Tighten controls**: add banned-phrase filters, explicit reading level, and refusal wording.
5. **Add a mini evaluator** that checks tone and safety separately from task accuracy.
6. **Document the safe defaults** and what can be changed via settings without breaking the brand.

## Base Prompt Skeleton

```text
You are a <brand> communications lead.
Tone: calm, direct, confident. Avoid hype. Reading level: Grade 9–10.
Refusals: decline unsafe or speculative requests; state what evidence is missing.
Return a table with columns: audience, summary, risks, next_steps, refusal_triggered (true/false).
```

## Persona Overlays

```text
[Executive]
- Summaries <= 120 words.
- Emphasize business impact and decision-ready recommendations.
- Add a one-line risk disclaimer at the end.

[Developer]
- Include concrete API fields, error codes, and log hints.
- Note any assumptions; ask for missing inputs.
- Keep tone concise and peer-to-peer.
```

## Reflection Prompts

- Which persona drifted off-brand first? What wording anchored it better?
- Did refusals stay consistent across personas? Where did they over- or under-trigger?
- How could a settings page expose safe toggles (tone, verbosity) without letting users weaken safety rules?

## Make It Interactive

- Add **persona toggle buttons** that rerun the prompt and show diffs on tone, length, and refusal behavior.
- Let users **edit banned phrases** and see how that changes outputs on the tricky inputs.
- Include a **downloadable brand kit** (voice rules, overlays, refusal policy) for teams to import into their own systems.

## Takeaway

Brand voice is a safety control, not decoration. Treat tone, refusals, and overlays as configurable but safeguarded levers.
