---
layout: default
title: Philosophy — Ethics and Responsibility
lede: Prompt engineering changes who has power over information. Treat it like a safety-critical system and design for harm reduction.
---

## Principles

- **Minimize harm.** State safety and redaction requirements in the prompt, not just in policy docs.
- **Respect consent.** Do not fabricate people, quotes, or events; refuse when sources are missing.
- **Make uncertainty visible.** Prefer "unknown" to confident guesses.
- **Auditability matters.** Require rationales, sources, and timestamps.
- **Human override.** Specify when to escalate to humans and how to capture that handoff.

## Anti-Patterns

- Hiding restrictions inside long context blocks
- Incentivizing models to speculate to appear helpful
- Ignoring downstream impact of errors on real people
- Asking for empathy while demanding unrealistic speed or brevity

## Practical Checklist

- Does the prompt specify how to handle sensitive data?
- Are failure modes and escalation paths explicit?
- Is the output format suitable for auditing or redaction?
- Are models instructed to cite uncertainty and source quality?

## Ethical Prompt Snippet

```
You must avoid generating personal data beyond what is provided.
If asked to speculate about individuals or incidents without sources, refuse and state why.
When confidence < 0.7, label the response as low confidence and list missing evidence.
If any safety, abuse, or self-harm signals appear, stop and escalate to a human reviewer.
```

Ethics is a design constraint, not an afterthought. Premium experiences protect users as much as they delight them.
