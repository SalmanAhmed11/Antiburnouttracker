# Current State — Anti Burnout

**Last documented review:** 2026-11-20 (Phase 0B merged; Phase 0D memory update prepared)
**Phase:** Phase 0 (Environment Audit & Governance Baseline) COMPLETED; next approved task is assessing workstation permissions and preparing portable Flutter SDK.
**Production code:** NOT STARTED (strictly no application code).
**Source of truth:** GitHub repository (`https://github.com/SalmanAhmed11/Antiburnouttracker`) is the source of truth for all project documentation and engineering memory.

## Confirmed progress
- Core product: Snowball Effect; low-pressure accountability and user-controlled action.
- Four primary tabs planned: Today, Habits, Insights, Coach.
- Two original semi-realistic AI coach choices; optional custom name; Easy/Medium/Hard tone, with user approval for meaningful actions.
- Product status semantics and scheduling models established; numerical game balance still provisional.
- Brand direction and dark/light visual concept reviewed positively by owner; mountain/path/snowball logo with **no star**, high-contrast purple in light theme.
- 26 screen templates and eight supporting interaction flows drafted in dark and light theme, with design requirements and a browser design preview.
- Phase 0 read-only environment audit completed (Git, Android Studio, Android SDK, OpenJDK 21, Node.js/npm verified).
- Phase 0B project-continuity documentation (18 files including `AGENTS.md`, `.gitignore`, `ROADMAP.md`, `PRODUCT_BASELINE.md`, `DECISION_REGISTER.md`, architecture backlog, and review prompts) committed and merged to `main` via PR #1 (`d17f592`).
- GitHub repository is established as the primary source of truth for project documentation.

## Not yet approved / blocked
- Flutter/Dart environment setup remains outstanding (Flutter SDK not installed / not on PATH, no AVD configured, Android SDK licenses pending).
- Editable UI/UX validation (Stitch/Figma handoff, component library, state review) remains outstanding.
- Outstanding product edge cases, premium price figures, AI usage quotas, and numerical level thresholds remain OPEN in `DECISION_REGISTER.md`.
- Architecture ADRs, database schema, API contracts, threat model, automated test strategy, and release runbook not yet written.
- No production app code has been created or authorised.

## Active next task (one task only)
**Assess university-PC installation permissions and prepare a portable Flutter SDK setup.** Check local file permissions, user-profile persistence, and execute a non-administrative, portable extraction and PATH configuration strategy without breaking university IT policies.

## Following gate, not yet authorised
After workstation permissions and portable Flutter SDK setup are verified, proceed with `flutter doctor -v`, Android SDK license acceptance, and virtual device configuration. Editable UI/UX handoff review follows in Phase 1/Gate 1.

## Source references
- Source Drive folder: https://drive.google.com/drive/folders/1hcZw4raqxOxpev9Ke0ZVNT0z8g7tDNAe (master designs and documents)
- Repo: https://github.com/SalmanAhmed11/Antiburnouttracker (source of truth for engineering memory)
- Rules: `AGENTS.md` (mandatory agent instructions)
- Product baseline: `docs/product/PRODUCT_BASELINE.md`
- Decision register: `docs/product/DECISION_REGISTER.md`

## Session record
- Most recent session record: [`docs/operations/sessions/2026-11-20-phase0-continuity-baseline.md`](sessions/2026-11-20-phase0-continuity-baseline.md) (records Phase 0 audit, Phase 0B baseline import, PR #1 merge, and Phase 0D status update).

## Last read-only Antigravity audit — 2026-11-20
- Repository: `C:\Users\k2554693\Antiburnouttracker`; remote `origin/main` synchronized.
- Tooling verified present: Git 2.45.1, Node 26.12.1, npm 11.20.0, Android Studio 2024.3.2, Android SDK platforms 33-36, OpenJDK 21, Android emulator engine.
- Tooling missing: Flutter/Dart SDK, Android Virtual Device (AVD), Android SDK licenses unaccepted.
- Workstation constraint: University PC environment; verify local permissions and portable setup strategy before installing tools.
