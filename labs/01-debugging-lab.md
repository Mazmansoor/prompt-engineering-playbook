---
layout: default
title: Lab — Debug a Weak Prompt
lede: Learn a repeatable debugging loop instead of trial and error. Tighten feedback, document fixes, and ship safer prompts.
---

## Purpose

Teach a disciplined debug loop you can reuse across products. The goal is to make failure modes visible and fixable.

## Setup

Use any model. Start with this flawed prompt:

```
"Summarize this article and extract key quotes."
```

Expected issues:

- Missing context, role, and format
- High variance in tone and length
- Quotes may be fabricated

## Exercise Steps

1. **Run the prompt as-is.** Capture the output and note failure modes.
2. **Add explicit constraints.** Specify role, length, and citation format.
3. **Add evaluation criteria.** Ask the model to flag uncertain or unsupported claims.
4. **Compare outputs.** Which failures disappeared? Which remain?
5. **Write a short retro.** Document the changes that produced the biggest improvement.

## Upgrade Template

```
You are an evidence-focused analyst.
Summarize the article in 5 bullet points.
Return a table with columns: claim, quote, source_location, confidence (0-1).
If you cannot find a direct quote, mark quote as "unknown" and lower confidence.
Flag any speculation and propose a follow-up check.
```

## Reflection Prompts

- How did adding an output schema change the model’s reasoning?
- Which failures remained even after constraints? What data was missing?
- How would you automate evaluation for this task?
- Which fixes should be codified as reusable snippets or presets for similar prompts?

## Takeaway

Debugging is about tightening feedback loops, not guessing better wording. Ship prompts with evidence, structure, and refusal policies baked in.

## Operational Add-Ons

- Add a **failure log** that captures the original input, bad output, and the exact fix applied so teams can reuse repairs.
- Pair the lab with a **scoring harness** (see the evaluation lab) and promote fixes only when scores improve on regression cases.
- Wire an **observability hook** that emits events for constraints triggered, refusals issued, and schema violations to feed dashboards.

## Make It Interactive

- Add an **inline diff** that highlights changes between baseline and improved prompts so learners see exactly what reduced variance.
- Build a **settings pane** for the lab that lets people toggle model temperature, schema strictness, and refusal policies, then shows how each change affects outputs.
- Offer **downloadable lab packs** (inputs, prompts, expected outputs) so teams can rerun the exercises in their own pipelines or demos.
