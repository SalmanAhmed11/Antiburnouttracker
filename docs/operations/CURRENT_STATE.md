# Current State — Anti Burnout

**Last documented review:** 2026-11-23 (Slice 0 owner architecture approval & controlled initial implementation authorisation)
**Current governance:** Progressive slice-scoped SDLC merged via PR #4; Gate 0 outstanding controls remain DRAFT.
**Application code:** NOT STARTED. No build, tests or infrastructure deployment claimed.
**Source of truth:** https://github.com/SalmanAhmed11/Antiburnouttracker

## Verified project history and scope
- PR #1 — project continuity baseline merged 2026-11-20.
- PR #2 — status/session handoff merged 2026-11-20.
- PR #3 — verified toolchain/native strategy baseline merged 2026-11-20.
- PR #4 — progressive SDLC seven-slice roadmap merged 2026-11-23, `main` observed at `13fbce23f530e5803c85097468be79c1657469e1` before preparing this documentation.
- Native Android and iOS Flutter app only, shared Dart codebase; no Flutter Web/PWA/Cloudflare beta.
- Product baseline: Snowball Effect; Today/Habits/Insights/Coach; 100 reference XP Green; negotiated qualifying Yellow proportional XP; 600 XP per shield, two wallet max; free indefinite manual pause. Edge-case XP, weekly and monetisation decisions not silently resolved.
- Dynamic AI Coach will generate contextual conversations; only typed proposals subject to independent server validation and explicit user consent. Supabase remains a preferred candidate requiring later ADR approval; none is provisioned.
- MVP animations: lightweight onboarding, essential microinteractions, static/pre-rendered Coach visual acceptable. Accessibility and reduced-motion checks start in Slice 0.
- Manual Stitch dark/light designs exist for 26 screens and 8 flows. Six original HTML exports for screens 01/06/21 (both modes) were inspected for token extraction in `docs/design/DESIGN.md`; native artwork/fonts and screen fidelity need separate review.

## Owner decisions on 23 November 2026
- **ADR-001 ACCEPTED for Slice 0:** Option A — Flutter SDK-first feature-oriented MVVM with built-in state mechanisms (`ChangeNotifier`/`ValueNotifier`) and constructor injection; reevaluate at Slice 1.
- **ADR-002 ACCEPTED for Slice 0:** Option B — `go_router` with `StatefulShellRoute.indexedStack`; exact compatible dependency version must be reviewed before package installation.
- **Slice 0 scope:** Welcome, four-tab navigation shell, Appearance theme setting, verified design tokens, accessibility and native Android build checks. No production authentication, backend, AI, XP, habit domain, subscriptions or unreviewed assets.
- **S0-A ONLY is owner-authorised:** inspect tools and clean repository, prepare minimal native Flutter scaffold, run actual baseline checks and an Android smoke-test build. This permission becomes effective **after this documentation pack is reviewed and merged**. S0-B/C/D are not yet authorised.
- Historical numerical PD-01/05 details remain OPEN as documented; the owner chose progressive decisions before each relevant slice, not all 18 before building a shell.

## Current workstation uncertainty
- Antigravity workspace last observed at `C:\Users\k2554693\.gemini\antigravity\scratch\Antiburnouttracker`, but must be reverified on use.
- Flutter 3.50.1/Dart 3.14.0 were verified on 2026-11-20. After the university-PC session reset, Flutter files were reported missing; do not assume current installation or PATH is working.
- Android Studio 2024.3.2 and Android SDK APIs 33–36 were previously observed, licenses accepted. Android emulator/device running and native APK build remain unverified.
- iOS build requires macOS/Xcode or approved hosted macOS environment; Windows can maintain Flutter/iOS source but cannot verify native iOS compilation.
- `gh.exe` credential-helper path previously failed, while ordinary `git push` subsequently succeeded. Do not infer a working GitHub CLI.

## Outstanding gates and blockers
- Gate 0: GitHub branch protections, reviewed project-specific skills. Do not mark complete without evidence.
- Slice 0: merge this documentation pack; owner verify native assets/font usage; after S0-A, approve S0-B/C scope. ADR-001/002 are owner-selected; no build tests have been executed.
- Later slices: ADR-003..012 and relevant PD questions remain pending slice-specific review. No backend or external beta authorisation.

## Single next task
**Publish this documentation pack on a topic branch and merge through an owner-reviewed PR. Once merged, execute only S0-A (native Flutter scaffold + Android toolchain smoke test) with real terminal evidence and a separate implementation PR.**

## Next step not yet authorised
S0-B theme tokens/native UI implementation, S0-C full shell/welcome, S0-D further polish, and all Supabase/AI/product logic require separate explicit owner approval.

## References
- `AGENTS.md`
- `docs/ROADMAP.md`
- `docs/product/PRODUCT_BASELINE.md`
- `docs/product/DECISION_REGISTER.md`
- `docs/design/DESIGN.md`
- `docs/design/DESIGN_REVIEW.md`
- `docs/architecture/ARCHITECTURE_PLAN.md`
- `docs/architecture/decisions/ADR-001-flutter-foundation.md`
- `docs/architecture/decisions/ADR-002-navigation-routing.md`
- `docs/quality/SLICE0_ACCEPTANCE.md`
- `docs/quality/TEST_SECURITY_RELEASE.md`
- `prompts/000-resume-project.md`
