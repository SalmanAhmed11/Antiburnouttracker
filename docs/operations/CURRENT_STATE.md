# Current State — Anti Burnout

**Last documented review:** 2026-11-23 (Progressive SDLC Roadmap & Slice-Scoped Architecture Draft)
**Phase:** Gate 0 (Continuity & Control) in DRAFT; Progressive SDLC Framework DRAFT on branch `docs/progressive-sdlc-roadmap`.
**Production code:** NOT STARTED (strictly no application code authorized; documentation-only draft).
**Source of truth:** GitHub repository (`https://github.com/SalmanAhmed11/Antiburnouttracker`) is the source of truth for all project documentation and engineering memory.

---

## Confirmed Progress & Architectural Direction
- **Progressive SDLC Framework Approved in Principle (2026-11-23):** Transitioned from rigid monolithic waterfall gates to a progressive, slice-scoped delivery model across seven vertical slices (Slices 0–6).
- **Core Product Baseline (LOCKED):**
  - Philosophy: Snowball Effect; low-pressure accountability, voluntary momentum.
  - Primary tabs: Today, Habits, Insights, Coach.
  - Coach selection: Two approachable 3D-looking character choices; custom name; Easy/Medium/Hard tone settings (tone does not modify scoring).
  - Status semantics: Green = target fully met (100 base reference XP); Yellow = negotiated meaningful minimum with proportional XP; Red = missed commitment. Original targets remain historically auditable.
  - Gamification & recovery: 1 shield per 600 XP (max 2 stored, manual use); free indefinite manual emergency pause; comeback badges.
- **Dynamic AI Coach Core Principles:**
  - Dynamic, natural, context-aware dialogue; never static decision trees or scripted responses.
  - Structured proposal tool calling only (`propose_habit_reduction`). Client-side UI confirmation enables informed consent, but the trusted backend independently enforces authentication, RLS tenant isolation, schema/business-rule validation, and idempotency.
  - Authorised database queries for user habit context; RAG clarified as optional retrieval, not prompt-injection security.
- **Platform Strategy (Owner Confirmed):**
  - Native iOS and Android application built using a shared Flutter/Dart codebase.
  - Out of scope: Flutter Web, Progressive Web Apps (PWA), Cloudflare Pages hosting, and separate web-based betas.
  - Workstation constraints: Windows workstation supports Flutter development, testing, and Android builds; native iOS compilation requires macOS/Xcode or an approved hosted macOS build environment; early Android native build verification milestone established in Slice 0.
- **Backend Architecture:** Supabase preferred candidate for auth, PostgreSQL, RLS, Edge Functions, and server-authoritative scoring; evaluated progressively per slice.
- **MVP Interaction & Animation Direction (Owner Confirmed):** Meaningful, dynamic user interactions prioritized over elaborate visual animations. Reusable UI components; animations strictly separated from business logic; no unnecessary animation engines. Approved MVP scope: smooth onboarding transitions, essential microinteractions (navigation, check-in, validation, progress), dynamic LLM dialogue, lightweight coach representation (static portraits or small set of pre-rendered expression states from approved assets), and platform-compliant reduced-motion support (iOS Reduce Motion / Android Remove animations; MediaQuery.disableAnimationsOf is an accessibility query signal, requiring individually designed and tested fallback transitions). Accessibility applies continuously starting from Slice 0. Deferred to post-MVP: complex real-time 3D animations, pet companion environments, avatar gestures, voice-driven animations, and elaborate gamification sequences.
- **Visual Design Baseline:** 26 screen templates and 8 interaction flows drafted in master document; manual Stitch design work completed by owner. Visual token extraction required in Slice 0 (unverified colors remain PROPOSED, not LOCKED).

---

## Progressive Slice Dependency Summary

1. **Slice 0:** Flutter Native Foundation & Design System (`ADR-001`, `ADR-002`, verified Stitch tokens). *Earliest buildable Flutter feature.*
2. **Slice 1:** Habit Domain, Authentication, Scheduling, Secure Check-ins & XP Ledger Foundation (`ADR-003`, `ADR-004`, `ADR-005`, `ADR-006`).
3. **Slice 2:** Early Dynamic AI Coach Proof of Concept (`ADR-008`).
4. **Slice 3:** Yellow Renegotiation, Proportional Scoring & Streak Logic (Extended `ADR-004`).
5. **Slice 4:** Recovery Mechanics (Shields, Emergency Pause, Comebacks) (`ADR-007`, `ADR-012`).
6. **Slice 5:** Insights, Progress, Levels & Complete Journey Polish (`ADR-010`).
7. **Slice 6:** Monetization, Store Compliance & Release Readiness (`ADR-009`, `ADR-011`). *Paid monetization explicitly separated from initial free closed beta.*

---

## Active Next Task (One Task Only)
**Commit and push the Progressive SDLC Roadmap documentation diff on branch `docs/progressive-sdlc-roadmap` for owner PR review. Upon approval, proceed to Slice 0 prerequisites (verify design tokens from Stitch exports, draft ADR-001 and ADR-002).**

---

## Following Step (Not Yet Authorised)
Following owner approval of Slice 0 prerequisites, seek authorization to begin Slice 0 implementation (scaffold Flutter native project shell, configure theme tokens, build 4-tab shell navigation, and verify Android build).

---

## Session Record & Project History
- **PR #1:** Phase 0B Project continuity & governance baseline merged (`4eea302`).
- **PR #2:** Phase 0D Update Phase 0 status and session handoff merged (`fb5e712`).
- **PR #3:** SDLC toolchain baseline & verified environment reconciliation merged on 2026-11-20 (`635c1b8`).
- **Prior session record:** [`docs/operations/sessions/2026-11-20-sdlc-toolchain-baseline.md`](sessions/2026-11-20-sdlc-toolchain-baseline.md).
- **Current session branch:** `docs/progressive-sdlc-roadmap` (progressive SDLC roadmap adoption).

---

## Workstation Environment Status (Distinction: Prior Audit vs. Current Session)
- **Repository:** `C:\Users\k2554693\.gemini\antigravity\scratch\Antiburnouttracker`; remote `origin/main` synchronized at `635c1b8`.
- **Flutter SDK:** Flutter 3.50.1 (stable) and Dart 3.14.0 verified on 2026-11-20 at `C:\Users\k2554693\develop\flutter`. *Current status:* Following a temporary university-PC reset/fresh session, Flutter/Dart is not currently present on this machine's local disk until re-extracted or verified with fresh evidence prior to Slice 0 compilation.
- **Android SDK & Studio:** Android Studio 2024.3.2 and Android SDK platforms (APIs 33–36) present at `C:\Apps\Android`; build-tools and licenses accepted. Native Android build execution and emulator testing remain outstanding (scheduled as Slice 0 milestone).
- **iOS Toolchain:** Native iOS compilation requires macOS/Xcode or an approved hosted macOS build environment (Windows workstation).
- **Plugin & MCP:** Flutter plugin v1.0.7 active; `dart-mcp-server` connected. Official Flutter/Dart skills (25) and `flutter_a11y_agent` subagent available.

---

## Source References
- Repo: https://github.com/SalmanAhmed11/Antiburnouttracker
- Rules: `AGENTS.md`
- Roadmap: `docs/ROADMAP.md`
- Architecture plan: `docs/architecture/ARCHITECTURE_PLAN.md`
- Product baseline: `docs/product/PRODUCT_BASELINE.md`
- Decision register: `docs/product/DECISION_REGISTER.md`
- Design review: `docs/design/DESIGN_REVIEW.md`
- Quality/Security: `docs/quality/TEST_SECURITY_RELEASE.md`
- Code review standard: `prompts/003-code-review.md`
