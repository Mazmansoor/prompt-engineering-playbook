---
layout: default
title: Real-World — Support Triage
lede: Prompting for support triage should lower response times without losing empathy. Use a schema that is safe, auditable, and escalation-ready.
---

## Goals

- Categorize accurately with minimal manual review
- Surface risky or sensitive tickets to humans
- Provide a reproducible trail for compliance
- Keep tone respectful while being concise

## Prompt Structure

```
You are a support triage assistant.
Classify each ticket into: billing, access, feature request, bug, or abuse.
Include a confidence score (0-1) and a one-sentence rationale.
If abuse is detected, include a recommended escalation path and redact PII.
Return JSON with keys: category, confidence, rationale, escalate_to, redactions.
```

## Implementation Notes

- Pair with a **lexicon of product names** to reduce misclassification.
- Add **few-shot examples** for edge cases like refunds vs. credits.
- Log **rationales** for auditing and model retraining.
- Include **redaction rules** for user data before storing outputs.

## Metrics to Track

- Precision/recall per category
- Time-to-first-response for escalated tickets
- Percentage of tickets requiring manual correction
- False negative rate for safety-related categories (abuse, security)

## Example Response Schema

```json
{
  "category": "access",
  "confidence": 0.84,
  "rationale": "Login blocked after MFA reset; no billing terms mentioned.",
  "escalate_to": "L2-support",
  "redactions": ["Email address removed"]
}
```

## Experience Enhancements

- **Settings panel.** Allow ops teams to set category labels, routing destinations, and redaction rules from a UI, then generate the corresponding prompt so behavior stays aligned.
- **Playbook view.** Show the prompt, schema, and live metrics side-by-side for supervisors so they can understand how triage decisions are made.
- **Drift alerts.** Integrate evaluation harness results (precision/recall over time) and surface alerts when any category falls below a threshold.
- **Consent-aware outputs.** Toggle whether rationale and redactions appear in the agent response vs. internal logs to respect user privacy preferences.

## Shipping Checklist

- [ ] Redaction policy is explicit
- [ ] Escalation paths exist for abuse and security
- [ ] Confidence thresholds are defined for auto-closure vs. human review
- [ ] Logs capture rationale and redactions for audits
