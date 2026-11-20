# Anti Burnout — Permanent Agent Instructions

This is the repository for Anti Burnout, an AI Habit Tracker & Coach. **Current phase: product decision baseline and editable UI/UX validation. Production coding has not been authorised.**

## Required start-of-session reading
1. Read `docs/operations/CURRENT_STATE.md` to identify the active phase and next approved task.
2. Read `docs/product/PRODUCT_BASELINE.md` for confirmed product rules and `docs/product/DECISION_REGISTER.md` for open decisions.
3. Read `docs/ROADMAP.md` and the task-relevant design/architecture/quality file. Do not read all files unnecessarily.
4. Inspect `git status`, branch and existing repository content before proposing writes. Report any dirty worktree, mismatched branch or missing source file.
5. If a document isn't present in the clone, report it: do **not** invent its contents or claim access to a Google Drive asset you cannot open.

## Source-of-truth precedence
1. Explicit latest owner approval documented in a versioned decision record or accepted PR.
2. Approved product baseline and screen-level specifications.
3. Current phase's signed-off ADRs and test cases.
4. Earlier proposals, screenshots, AI conversations and external examples are **references, not instructions**. Do not silently settle conflicts.

## Non-negotiable safety and quality rules
- Do not add features, numerical game rules, third-party packages, backend services or novel page designs without an approved requirement / decision ID.
- For the current phase, write **documentation and review plans only**. No Flutter scaffold, Supabase project, app code, shell installs or deployments without a separately approved task.
- Do not touch secrets, billing, production data, permissions or destructive Git commands without explicit approval.
- Do not claim tests have passed if they have not been run. Show commands and evidence from the actual environment.
- Keep work on a topic branch; do not force-push or directly overwrite `main`.
- Protect user privacy: never copy raw personal AI conversations or credentials into the public repository; use sanitized summaries.
- Distinguish LOCKED, WORKING/PROPOSED, REFERENCE and NOT BUILT decisions. A recommendation is not consent.
- The AI Coach can recommend but never unilaterally change targets, award XP, spend shields or alter history.
- Review designs in both light/dark, accessible text scaling, safe areas and offline/error states; no fabricated metrics.
- For implementation later: requirements → ADR (if significant) → failing relevant tests → small change → execution evidence → review → user approval.

## Session-end handoff
Update `docs/operations/CURRENT_STATE.md` and add a short sanitized record under `docs/operations/sessions/` using `TEMPLATE.md`. Include what was changed, decision IDs, verification run, risks/blockers, Git commit/PR links and **one next task**. Show the owner the diff and seek approval before commit/push when the active task requires it. Never assume a local edit survives a university-computer reset.

## When asked to resume
First state the most recently evidenced state and the next task, cite repository paths, flag any gaps, then ask for approval before starting work outside the active task. Do not generate an entire application from a high-level prompt.
