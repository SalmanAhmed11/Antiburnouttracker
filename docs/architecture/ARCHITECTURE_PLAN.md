# Architecture, Database and API Design Backlog

**Status: Progressive Slice-Scoped Architecture Plan.** Architecture Decision Records (ADRs) are evaluated and approved incrementally prior to each implementation slice. Do not start source code, schema, or cloud provisioning without explicit prior ADR and slice approval.

## Target Platform & Deployment Boundaries
- **In Scope:** Native Android and native iOS application developed with a shared Flutter/Dart codebase. Platform-specific implementations only where technically necessary.
- **Excluded from Scope:** Flutter Web deployment, Progressive Web Apps (PWA), Cloudflare Pages hosting, and separate web-based betas.
- **Backend Candidate:** Supabase is the preferred candidate (authentication, PostgreSQL, Row Level Security, Edge Functions, server-authoritative scoring); adoption remains subject to formal ADR evaluation.
- **Workstation Verification:** Native Android build execution and emulator testing is an early milestone in Slice 0; native iOS compilation requires macOS/Xcode or an approved hosted macOS build environment.

---

## Slice-Aligned Architecture Decision Records (ADRs)

| ADR | Title / Topic | Prerequisite For | Key Alternatives & Architectural Questions |
| :--- | :--- | :--- | :--- |
| **ADR-001** | Flutter UI Architecture & State | **Slice 0** | Layer boundaries, state management (Riverpod vs BLoC vs Clean Architecture); testability and separation of presentation. |
| **ADR-002** | Routing & Deep Links | **Slice 0** | `go_router` vs Flutter Navigator 2.0; 4-tab shell navigation, modal transitions, onboarding guards, and deep-link handling. |
| **ADR-003** | Backend Boundary & Edge Functions | **Slice 1** | Supabase native SDK + TypeScript Edge Functions vs standalone API server; latency, cold starts, client vs server secrets. |
| **ADR-004** | Data Ownership, Atomic Ledger & Scoring | **Slice 1** (Mandatory before real XP) | Server-authoritative XP and streak ledger; atomic database transactions; idempotency keys and replay protection. Extended in Slice 3 for Yellow reductions. |
| **ADR-005** | Data Model & Migrations | **Slice 1** | Relational schema (PostgreSQL): users, habits, recurrence, check-in records, audit trail; versioned migration tooling. |
| **ADR-006** | Authentication & Authorization | **Slice 1** | Apple, Google, passwordless email; Row Level Security (RLS) policies by auth subject; secure session refresh. |
| **ADR-008** | Dynamic AI Coach Architecture & Security | **Slice 2** | LLM API gateway via Edge Function; dynamic context assembly from authorized DB queries; structured tool proposals (`propose_habit_reduction`); prompt-injection defense; hard UI consent gate. *(Clarification: RAG is an optional retrieval tool, not a prompt-injection boundary).* |
| **ADR-007** | Offline Caching & Sync Reconciliation | **Slice 4** | Optimistic UI vs server-confirmed state; local cached drafts vs queued actions; timestamp conflict resolution and idempotency. |
| **ADR-012** | Notification & Time Policy | **Slice 4** (with minimal timezone & local due-cutoff subset in **Slice 1**) | Local device scheduled notifications vs push triggers; quiet hours; DST transitions; local midnight due-date boundaries coordinated with PD-04 and PD-05. |
| **ADR-010** | Observability, Telemetry & Operations | **Slice 5** | Sanitized error reporting (Sentry/crashlytics); safe logging (zero raw chat transcripts or habit text in telemetry); backup/restore SLOs. |
| **ADR-009** | Billing, Store In-App Purchases & Entitlements | **Slice 6** | RevenueCat vs native StoreKit / Play Billing; server-side receipt validation; restoration flows. *(Explicitly deferred from free closed beta).* |
| **ADR-011** | App Release Engineering & Beta Channels | **Slice 6** | Android signing, Google Play internal/closed testing, iOS TestFlight CI/CD automation, rollback runbooks. |

---

## Architectural Boundaries & Principles

### 1. Three-Tier Separation
```
┌────────────────────────────────────────────────────────────────────────┐
│ 1. DYNAMIC AI CONVERSATIONAL TIER                                     │
│    • Natural, adaptive dialogue tailored to user context               │
│    • Zero hardcoded decision trees or static response scripts          │
│    • Generates structured proposals only via typed tool calls          │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ Emits structured proposal
                                    ▼ (e.g. propose_habit_reduction)
┌────────────────────────────────────────────────────────────────────────┐
│ 2. SECURITY & USER CONSENT GATEWAY (Hard Boundary)                     │
│    • Strict schema validation of tool arguments                        │
│    • EXPLICIT USER CONFIRMATION REQUIRED in UI for state changes       │
│    • LLM output cannot directly mutate database records or mint XP     │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ User confirms proposal in UI
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 3. DETERMINISTIC APPLICATION BUSINESS LOGIC (Server-Authoritative Core)│
│    • Atomic XP ledger & immutable historical audit trail               │
│    • Mathematical streak accounting (Green, Yellow, Red)               │
│    • Row Level Security (RLS) user isolation                           │
│    • 100% testable via deterministic unit/integration TDD tests        │
└────────────────────────────────────────────────────────────────────────┘
```

### 2. Context Retrieval, AI Defence-in-Depth & Trusted Backend Boundaries
- **Authorised Database Retrieval:** User habit status, commitments, and historical records are loaded into the AI context via authenticated, parameterized database queries. RAG is strictly an optional mechanism for retrieving reference behavioral coaching knowledge; it is **not** an access control or prompt-injection security mechanism.
- **Defence-in-Depth vs Complete Security Guarantees:** Client-side confirmation UI, system prompt instructions, input sanitization, and constrained tool schemas are valuable defence-in-depth measures, but they are **not** complete security guarantees against prompt injection or adversarial manipulation. The client-side confirmation UI supports informed user consent but **cannot replace server-side authorization**.
- **Trusted Backend Enforcement (Non-Negotiable):** The trusted backend (PostgreSQL RLS, Edge Functions, database triggers) must independently and authoritatively enforce:
  1. *Authentication:* Verification of cryptographically valid user session tokens.
  2. *User-Specific Authorization & Data Ownership:* Every read/write is strictly partitioned by user identity; no client or LLM proposal can bypass tenant isolation.
  3. *Schema & Business-Rule Validation:* Payloads are strictly validated against domain invariants on the server, independent of what the AI emitted.
  4. *Restricted Tool Permissions:* Edge Functions and database roles operate with least privilege.
  5. *Idempotency for Consequential Actions:* Cryptographic/uuid idempotency keys prevent duplicate or replayed mutations.
  6. *Exact Action Verification for User Consent:* Where user consent is required, the backend cryptographically or deterministically validates that the confirmed payload matches the exact proposal presented to the user.
  7. *Server Credential Protection:* LLM provider API keys, database service-role keys, and payment credentials are kept exclusively on the server; zero secrets exist in mobile binaries.
  8. *Adversarial & Security Evaluations:* Regular automated testing for prompt injection, jailbreaks, data exfiltration attempts, and authorization bypasses.

### 3. UI Interaction & Animation Architecture (MVP Scope)
- **Standard Flutter Animations:** Standard implicit and explicit Flutter animations only (`AnimatedSwitcher`, `TweenAnimationBuilder`, `PageRouteBuilder`). Zero heavy third-party 3D or physics animation engines for MVP.
- **Decoupled Architecture:** Animation controllers and visual microinteractions are strictly separated from domain models and business logic.
- **Lightweight Coach Assets:** Pre-rendered character expression states or static portraits loaded from local assets; complex real-time 3D, pet environments, and avatar gesture engines are explicitly deferred.
- **Accessibility & Reduced Motion:** `MediaQuery.disableAnimationsOf(context)` is an accessibility query/signal, not an automatic guarantee that all custom animations respect user preferences. Platform-level preferences (including iOS "Reduce Motion" and Android "Remove animations") must be respected by individually designing and testing all custom transitions, microinteractions, and reusable components with graceful fallbacks (e.g., instant cuts or subtle cross-fades rather than motion-heavy transforms). Accessibility verification applies continuously starting from Slice 0, not as a late release phase.

---

## Required Design Outputs Per Slice

Before code implementation begins for any slice, the associated ADRs and design artifacts must be approved:
- **Slice 0:** Verified design token map from Stitch (`docs/design/DESIGN.md`), `ADR-001`, `ADR-002`.
- **Slice 1:** PostgreSQL schema migration scripts, RLS policy definitions, `ADR-003`, `ADR-004`, `ADR-005`, `ADR-006`.
- **Slice 2:** `ADR-008`, tool schema JSON contracts, prompt evaluation suite, prompt-injection test harness.
- **Slice 3:** Extended transaction definitions in `ADR-004`, mathematical edge test specifications.
- **Slice 4:** Offline sync state machine, `ADR-007`, `ADR-012`.
- **Slice 5:** Telemetry schema, GDPR export/delete specification, `ADR-010`.
- **Slice 6:** Store entitlement matrix, `ADR-009`, `ADR-011`.

---

## ADR Template
```markdown
**Title / ID:** ADR-XXX
**Status:** Proposed / Accepted / Superseded
**Prerequisite For Slice:** Slice X
**Context and Requirement IDs:**
**Options Evaluated:**
**Decision:**
**Why / Tradeoffs / Risks:**
**Security & Privacy Implications:**
**Implementation Boundary:**
**How Tested:**
**Approval Date:**
**Revisit Conditions:**
```
