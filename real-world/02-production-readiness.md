---
layout: default
title: Real-World — Production Launch Checklist
lede: Ship prompts like you ship software: with defined gates, telemetry, and rollback plans. Use this checklist to turn a polished prompt into a production-ready service.
---

## Goals

- Reduce launch risk with explicit gates and owners
- Keep behavior observable with logs, metrics, and reproducible prompts
- Provide rollback, redaction, and escalation plans before traffic arrives

## Non-Negotiables

- **Versioned prompts.** Store the exact prompt, schema, and defaults with a semantic version and changelog entry.
- **Guardrails.** Include refusals, missing-data handling, and timeouts so the system fails closed.
- **Redaction.** Remove PII before prompts are stored or sent to third parties; document what is redacted and why.
- **Human-in-the-loop.** Define thresholds for auto-approval vs. human review with escalation owners.

## Pre-Flight Design Checklist

- [ ] Inputs and outputs are validated against a schema
- [ ] Safety refusals and tone guidance are present for risky domains
- [ ] Tool calls or function manifests include budgets, retry, and fallback behavior
- [ ] Prompt includes a short rationale for auditable decisions
- [ ] Acceptance criteria are written as bullet points the model can restate

## Evaluation Gates

Run a small harness before every launch and after prompt edits.

- **Dataset.** 20–50 anonymized examples with clear expected outcomes.
- **Rubric.** Scoring prompt with criteria for correctness, safety, and tone.
- **Thresholds.** Minimum scores per criterion; failing prompts are blocked from deploy.
- **Regression log.** Track variants, scores, and fixes so you can explain changes to stakeholders.

## Observability Kit

- **Structured logs.** Capture input IDs, model version, prompt version, latency, and decision rationale.
- **Metrics.** Dashboards for success rate, refusal rate, escalation rate, and P50/P95 latency.
- **Drift checks.** Weekly trend views for rubric scores and category precision/recall where applicable.
- **Alerting.** Page on-call when critical categories dip below thresholds or latency exceeds SLOs.

## Runbook Snapshot

Use this skeleton to keep operations repeatable.

```markdown
# Prompt Launch Runbook

## Owners
- PM: <name/contact>
- Eng: <name/contact>
- On-call: <name/contact>

## Deploy Steps
1. Pull latest prompt version and schema
2. Run evaluation harness and log results
3. Toggle canary traffic to 5% and watch metrics for 30 minutes
4. Promote to 100% if thresholds hold; otherwise rollback prompt version

## Rollback
- Revert to prompt version X.Y.Z
- Clear caches and retry failed messages
- Notify on-call and annotate the incident timeline

## Post-Launch
- Capture learnings and update acceptance criteria
- Schedule next evaluation sweep
```

## Handoff Packet

Include these artifacts for reviewers and compliance:

- Prompt text, schema, and refusal policy
- Evaluation dataset, rubric, and latest scores
- Logging/redaction policy and retention timeline
- Owner list, escalation ladder, and rollback plan

## Experience Enhancements

- **Settings page.** Allow teams to toggle observability defaults (log fields, redaction levels, alert thresholds) and export a config JSON alongside the prompt.
- **Launch timeline.** Embed a visual status bar showing which gates have passed (dataset ready, rubric scoring, canary complete) so stakeholders can self-serve status.
- **Evidence locker.** Auto-generate a PDF/Markdown pack with the prompt version, scores, and runbook after each launch for audits and award submissions.
