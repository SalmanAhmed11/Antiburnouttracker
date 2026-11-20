# Current State — Anti Burnout

**Last documented review:** 2026-11-20 (SDLC toolchain baseline & verified environment reconciliation)
**Phase:** Gate 0 (Continuity & Control) in DRAFT pending final branching protections and skill vetting; Gates 1 & 2 ACTIVE.
**Production code:** NOT STARTED (strictly no application code authorized).
**Source of truth:** GitHub repository (`https://github.com/SalmanAhmed11/Antiburnouttracker`) is the source of truth for all project documentation and engineering memory.

## Confirmed progress
- Core product: Snowball Effect; low-pressure accountability and user-controlled action.
- Four primary tabs planned: Today, Habits, Insights, Coach.
- Two original semi-realistic AI coach choices; optional custom name; Easy/Medium/Hard tone, with user approval for meaningful actions.
- Product status semantics and scheduling models established; numerical game balance still provisional.
- Brand direction and dark/light visual concept reviewed positively by owner; mountain/path/snowball logo with **no star**, high-contrast purple in light theme.
- 26 screen templates and eight supporting interaction flows drafted in dark and light theme, with design requirements and a browser design preview.
- **Flutter & Dart SDK verified:** Flutter 3.50.1 (stable channel, engine hash 51379e6df4) and Dart 3.14.0 (DevTools 2.61.0) verified at `C:\Users\k2554693\develop\flutter`.
- **Android toolchain substeps verified:** Android Studio 2024.3.2, Android SDK platforms (APIs 33-36), build-tools, OpenJDK 21, and accepted licenses verified; native build and emulator execution testing remain outstanding.
- **Dart/Flutter MCP connected:** `dart-mcp-server` active via official Flutter plugin v1.0.7 with 14 development tools.
- **Official Flutter/Dart skills available:** 25 skills covering unit testing, widget testing, integration testing, architecture, responsive layouts, coverage, and debugging, plus `flutter_a11y_agent` subagent. No additional Flutter/Dart skill repositories needed.
- **Stitch design work:** Completed manually by product owner; Stitch MCP integration and skills are not required. Complete design validation, component tokens, and accessibility testing remain outstanding.
- **Native Mobile Platform Direction (Owner Confirmed):**
  - **Target platforms:** Native iOS and Android application built using a shared Flutter/Dart codebase; platform-specific implementations only when technically necessary.
  - **Not in current scope:** Flutter Web deployment, Progressive Web App (PWA) delivery, Cloudflare Pages hosting, or a separate web-based beta application.
  - **Testing strategy:** TDD/unit testing, widget/integration testing, local Android emulator/device testing, Google Play internal/closed testing, iOS simulator/device testing when macOS/Xcode is available, and Apple TestFlight testing before public App Store publication.
  - **Workstation constraints:** Current Windows workstation supports Flutter development, analysis, unit/widget testing, and Android development; native iOS compilation requires macOS/Xcode or an approved hosted macOS build environment; no Android emulator or native build has yet been verified.
  - **Backend architecture:** Supabase is the preferred candidate for authentication, PostgreSQL, RLS, Edge Functions, and server-authoritative scoring, preserved for formal evaluation under ADR-003, ADR-004, ADR-006, and ADR-007.
- **Project continuity & governance merged:** Phase 0B (`4eea302`) and Phase 0D (`fb5e712`) merged to `main` via PR #1 and PR #2.

## Not yet approved / blocked (Outstanding Gates)
- **Gate 0 (Continuity & Control):** Branch protection configuration and project-owned skill vetting in `.agents/skills/` remain outstanding; gate status is DRAFT.
- **Gate 1 (Product Rules & Acceptance Criteria):** Unresolved edge cases in `DECISION_REGISTER.md` (PD-01 through PD-18, including non-measurable scoring, boundary cutoffs, shield shortfall timing, and provisional pricing) remain OPEN.
- **Gate 2 (Editable UI/UX & Flow Validation):** Manual Stitch design assets need token extraction into `docs/design/DESIGN.md`, state matrix completion in `docs/design/DESIGN_REVIEW.md`, and accessibility/contrast walkthroughs.
- **Gate 3 (Architecture & Security Design):** Architecture Decision Records (ADR-001 through ADR-012, including Supabase backend boundary), data schema, API contracts, threat model, and test strategy not yet drafted or approved.
- **Gate 4 (Engineering Environment & Slices):** Native Android build execution, emulator testing, CI configuration, and feature code implementation are strictly **NOT AUTHORISED**.

## Active next task (one task only)
**Conduct Round A Product Decision Workshop (addressing unresolved PD-01 through PD-07 edge cases, non-measurable habit scoring, boundary cutoffs, and acceptance criteria in `docs/product/DECISION_REGISTER.md`; note: 100 reference XP for full completion is already LOCKED).**

## Following gate, not yet authorised
After Round A and B product decisions are settled, proceed with Gate 2 editable design validation and Gate 3 Architecture Decision Records (ADR-001 through ADR-012). Implementation slices in Gate 4 require explicit prior gate completion.

## Source references
- Source Drive folder: https://drive.google.com/drive/folders/1hcZw4raqxOxpev9Ke0ZVNT0z8g7tDNAe (master designs and documents)
- Repo: https://github.com/SalmanAhmed11/Antiburnouttracker (source of truth for engineering memory)
- Rules: `AGENTS.md` (mandatory agent instructions)
- Product baseline: `docs/product/PRODUCT_BASELINE.md`
- Decision register: `docs/product/DECISION_REGISTER.md`
- Code review standard: `prompts/003-code-review.md`

## Session record
- Most recent session record: [`docs/operations/sessions/2026-11-20-sdlc-toolchain-baseline.md`](sessions/2026-11-20-sdlc-toolchain-baseline.md) (records toolchain verification, Stitch completion note, native mobile strategy, and code-review workflow addition).

## Verified workstation environment — 2026-11-20
- Repository: `C:\Users\k2554693\Antiburnouttracker`; remote `origin/main` synchronized.
- Flutter SDK: `3.50.1` stable at `C:\Users\k2554693\develop\flutter\bin\flutter.bat`.
- Dart SDK: `3.14.0` bundled at `C:\Users\k2554693\develop\flutter\bin\cache\dart-sdk`.
- Android SDK: API 33-36 at `C:\Apps\Android\Sdk`; licenses accepted; build execution and emulator testing pending.
- Android Studio: `2024.3.2` at `C:\Apps\Android\Android Studio`; JBR OpenJDK 21.
- Plugin & MCP: Flutter plugin v1.0.7 active; `dart-mcp-server` connected.
