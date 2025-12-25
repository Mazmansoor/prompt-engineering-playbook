---
layout: default
title: Feedback & Contact
hero_heading: Feedback & Contact
lede: Gather premium-grade feedback, route it to the right owners, and keep a clean audit trail without sending people back to the repo.
cta_label: Submit Feedback
cta_target: #feedback-form
cta_secondary_label: Email the Team
cta_secondary_target: mailto:feedback@example.com?subject=Prompt%20Playbook%20Feedback
---

## Why Feedback Matters

- **Proof of value.** Show prospects and stakeholders that the playbook keeps improving based on real usage.
- **Signal quality issues early.** Capture breakages, confusing sections, or accessibility gaps before they become churn.
- **Guide the roadmap.** Prioritize labs, presets, and templates that customers explicitly ask for.

## Feedback & Contact Options

<div class="feedback-panel">
  <h3>Preferred: Form Submission</h3>
  <p>Drop the feedback form below into your static site host (Netlify, Vercel, Cloudflare Pages, or GitHub Pages with a form backend). Swap the <code>action</code> URL with your provider endpoint (Formspree, Basin, Netlify Forms, etc.).</p>
  <form id="feedback-form" class="feedback-form" action="https://formspree.io/f/YOUR_ENDPOINT" method="POST">
    <div class="form-row">
      <label for="name">Name</label>
      <input id="name" name="name" type="text" placeholder="How should we address you?">
    </div>
    <div class="form-row">
      <label for="email">Email (optional)</label>
      <input id="email" name="email" type="email" placeholder="name@company.com">
    </div>
    <div class="form-row">
      <label for="role">Role</label>
      <input id="role" name="role" type="text" placeholder="e.g., PM, Educator, Compliance">
    </div>
    <div class="form-row">
      <label for="section">Page or section</label>
      <input id="section" name="section" type="text" placeholder="Which page or module are you reacting to?">
    </div>
    <div class="form-row">
      <label for="feedback">Feedback</label>
      <textarea id="feedback" name="feedback" rows="4" placeholder="What worked, what broke, and what you'd like next"></textarea>
    </div>
    <div class="form-row inline">
      <label for="contact-consent" class="checkbox">
        <input id="contact-consent" name="contact_consent" type="checkbox" value="yes">
        <span>I’m okay being contacted for follow-up.</span>
      </label>
    </div>
    <input type="hidden" name="_subject" value="Prompt Playbook Feedback">
    <button type="submit" class="button primary">Send Feedback</button>
  </form>
  <p class="helper">Tip: If you want to log submissions, connect your form backend to a spreadsheet or CRM (e.g., Airtable, Google Sheets) via a no-code automation.</p>
</div>

<div class="feedback-panel">
  <h3>Alternate: Direct Email</h3>
  <p>Prefer a direct channel? Use a dedicated inbox and triage queue.</p>
  <ul>
    <li><strong>Inbox:</strong> <a href="mailto:feedback@example.com?subject=Prompt%20Playbook%20Feedback">feedback@example.com</a></li>
    <li><strong>Auto-routing:</strong> Add labels for "bug", "content", and "partnership" so owners see the right notes.</li>
    <li><strong>Templates:</strong> Configure an autoresponder with a short SLA and a link back to this page.</li>
  </ul>
</div>

## How to Capture and Route Feedback

1. **Pick a backend.** Create an endpoint with Formspree, Basin, or your preferred static form service and paste its URL into the form’s <code>action</code> attribute.
2. **Add logging.** Use Zapier/Make to forward submissions into a spreadsheet with columns for name, role, section, sentiment, and follow-up owner.
3. **Create a triage ritual.** Weekly review: merge duplicates, assign owners, and track resolution dates. Publish notable fixes on the landing page so readers see responsiveness.
4. **Close the loop.** When you ship a fix, reply to the submitter (if they opted in) and thank them. Include a short changelog link.

## Privacy & Trust Signals

- Keep fields optional except for the feedback text itself.
- Avoid collecting sensitive data—this playbook should feel safe to share.
- If you add analytics or third-party capture, disclose it here with a one-line notice.

## Where to Place the CTA

- Add a top-level navigation link labelled "Feedback" pointing here.
- Include a brief "Was this useful?" link to this page at the bottom of high-traffic pages (labs, patterns, real-world templates).
- Mention the contact options in your README so contributors know how to share suggestions without hunting for repo links.
