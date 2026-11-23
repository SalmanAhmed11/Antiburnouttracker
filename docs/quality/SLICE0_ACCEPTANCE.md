# Slice 0 — Acceptance Criteria and TDD Plan

**Status:** OWNER-APPROVED ACCEPTANCE PLAN / NOT RUN (23 November 2026). No application code has been built by preparing this document.
**Scope:** Flutter native Android+iOS shell, Welcome, four-tab preview, Appearance, verified design system, accessibility and early Android build.

## Prerequisites before implementation

- [x] Owner approved ADR-001 Option A and ADR-002 Option B on 2026-11-23. Exact `go_router` version requires compatibility/dependency review before installation.
- [x] Source values were inspected in six Stitch HTML exports for screens 01/06/21.
- [ ] Owner visually approves the native screen mapping, reusable assets and font licences before UI implementation in S0-B/S0-C.
- [ ] Merge the owner-approved updates to `AGENTS.md` and `prompts/000-resume-project.md` with this pack via PR before executing S0-A.
- [ ] Antigravity confirms a **clean repository**, current `main` commit, and working Flutter/Android environment; the university machine may reset between sessions.
- [x] Owner authorised the first narrow S0-A scaffold / native Android smoke-test task on 2026-11-23, effective only after the supporting documentation PR is merged and the current workstation is verified.

## Acceptance tests (test-first where meaningful)

| ID | Required behaviour | Evidence |
| --- | --- | --- |
| S0-01 | Native iOS/Android project structure; no web/PWA build | Repo/platform inventory |
| S0-02 | Exact source-observed dark/light token constants and semantic Material 3 mapping | Unit/widget assertions and owner screenshot comparison |
| S0-03 | System, light and dark themes update without route corruption | Theme widget tests |
| S0-04 | Welcome renders approved product copy and honest CTA states | Widget test and owner visual approval |
| S0-05 | Four bottom tab labels and destinations in order Today/Habits/Insights/Coach | Widget navigation tests and semantics |
| S0-06 | Tab switching and opening/closing Appearance preserve navigation expectations | Navigation tests, Android back checks |
| S0-07 | All non-live content explicitly presented as preview/empty; no false real XP, AI or sign-in | Content inspection tests and owner review |
| S0-08 | Readability and semantic contrast meet WCAG 2.2 AA, not merely nominal colour token use | Pair checks + native visual audit |
| S0-09 | Text scales, small screens, safe areas, minimum touch target sizes and focus/semantics work | Flutter widget tests + manual accessibility inspection |
| S0-10 | Android disable-animations and iOS reduce-motion handling have graceful fallbacks | Widget/simulator/device evidence as available |
| S0-11 | Analysis, formatting, relevant tests and native Android APK build actually execute | Real terminal logs: `flutter analyze`, `flutter test`, `flutter build apk`, `dart format` check |
| S0-12 | Small reviewed PR per approved implementation step; no secrets or unapproved dependencies | Branch diff, lockfile, review |

## Approved phased implementation order — S0-A ONLY authorised conditionally

1. **S0-A (authorised after the documentation merge):** Verify toolchain; create a minimal Flutter native scaffold and Android smoke-test build without user-data, login, AI, or app-domain implementation.
2. **S0-B:** Implement exact reviewed themes and representative components with tests.
3. **S0-C:** Welcome/Today shell/Appearance and four functioning preview tabs, with accessibility tests.
4. **S0-D:** Device review, native build evidence, adjustments, owner sign-off.

Each implementation step requires approved requirements, failing relevant tests where applicable, minimum working code, executed test output, security and accessibility review, and owner review before merge.

## Explicit exclusions

No auth/Supabase, check-ins/XP, AI provider, real habit records, paid billing, real-time 3D avatars, Flutter Web/PWA, production deployment, or unreviewed external assets.

**Owner architecture approval:** APPROVED 2026-11-23 (ADR-001 Option A, ADR-002 Option B, limited to Slice 0).
**Owner permission to start implementation:** S0-A ONLY; conditional on documentation PR merge and workstation verification. S0-B/C/D require separate owner approval.
**Build / test results:** NOT RUN.
