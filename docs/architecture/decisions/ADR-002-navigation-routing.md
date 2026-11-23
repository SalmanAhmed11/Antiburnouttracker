# ADR-002 — Routing and Native Tab Navigation

**Status:** ACCEPTED choice for Slice 0 (owner approval 2026-11-23; version pending verification)
**Drafted:** 2026-11-23
**Required for:** Slice 0
**References:** `docs/design/DESIGN_REVIEW.md`, Stitch Today screen 06, `docs/ROADMAP.md`.

## Context

The primary destinations are **Today, Habits, Insights, Coach**. The Welcome/onboarding flow is outside the four-tab shell. In later slices, habits have detail/edit flows, the AI has a proposal-review flow, and authenticated routes and deep links may be needed. Navigation should preserve tab state, support native back, and remain testable.

## Alternatives

| Option | Strengths | Tradeoffs |
| --- | --- | --- |
| A. Flutter SDK `Navigator` + `NavigationBar` + `IndexedStack` | Zero package dependency, adequate for a simple tab demo | Custom handling for nested independent stacks and deep links; likely refactor later |
| B. `go_router` `StatefulShellRoute.indexedStack` + Flutter `NavigationBar` | Separate tab navigators, scalable routing/deep link semantics, supported ecosystem examples | Explicitly approve and pin one package; some routing complexity in Slice 0 |
| C. Custom RouterDelegate/Navigator 2.0 | Full control | Unnecessary implementation/testing cost without a special requirement |

## Accepted decision — Option B

**OWNER APPROVED: Option B:** `go_router` with a `StatefulShellRoute.indexedStack`, using native Material 3 `NavigationBar` styled with verified Stitch tokens. Supports distinct navigation history per tab as the app grows. The exact `go_router` version is **not selected**; verify current Flutter/Dart compatibility and review the precise stable package version and dependency diff before installing it. This approval covers the library selection, not an unverified version.

Sources:
- https://docs.flutter.dev/ui/navigation
- https://pub.dev/documentation/go_router/latest/go_router/StatefulShellRoute-class.html
- https://github.com/flutter/packages/blob/main/packages/go_router/example/lib/stateful_shell_route.dart

If the university workstation cannot install the approved package, surface Option A as a deliberate fallback; never silently change this ADR.

## Proposed route concepts (not immutable public URLs)

| Screen | Sample path | Layout | Slice 0 truthfulness |
| --- | --- | --- | --- |
| Welcome (01) | `/welcome` | Outside tabs | Approved welcome copy and reviewed visual assets; sign-in cannot pretend to work |
| Today (06) | `/today` | Tab 0 | Clearly labelled preview or empty state; no fake real progress |
| Habits | `/habits` | Tab 1 | Accessible empty/preview state |
| Insights | `/insights` | Tab 2 | No fabricated analytics |
| Coach | `/coach` | Tab 3 | No scripted fake "live AI" claims |
| Appearance (21) | `/appearance` | Outside tab bar or stacked above existing branch | Returns to previous destination |

Route shapes, auth callbacks, notification links and public deep links remain **proposals** and require further review in their own slices.

## Navigation invariants and checks

1. Selecting each tab reveals the correct destination and active state, with text/semantics not colour alone.
2. Switching between tabs maintains intended branch navigation and avoids duplicate bottom bars.
3. Opening Appearance and returning preserves the previous route.
4. Android back handling respects nested navigation and exits predictably; iOS back affordances are coherent.
5. Tab labels and actions remain usable at enlarged system text on narrow screens.
6. Onboarding/Welcome is separated from authenticated destinations; Slice 0 previews do not imply users are signed in.
7. Reduced-motion behaviour changes nonessential transitions appropriately for Android/iOS accessibility preferences.
8. Later auth guards and protected deep links must check authorization, not trust route parameters.

## Approval record

**Owner-selected option:** Option B (`go_router` with `StatefulShellRoute.indexedStack`), confirmed 2026-11-23.
**Third-party dependency:** `go_router` approved in principle for Slice 0; exact version and dependency diff require explicit review before installation.
**Compatibility/version:** PENDING real workstation verification.
**Owner approval date:** 2026-11-23.
**Validation:** `docs/quality/SLICE0_ACCEPTANCE.md`.
