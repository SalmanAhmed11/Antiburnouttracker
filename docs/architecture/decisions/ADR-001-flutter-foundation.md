# ADR-001 — Flutter Architecture & State Boundaries

**Status:** ACCEPTED for Slice 0 (owner approval 2026-11-23; scope-limited)
**Drafted:** 2026-11-23
**Required for:** Slice 0 — Flutter Native Foundation & Design System
**References:** `docs/ROADMAP.md`, `docs/design/DESIGN.md`, `docs/product/PRODUCT_BASELINE.md`.

## Context

Anti Burnout needs one native Flutter/Dart codebase for iOS and Android. Slice 0 implements a visually faithful welcome screen, design tokens, theme switching and four-tab navigation. Future slices bring authentication, Supabase candidate data, server-authoritative XP and an adaptive LLM Coach. We need separation and testability, but not a speculative enterprise architecture or a scripted chatbot.

## Alternatives

| Option | Benefits | Costs/risks |
| --- | --- | --- |
| A. Flutter SDK-first MVVM with Views/ViewModels, constructor injection and `ChangeNotifier`/`ValueNotifier` for local shell/theme state | Smallest initial dependency footprint, well-supported Flutter guidance, easy widget tests | Reevaluate cross-feature async state before Slice 1 |
| B. Feature-oriented MVVM with Riverpod from Slice 0 | Strong async/DI model for future features | New dependency and abstractions for a presentation-only slice |
| C. BLoC plus full Clean Architecture layers across all components | Rigorous explicit state transitions | Overhead and boilerplate without proven Slice 0 value |

## Accepted decision — Option A

**OWNER APPROVED: Option A for Slice 0**, with feature-oriented MVVM separation, constructor-injected dependencies and no new state-management package. This is **not** a permanent rejection of Riverpod/BLoC; evaluate again before Slice 1 when real asynchronous/authenticated state exists.

Flutter's official architecture guide advocates UI views/viewmodels, data repositories/services and dependency injection, with optional domain logic when warranted:
- https://docs.flutter.dev/app-architecture/guide
- https://docs.flutter.dev/app-architecture/recommendations

## Responsibility boundaries

- `app/`: native app root, theme mode and approved router composition.
- `design_system/`: verified semantic colour, type, radius, spacing and responsive tokens, reusable accessible controls.
- `features/welcome/`, `features/shell/`, `features/appearance/`: feature views and minimal ViewModels/controllers where behaviour requires them.
- UI views own visual layout, screen reader semantics and transitions; no XP calculations or direct backend/LLM database access.
- Scope-specific state such as theme selection may be transient (in-memory) for Slice 0; do not promise cross-launch persistence before a later decision.
- No Supabase, auth, offline cache, AI provider integration or real habit domain service is scaffolded as fictional production functionality in Slice 0.
- Data access will use repositories/services after their relevant ADRs; do not create empty architecture boilerplate for future slices.
- Flutter Material 3 `ThemeData`/`ColorScheme` with explicit source-observed tokens; custom `ThemeExtension` only where useful. Exact branded values must not be silently replaced by auto-generated seed tones.
- Essential motion handled in the UI; respect Android `disableAnimations` and iOS `reduceMotion` (see current Flutter API docs).

### Proposed structure (not a command to create unused files)

```text
lib/
  app/
  design_system/
  features/
    welcome/
    shell/
    appearance/
test/
  app/
  design_system/
  features/
```

## Test and approval requirements

- Unit/widget tests for theme switching, clear preview-data boundaries, large type, contrast, semantics, reduced motion and accessible tap targets.
- Native Android compilation and emulator/device launch, real `flutter analyze`, `flutter test` and formatting output from Antigravity (not self-reported).
- Small PRs and no unapproved external dependencies. Owner separately authorises the narrowly bounded S0-A scaffold only after the approved documentation is merged and workstation safety checks pass; later work requires its own slice task and evidence.

**Owner decision:** Option A selected explicitly on 2026-11-23 in the Anti Burnout ChatGPT conversation. Scope: Slice 0 only; later state-management reevaluation retained.
**Approval date:** 2026-11-23.
**Revisit:** Before Slice 1 data/auth state, or earlier if tests demonstrate architectural limitation.
