---
layout: default
title: What Is a Prompt?
lede: Prompts are configuration layers that direct attention, scope, safety, and evaluation—not casual questions.
cta_label: View Style Guide
cta_target: /foundations/prompt-style-guide
---

## The Core Frame

A prompt is a **control surface** that configures model behavior. It shapes:

- What the system attends to
- How it reasons and what it ignores
- The guardrails that constrain outputs
- How success is measured

Treat it like a product spec, not a message.

## The Core Misunderstanding

Most teams treat prompts as clever wording. In reality, prompts are **configurations** that set:

- **Role** — who the system acts as
- **Task** — the outcome to produce
- **Context** — the inputs that matter
- **Constraints** — the bounds and exclusions
- **Evaluation** — what success and failure look like

Miss one, and failure is likely.

## A Minimal Prompt Skeleton

Every effective prompt answers five questions:

1. Who is the system acting as?
2. What is the task?
3. What context matters?
4. What constraints apply?
5. What does success look like?

Put these upfront. Avoid burying them in background text.

## Practical Guidance

- **Prefer explicitness.** Name roles, formats, and limits.
- **Separate task from context.** Do not hide instructions inside narrative prose.
- **Model failure.** Ask for uncertainty, missing data, and next steps.
- **Make outputs auditable.** Favor tables, schemas, and cited evidence.

## Before You Move On

- Draft a prompt using the five-part skeleton.
- Identify the highest-risk failure mode (hallucination, formatting, safety) and state how it should be handled.
- Add an evaluation line: what should the model refuse or flag as low confidence?
