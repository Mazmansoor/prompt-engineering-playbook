---
layout: default
title: Advanced — Tool-Using Prompts
lede: Modern models can plan and call tools, but they only succeed when the prompt defines boundaries and accountability.
---

## Guardrails to Include

- **Tool manifest.** Inputs, outputs, failure modes, and cost/latency expectations.
- **Decision policy.** When to call a tool versus respond directly; how to handle partial data.
- **Budget awareness.** Max calls, expected runtime, and what to do when limits are hit.
- **Fallback behavior.** Report failures, salvage partial results, and request next steps.
- **Audit trail.** Require call summaries so humans can review what happened.

## Minimal Skeleton

```
You can call the following tools:
- search(query): retrieves recent information
- db_lookup(id): returns structured records

Use tools only when you lack the data to answer confidently.
If a tool fails, report the failure and continue with best-effort reasoning.
Always show your working notes before the final answer.
Stop after 3 tool calls unless new evidence appears.
```

## Debugging Tips

- Add a short **pre-plan** section: "List the steps you will take before acting." 
- Request **call summaries**: "After each tool call, summarize what you learned."
- Enforce **stop conditions**: "Do not exceed three tool calls without new evidence."
- Require **confidence and gaps**: "Rate your confidence 0-1 and name the missing data."

## Signs of Quality

- The model justifies why a tool is or is not used
- Tool inputs mirror the user request, not hallucinated parameters
- Failures are surfaced with next steps, not hidden
- There is a clear audit trail of reasoning and tool effects

## Implementation Pattern: Investigation Agent

```
You are an investigation agent responsible for gathering reliable evidence.

## Objective
Produce a concise incident brief for leadership.

## Tools
- timeline(entity): fetches ordered events
- dossier(entity): returns structured facts

## Rules
- Plan before calling tools. Show the plan as a bullet list.
- After each tool call, summarize what changed.
- If a tool fails, note the error and continue with other tools.
- Stop after 2 calls per tool unless new evidence appears.

## Output
Return a markdown table with columns: signal, evidence, confidence (0-1), follow_up.
If confidence < 0.7 for any row, propose the next tool or data needed.
```

## Shipping Checklist

- [ ] Tool manifest includes inputs, outputs, and limits
- [ ] Decision and fallback policies are explicit
- [ ] Model is required to show reasoning and confidence
- [ ] Stop conditions prevent infinite tool loops
