# Anti Burnout — Progressive Development Roadmap & Approval Gates

This is an **evidence-driven, slice-scoped roadmap**, not a calendar promise. It replaces the rigid monolithic waterfall model (requiring all 18 product decisions and 12 ADRs to be finalised before any coding) with a **progressive, feature-dependent SDLC**.

## Governance & Approval Hierarchy

Each development slice operates under four distinct lifecycle checkpoints:
1. **Permission to begin a slice:** Explicit owner approval of the slice's prerequisite product decisions, ADRs, and implementation boundaries.
2. **Completion of a slice:** Verifiable deliverables, passing invariant/negative/authorization tests, security/accessibility checks, code review, and explicit owner sign-off.
3. **Readiness for external beta testing:**
   - **Sub-stage A: Free internal/closed native beta distribution:** Internal Slices 0–5 completed, verified on Android (Google Play internal/closed testing) and iOS (Apple TestFlight). *Note: Free beta testing explicitly does not require final subscription pricing or completed purchase infrastructure unless the beta specifically includes paid features.*
   - **Sub-stage B: Paid subscription implementation & testing:** StoreKit (iOS) and Google Play Billing integration, server-side receipt validation, sandbox testing, and entitlement provisioning (Slice 6). Paid store entitlements require separate owner approval and verification before those features are distributed.
4. **Readiness for public app store release:**
   - **Sub-stage C: Public store release readiness:** Slice 6 completed, public store listings, terms/privacy policy compliance, production telemetry active, and owner-authorised release build.

### Non-Negotiable Engineering Principles
- **Dynamic AI Coach:** Generates natural, context-aware dialogue; never static decision trees or scripted responses.
- **Three-Tier Boundary:** Dynamic AI conversation, security/consent controls, and deterministic business logic (XP ledger, streaks, RLS) are strictly separated.
- **Zero Unauthorised State Mutation:** AI tools emit structured proposals only (e.g. `propose_habit_reduction`). Protected user state is modified *only* after explicit user confirmation in the UI.
- **Authorised Data Retrieval:** User habit data is retrieved via authenticated database queries. RAG is an optional retrieval architecture for long-term reference, **not** a prompt-injection defense.
- **Targeted Testing:** Prioritises business invariants, state transitions, duplicate/replay prevention, RLS user isolation, and negative scenarios over arbitrary vanity 100% code coverage.
- **Continuous Quality & Accessibility:** Security, accessibility, static analysis, and code review apply continuously to every slice, starting from Slice 0. Essential accessibility checks (including screen-reader semantics, WCAG 2.2 AA contrast, and platform-level reduced-motion behavior) are never deferred to late release phases.
- **Native iOS & Android Strategy:** Shared Flutter/Dart codebase for native mobile only. Web, PWA, and Cloudflare Pages are out of scope. Native iOS compilation requires macOS/Xcode or an approved hosted environment; an early Android native build verification milestone is mandated.
- **MVP Interaction & Animation Scope (Owner Confirmed):** Prioritise meaningful, dynamic user interactions over elaborate visual animations. Build reusable UI components; keep animations strictly separated from business logic; introduce no unnecessary animation engines or heavy dependencies. Approved MVP scope: smooth onboarding transitions, essential microinteractions (navigation, check-in, validation, progress), dynamic LLM dialogue, lightweight coach representation (static portraits or small set of pre-rendered expression states from approved character assets), and platform-compliant reduced-motion support. *Note: `MediaQuery.disableAnimationsOf(context)` is an accessibility signal, not an automatic guarantee; custom animations and transitions must be individually designed and tested to respect platform preferences such as iOS "Reduce Motion" and Android "Remove animations" (e.g. providing instant cuts or subtle cross-fades rather than motion-heavy transforms).* Explicitly deferred to post-MVP: complex real-time 3D animation, pet-companion environments, avatar gesture systems, voice-driven animations, and elaborate gamification sequences.

---

## Slice Dependency & Approval Matrix

| Slice | Focus Area | Prerequisite ADRs | Required Product Decisions | Decisions Deferred | Earliest Build Milestone |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Slice 0** | Flutter Native Foundation & Design System | ADR-001, ADR-002 | Verified Stitch design tokens (unverified colors remain PROPOSED) | Gamification math, backend, AI prompts, billing | **Yes (Earliest buildable Flutter feature)** |
| **Slice 1** | Habit Domain, Auth, Scheduling & XP Ledger | ADR-003, ADR-004, ADR-005, ADR-006 | Habit entity, recurrence, minimal timezone (PD-04), minimal duplicate check-in (PD-05 remains OPEN), 100 XP Green (LOCKED) | Yellow proportional formulas, shields, pause, pricing | No (Requires Slice 0 shell & backend setup) |
| **Slice 2** | Early Dynamic AI Coach Proof of Concept | ADR-008 | Coach persona (2 characters, custom name, Easy/Med/Hard tone) (LOCKED), UI consent contract | Proportional scoring math, long-term memory, billing | No (Requires Slice 1 habit domain & auth) |
| **Slice 3** | Yellow Renegotiation & Proportional Ledger | ADR-004 (extension) | PD-01 (proportional scoring), PD-06 (timing cutoff), PD-07 (below-minimum) | Shields, emergency pause, comeback cooldowns | No (Requires Slice 1 ledger & Slice 2 UI) |
| **Slice 4** | Recovery Mechanics (Shields, Pause, Comeback) | ADR-007, ADR-012 | PD-08..PD-11 (Shield 600 XP/wallet 2 LOCKED; pause boundaries, comeback badge) | Subscription pricing & commercial limits | No (Requires Slice 1 & 3 scoring engine) |
| **Slice 5** | Insights, Progress, Levels & Complete Journey | ADR-010 | PD-02 (Level curve thresholds & caps), analytics definitions | Subscription billing | No (Requires Slices 1–4 tracking data) |
| **Slice 6** | Monetization, Store Compliance & Beta Release | ADR-009, ADR-011 | PD-16 (Tier pricing, AI allowances) — *Paid monetization deferred from free beta* | Future post-beta features (PD-17) | External Beta & Public Release |

---

## Detailed Sliced Approval Gates

### Slice 0: Flutter Native Foundation & Design System
* **Objective:** Establish the Flutter native workspace, verified design system tokens, typography, and primary 4-tab shell navigation. Validate local Android toolchain and build execution.
* **Approved Stitch References:** Screens 01 (Welcome), 06 (Today base shell), 21 (Appearance).
* **Required Product Decisions:** Visual tokens verified against owner-approved Stitch exports. Example color hexes in prior drafts remain PROPOSED until verified.
* **Required ADRs:**
  - `ADR-001` (Flutter UI Architecture & State Management: layer boundaries, Riverpod/Clean Architecture).
  - `ADR-002` (Routing & Deep Links: navigation structure for Today, Habits, Insights, Coach).
* **Decisions That Can Remain Open:** All gamification math, scoring formulas, backend schemas, AI prompts, subscription pricing.
* **Implementation Boundaries:** Presentation, token system, reusable UI components, and shell navigation only. Zero backend calls, zero state persistence. Lightweight, standard Flutter transitions only; no heavy animation engines or custom physics dependencies.
* **TDD & Verification:**
  - Flutter widget tests verifying theme toggle (light/dark/system), typography rendering, safe-area compliance, 4-tab navigation, and individual reduced-motion behavior (verifying that platform signals like iOS Reduce Motion and Android Remove animations correctly trigger graceful fallback transitions such as instant cuts or fades rather than transforms).
  - Accessibility checks apply immediately in Slice 0 and continuously thereafter, not deferred to Slice 5.
  - Native Android build verification: execute `flutter build apk` or run on connected Android device/emulator to verify local toolchain.
* **Security & Accessibility:** Safe-area handling, WCAG 2.2 AA contrast on token palette, dynamic text scaling support, individual reduced-motion transition testing across platforms, no secrets in repo.
* **Acceptance Criteria:** App builds and runs on local Android environment; 4 tabs switch smoothly; dark/light mode toggles; passes `flutter test` and `flutter analyze`.
* **Owner Approval Checkpoint:** Owner reviews UI shell and verifies design token alignment with Stitch master.

---

### Slice 1: Habit Domain, Authentication, Scheduling, Secure Check-ins & XP Ledger Foundation
* **Objective:** Deliver truthful habit scheduling, user authentication, baseline daily check-in (Green = 100 base XP; Missed = Red), and server-authoritative atomic XP ledger.
* **Approved Stitch References:** Screens 03 (Account Access), 06 (Today), 07 (My Habits), 10 (Habit Goal), 11 (Schedule/Minimum), 12 (Review Commitment).
* **Required Product Decisions:** Habit entity schema, recurrence types (daily, fixed days, weekly quota), minimal timezone and day-boundary semantics (PD-04, coordinated with minimal day-boundary subset of ADR-012), minimal duplicate check-in rule (note: PD-05 remains OPEN until the owner explicitly approves its implementation rule), missed-commitment definition; 100 base reference XP for full Green completion (LOCKED). Full notification and recovery policy remains deferred until later slices.
* **Required ADRs:**
  - `ADR-003` (Backend Boundary: Supabase client & Edge Functions).
  - `ADR-004` (Data Ownership, Atomic Ledger & Scoring: **mandatory before implementing server-authoritative XP awards**).
  - `ADR-005` (Data Model & Migrations: users, habits, recurrence, check-in records).
  - `ADR-006` (Authentication & Authorization: Apple/Google/email auth, Row Level Security).
* **Decisions That Can Remain Open:** Yellow proportional formulas, non-measurable micro-step scoring, shield shortfall logic, comeback windows, subscription billing.
* **Implementation Boundaries:** Habit CRUD, local/server check-in, atomic XP ledger. No Yellow reductions, no AI coach.
* **TDD & Verification:**
  - Invariant tests for recurrence rules (daily, fixed days, quota).
  - Integration tests for auth and check-in workflows.
  - RLS denial tests proving users cannot read or modify another user's habits or XP ledger.
  - Idempotency tests verifying double-tap / replay submissions cannot double-award XP.
* **Security & Accessibility:** RLS on all database tables; client secrets restricted to publishable keys; auth token verification on every write; clear screen-reader labels for habit items.
* **Acceptance Criteria:** User can register/log in, create a habit with recurrence, check in full completion to earn 100 XP in server ledger, and view missed commitments as Red; RLS isolation verified.
* **Owner Approval Checkpoint:** Owner reviews ledger schema, check-in flows, and RLS test evidence.

---

### Slice 2: Early Dynamic AI Coach Proof of Concept
* **Objective:** Validate Anti Burnout's core differentiator early. Implement a dynamic, context-aware AI Coach generating natural, non-scripted dialogue and structured reduction proposals, protected by a hard UI consent gate.
* **Approved Stitch References:** Screens 04 (Coach Selection), 09 (AI Coach Chat), 16 (AI Proposal Review), 26 (Coach Preferences).
* **Required Product Decisions:** 2 coach character choices, custom name, Easy/Medium/Hard tone guidelines (LOCKED); explicit consent requirement before any target modification.
* **Required ADRs:**
  - `ADR-008` (AI Coach Architecture: LLM gateway, dynamic context assembly from authorized DB queries, tool calling contracts, prompt-injection defense, non-clinical safety boundaries).
* **Decisions That Can Remain Open:** Proportional scoring math (Slice 3), long-term vector embeddings, subscription tier gates.
* **Implementation Boundaries:** Conversational interface and structured proposal generation (`propose_habit_reduction`). Lightweight AI Coach visual representation using approved character assets: static portraits or a small set of pre-rendered expression states are sufficient for MVP. Complex real-time 3D character animation, interactive pet environments, avatar movement/gesture systems, and voice-driven animations are explicitly deferred until post-MVP evaluation. **AI proposals DO NOT modify protected user state directly; proposals render in Screen 16 for user approval.**
* **TDD & Verification:**
  - Dynamic response evaluation suite verifying adaptive dialogue across Easy, Medium, and Hard tones without static trees.
  - Prompt-injection resistance test suite.
  - Schema validation for `propose_habit_reduction` tool call.
  - UI consent gate tests proving database state cannot be mutated by LLM output alone.
* **Security & Accessibility:** Zero LLM API keys in mobile binary (backend Edge Function gateway); structured user habit data loaded via authorized database queries (RAG is optional retrieval, not prompt-injection security). Defence-in-depth: client UI confirmation enables informed consent, while the trusted backend independently enforces authentication, RLS user-specific authorization, schema validation, idempotency, and exact-action matching. Non-clinical safety guardrails and adversarial prompt-injection tests.
* **Acceptance Criteria:** Natural conversation running with Coach; Coach can suggest a context-aware reduction proposal via structured tool; proposal renders in UI consent view; zero unconfirmed database mutations.
* **Owner Approval Checkpoint:** Owner reviews conversational quality, safety evals, and consent barrier.

---

### Slice 3: Yellow Renegotiation, Proportional Scoring and Streak Logic
* **Objective:** Implement the Snowball Effect: completing user-approved reduced commitments, awarding proportional XP, and maintaining dual-streak accounting (Consistency vs Full Target).
* **Approved Stitch References:** Screens 06 (Today - Yellow state), 13 (Habit Detail), 14 (Habit History), Flow F02 (Yellow Renegotiation).
* **Required Product Decisions:** PD-01 (proportional calculation for measurable habits, resolution of non-measurable micro-step scoring), PD-06 (renegotiation timing cutoff), PD-07 (below-minimum effort handling).
* **Required ADRs:** Updates to `ADR-004` (Ledger event types for Yellow reductions and audit preservation).
* **Decisions That Can Remain Open:** Shield economics, emergency pause boundaries, subscriptions.
* **Implementation Boundaries:** User approval of reductions, Yellow check-in submission, proportional XP ledger transaction, dual streak updates. Essential check-in microinteractions, validation, and feedback animations only; elaborate gamification animation sequences are deferred. Original target remains auditable.
* **TDD & Verification:**
  - Invariant tests: Yellow awards strictly <100 XP; Yellow preserves original target in audit history.
  - State machine tests: Consistency streak increments while full target streak remains distinct; late renegotiation rejected.
* **Security & Accessibility:** Server-authoritative calculation of proportional XP (client cannot forge custom XP values).
* **Acceptance Criteria:** User can negotiate reduction (manually or via Coach proposal), approve in UI, check in, receive proportional XP, and see consistency streak maintained truthfully.
* **Owner Approval Checkpoint:** Owner reviews mathematical edge tests, audit trail preservation, and UI states.

---

### Slice 4: Recovery Mechanics, Shields, Pause and Comebacks
* **Objective:** Deliver safety nets preventing burnout and guilt: shield wallet, indefinite manual emergency pause, and comeback badges.
* **Approved Stitch References:** Screens 18 (Recovery & Shields), Flows F04 (Manual Shield), F05 (Comeback).
* **Required Product Decisions:** PD-08..PD-11 (Shield exchange 600 XP = 1 shield, max 2 wallet stored; shield application to daily/weekly quotas; indefinite emergency pause; comeback window & badge rules).
* **Required ADRs:**
  - `ADR-007` (Offline Caching & Sync Reconciliation: offline queued check-ins, optimistic UI vs confirmed server status).
  - `ADR-012` (Notification & Time Policy: quiet hours, timezones, due cutoffs).
* **Decisions That Can Remain Open:** Subscription pricing and billing.
* **Implementation Boundaries:** Shield earning (every 600 XP), shield spending, emergency pause toggle, comeback badge issuance. No false completion or unearned XP.
* **TDD & Verification:**
  - Ledger deduction tests; emergency pause prevents streak break without awarding XP.
  - Comeback badge tests following verified return.
  - Offline queue and idempotent sync replay tests.
* **Security & Accessibility:** Server-enforced wallet balance checks; offline timestamp and replay protection.
* **Acceptance Criteria:** Shields earn at 600 XP milestones; user can manually shield an eligible missed session; emergency pause freezes schedules with zero falsification; offline check-in reconciles upon reconnection.
* **Owner Approval Checkpoint:** Owner reviews recovery edge tests and offline conflict verification.

---

### Slice 5: Insights, Progress, Levels and Complete Journey
* **Objective:** Surface visual habit analytics, level progression curves, accessibility compliance, and end-to-end journey polish.
* **Approved Stitch References:** Screens 02 (Snowball Story), 05 (First Week), 08 (Insights), 15 (Detailed Insights), 17 (Progress & Levels), 19 (Profile), 20–23, 25.
* **Required Product Decisions:** PD-02 (Level curve progression thresholds and caps), analytics definitions.
* **Required ADRs:** All prior ADRs updated; `ADR-010` (Observability & Telemetry).
* **Decisions That Can Remain Open:** Final paid subscription pricing.
* **Implementation Boundaries:** Data visualization, level rewards/badges, profile and settings management. Reusable UI components; responsive layouts, complete accessibility semantics, and OS-level reduced-motion compliance.
* **TDD & Verification:**
  - Analytics aggregation accuracy tests.
  - Comprehensive accessibility audit across screen reader semantics, 44pt/48dp touch targets, dynamic type scaling, WCAG 2.2 AA contrast, and platform-level reduced-motion compliance in dark and light modes, verifying that continuous accessibility standards established from Slice 0 hold across the unified user journey.
* **Security & Accessibility:** Sanitized logging (no raw AI chat transcripts or personal habit text in telemetry); GDPR data export and account deletion flows.
* **Acceptance Criteria:** Full onboarding to daily tracking to insights loop functional; passes comprehensive accessibility and contrast audit.
* **Owner Approval Checkpoint:** Owner reviews complete journey and accessibility audit.

---

### Slice 6: Monetization, Store Compliance & Beta Release (Gate 5)
* **Objective:** Package native builds for Google Play internal/closed testing and Apple TestFlight for closed beta; prepare monetization and store compliance for public launch.
* **Approved Stitch References:** Screen 24 (Plus / Entitlements).
* **Required Product Decisions:** PD-16 (Paid tiers, subscription pricing, premium AI quotas). *Note: Paid subscriptions are NOT required for the initial free closed beta.*
* **Required ADRs:**
  - `ADR-009` (Store In-App Purchases & Entitlements).
  - `ADR-011` (Release Engineering, Signing, CI/CD).
* **Implementation Boundaries:** StoreKit and Google Play Billing, signed native `.aab` / `.ipa`, release CI/CD pipeline.
* **TDD & Verification:**
  - Receipt validation tests; subscription entitlement tests; restore purchases tests.
  - Crash reporting and rollback verification.
* **Security & Accessibility:** Store privacy compliance, MASVS/MASTG security baseline, dependency vulnerability audit.
* **Acceptance Criteria:** Free closed beta distributed to testers on Android (Play Console) and iOS (TestFlight); subsequent paid tier verified on sandbox accounts; owner signs off public release build.
* **Owner Approval Checkpoint:** Owner signoff on beta distribution build and production release build.

---

## Outstanding Governance & Quality Invariants

The following governance and quality requirements from Phase 0 and earlier roadmaps remain active invariants across all development slices:
- **Branch Protection & Review Process (Gate 0 DRAFT):** Protected `main` branch with required PR reviews, CI passing checks, and linear git history.
- **Project-Specific Agent Skill Approval (Gate 0 DRAFT):** Project-owned agent skills maintained in `.agents/skills/` only when individually reviewed; no bulk installation of unvetted external repositories.
- **Product Decision Traceability:** Every business rule implemented must map directly to an approved decision ID in `docs/product/DECISION_REGISTER.md` with explicit acceptance tests.
- **Stitch Design Token Verification:** All colors, typography, spacing, and component specs must be extracted and verified from approved Stitch master designs into `docs/design/DESIGN.md` before implementation.
- **UI State & Accessibility Review:** Continuous review of light/dark themes, empty/error/loading states, safe-area compliance, 44pt/48dp touch targets, and platform reduced motion (`docs/design/DESIGN_REVIEW.md`).
- **Slice-Scoped Architecture Sign-Off:** Each vertical slice requires explicit owner review and approval of its prerequisite ADRs before code is written.
- **TDD & Independent Code Review:** Strict TDD (failing invariant/negative tests before implementation); independent code review standard enforced via `prompts/003-code-review.md`.
- **Security & Privacy Testing:** OWASP MASVS/MASTG mobile baseline, RLS denial tests, server-authoritative calculations, and zero client-side secrets.
- **Native Device Verification:** Native Android build and device/emulator execution verified in Slice 0; native iOS compilation verified in macOS/Xcode or approved hosted build environment.
- **Release Readiness Sign-Off:** Final release readiness checklist (`docs/quality/TEST_SECURITY_RELEASE.md`) verified before public distribution.
