# Prompt Engineering Playbook

Premium-grade, teaching-first guidance for designing prompt systems that hold up in production.

The playbook treats prompts as **designed control surfaces**—not magic spells. Every page is built for clarity, rigor, and client-ready polish.

## Structure

- `/foundations` — mental models and first principles
- `/patterns` — reusable prompt structures (e.g., structured outputs)
- `/advanced` — agentic, tool-using, and complex prompts
- `/labs` — exercises and prompt debugging
- `/real-world` — applied use cases and production checklists
- `/philosophy` — ethics, power, and responsibility

## Design Principles

- Explain *why*, not just *what*
- Show failures, not just successes
- Prefer clarity over cleverness
- Teach transferable thinking
- Keep presentation premium and client-ready

## Who This Is For

- Builders of AI-powered products who need predictable results
- Educators teaching responsible prompt design
- Analysts and strategists defining policy and governance
- Teams preparing prompts for regulated or high-stakes workflows

## Status

This is a living playbook. Stable ideas over novelty. Updates prioritize polish, operational rigor, and ethical clarity.

## Local Preview

Use the built-in Jekyll support to preview the premium layout locally:

1. Install Ruby and Bundler.
2. Run `bundle install` to fetch dependencies.
3. Run `bundle exec jekyll serve` and open `http://localhost:4000`.

If Jekyll is unavailable in your environment, you can still browse the markdown directly—every page is designed to read cleanly without the theme.

## Git Merge & Conflict-Resolution Guide

Follow these steps to keep your branch in sync and land changes without surprises:

1. **Sync main before you start.**
   ```bash
   git checkout main
   git pull origin main
   ```
2. **Create or update your feature branch.**
   ```bash
   git checkout -B work
   git rebase main
   ```
3. **Handle conflicts methodically.** When `git rebase` stops, run `git status` to see files in conflict, then open each file and pick the correct blocks. Use `git add <file>` after fixing each one, and continue with `git rebase --continue`. If you need to start over, `git rebase --abort` resets to the pre-rebase state.
4. **Verify formatting and build locally.**
   ```bash
   bundle exec jekyll build
   ```
   If Jekyll is unavailable, at least run `git status` to ensure only intentional edits are staged.
5. **Commit with a clear message.**
   ```bash
   git commit -am "Summarize the change"
   ```
6. **Push and open a PR.**
   ```bash
   git push origin work
   ```
   In GitHub, choose **Rebase and merge** (preferred for a linear history) or **Squash and merge** if the branch has many small commits.
7. **Last-mile check after merge.** Pull `main` again locally to confirm the merged site still builds and to cut a clean starting point for the next branch.

## Quickstart

1. Read `/foundations/01-what-is-a-prompt.md` to align on the five-part prompt skeleton.
2. Apply a reusable pattern from `/patterns` to reduce variance.
3. Stress-test it with a scenario in `/labs` and document failure modes.
4. Add guardrails from `/advanced` (tool policies, budgets, fallbacks) before shipping.
5. Run `/real-world/02-production-readiness` to pass launch gates and observability checks.
6. Review the ethical checklist in `/philosophy` to keep outcomes responsible.

## Depth-First Labs (No Fluff)

- **Debugging Lab.** Run a structured loop to expose missing context, schema gaps, and refusal errors—then log fixes so they’re reusable.
- **Evaluation Harness Lab.** Build a rubric, dataset, and scoring prompt so you can compare prompt variants with evidence instead of opinions.
- **Brand Voice & UX Lab.** Stress-test tone, overlays, and refusal wording across personas to keep outputs on-brand and safe.

## Awards-Ready Backlog

To push this from polished to prize-worthy, add:

- **Interactive labs** with runnable examples or short walkthrough clips.
- **Before/after case studies** showing measurable lift from adopting the patterns.
- **Accessibility pass** (ARIA labels, focus states, light/dark toggle) to meet AA standards.
- **Evaluation harness** with sample test sets, scoring scripts, and guidance for regression checks.

## Premium Feature Concepts

Bring the "premium product" promise to life with feature-grade additions:

- **Settings and brand kit page.** Let teams choose accent colors, typography scale, spacing density, and dark/light mode. Export the chosen tokens as JSON or CSS variables so brand and design partners can drop them into their own systems.
- **Experience presets.** Offer quick presets for "enterprise review", "education", and "agency pitch" modes that automatically swap typography, call-to-action copy, and layout density to match the audience.
- **Content controls.** Add switches to show/hide inline rationales, reveal failure examples, or flip between "teaching" and "delivery" voices so the same content works for learning and approvals.
- **Handoff pack generator.** One-click download of prompt templates, acceptance criteria, and QA checklists as PDF/Markdown bundles to send to clients or compliance reviewers.
- **Evaluation cockpit.** Small dashboard that surfaces prompt versions, quality gates, and sample test cases to make the playbook feel operational rather than static documentation.
