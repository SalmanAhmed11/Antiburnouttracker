# Anti Burnout — End-to-End Roadmap and Approval Gates

This is a **living checklist**, not a calendar promise. Gate statuses are evidence-driven. `DONE` means signed off, `DRAFT` means work exists but not fully approved, `BLOCKED` means missing evidence, `NOT STARTED` means no verified work.

## Gate 0 — Continuity and control (DRAFT)

- [x] Create GitHub repository (existing README; no application code verified).
- [x] Prepare portable rules/roadmap/current-state/decision register (Phase 0B starter pack merged).
- [x] Review and merge documentation via PR; verify `AGENTS.md` loads in Antigravity (PR #1 & PR #2 merged).
- [ ] Agree branching and approval process; configure protections where available.
- [x] Perform read-only environment audit (Git, Flutter/Dart, Android SDK, Node, workspace permissions).
- [ ] Keep project-owned agent skills in `.agents/skills/` only when individually reviewed; don't bulk install untrusted repos.

**Gate accepted when:** fresh clone and new Antigravity conversation can state exact phase, approved rules, active task and blockers without invented assumptions.

## Gate 1 — Product rules and acceptance criteria (DRAFT)

- [x] Consolidated concept, personas/benefit hypotheses, initial 26-screen inventory and brand identity.
- [x] Working requirements and proposed game/recovery rules documented in master.
- [ ] Review decision register PD-01..PD-18, record chosen alternatives and approval evidence (Round A unresolved edge cases active).
- [ ] Create requirement IDs, user stories, invariants and acceptance scenarios for every critical action.
- [ ] Define free versus Plus entitlement matrix; success/guardrail metrics.
- [ ] Classify MVP / beta / deferred scope; identify legal, privacy and store-policy questions.

**Gate accepted when:** all launch-critical behaviours are unambiguous or explicitly deferred; no unapproved numerical mechanics remain in an implementation prompt.

## Gate 2 — Editable UI/UX and user flow validation (DRAFT)

- [x] 26 dark/light screen design drafts and eight supporting interaction concepts.
- [x] Manual Stitch design work completed by product owner (Stitch MCP integration not required).
- [ ] Choose canonical editable design home and version identifiers.
- [ ] Extract and verify shared tokens (`DESIGN.md`), logo assets, typography, spacing and component library.
- [ ] Rebuild page 01 in both modes; inspect before building other pages.
- [ ] Complete page and state matrix in `docs/design/DESIGN_REVIEW.md`.
- [ ] Link all 8 core flows, validate back/forward/cancel confirmation and empty/error states.
- [ ] Run accessibility checks and formative usability walkthroughs; record fixes.
- [ ] Freeze approved design version and export reviewed snapshots/links.

**Gate accepted when:** selected user journeys are prototype-testable and the implementation agent need not invent screens or states.

## Gate 3 — Architecture and security design (NOT STARTED)

- [ ] Write ADRs for Flutter layers/state/routing, backend choice, transaction model and offline policy.
- [ ] Define data entities, relationships, indexes, ownership, migrations, RLS and audit ledger.
- [ ] Define API contracts, authorization/error schemas, idempotency and rate limits.
- [ ] Map trust boundaries, AI tool permissions, data retention, privacy and threat model.
- [ ] Define NFR targets (performance, accessibility, availability, privacy, cost, recovery).
- [ ] Record deployment environments, rollback approach and Apple/Android tooling prerequisites.

**Gate accepted when:** important choices have recorded alternatives, tradeoffs, rationale and validation plans.

## Gate 4 — Engineering environment and implementation slices (NOT STARTED)

- [ ] Verify stable Flutter/Dart toolchain, Android build, Git, dependencies and local quality tools (Substeps verified: Flutter 3.50.1, Dart 3.14.0, Android SDK 36, and Dart MCP active; Outstanding: native Android build execution and emulator/device testing).
- [ ] Pin tool/dependency versions and review selected official skills/MCP permissions (Flutter plugin v1.0.7 verified; project-specific skills proposed).
- [ ] Establish CI for formatting, static analysis, unit/widget/integration tests and secret scanning.
- [ ] Implement design system first; then one narrowly scoped vertical feature at a time using tests and reviewed PRs.
- [ ] Check UX fidelity dark/light and business rules against approved design/acceptance criteria.

**Gate accepted per slice:** passing evidence + review + implementation explanation + owner approval.

## Gate 5 — Beta readiness and launch (NOT STARTED)

- [ ] Security tests (OWASP MASVS/MASTG, API, AI tool abuse, ownership isolation).
- [ ] Real device coverage, accessibility, regression, offline and migration recovery tests.
- [ ] Monitoring, crash reporting, backup restore and incident response rehearsed.
- [ ] Privacy/legal/store listing and subscription compliance reviewed.
- [ ] Distribution build verified, beta signoff and rollback plan recorded.

**Gate accepted when:** release risks are explicitly assessed and the owner authorises the specific build.

## Gate 6 — Ongoing maintenance (NOT STARTED)

- [ ] Triage feedback; evaluate AI safety regressions; upgrade dependencies and maintain backups.
- [ ] Review product metrics for sustained value (not compulsive engagement).
- [ ] Keep decision register, ADRs and session handoff current.
