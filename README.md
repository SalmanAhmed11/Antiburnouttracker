# Anti Burnout — AI Habit Tracker & Coach

> **Small Steps. Real Momentum.**

The goal of the Anti-Burnout Tracker is not to make people stop working out, stop doing laundry, or stop building their careers. The goal is to get them to do all of those things by changing the psychological framing from a high-stakes, life-or-death obligation into a low-stakes, highly rewarding game.

**Status (2026-11-20):** Product and visual design reference work exists. There is **no production app code**. Selected XP, quota, shield, comeback, pause, authentication, offline, AI privacy and four-tier structure directions have been approved; remaining edge cases, prices and editable design handoff are not final. This repo is the source-controlled engineering memory; approved product design artifacts are currently stored separately in the project owner's Google Drive.

## First stop on every new computer or agent session

1. Read [`AGENTS.md`](AGENTS.md) (Antigravity loads it as a workspace rule; read it explicitly if needed).
2. Read [`docs/operations/CURRENT_STATE.md`](docs/operations/CURRENT_STATE.md).
3. Review [`docs/product/PRODUCT_BASELINE.md`](docs/product/PRODUCT_BASELINE.md) and [`docs/product/DECISION_REGISTER.md`](docs/product/DECISION_REGISTER.md).
4. Consult [`docs/ROADMAP.md`](docs/ROADMAP.md), then take **only the currently approved next task**.
5. At the end of the session update the current state, relevant checklist and a short session record; commit and push the changes before leaving the machine.

## Project navigation

| File | Why it exists |
| --- | --- |
| `AGENTS.md` | Always-on agent safety and workflow constraints |
| `docs/operations/CURRENT_STATE.md` | Living handoff, current stage, blockers, next one task |
| `docs/ROADMAP.md` | End-to-end phase and acceptance-gate plan |
| `docs/product/PRODUCT_BASELINE.md` | Confirmed product identity and core rules |
| `docs/product/DECISION_REGISTER.md` | Remaining product decisions, proposals, and sign-off fields |
| `docs/design/DESIGN_REVIEW.md` | Editable design handoff and screen-by-screen validation |
| `docs/architecture/ARCHITECTURE_PLAN.md` | ADR backlog and required technical design artifacts |
| `docs/quality/TEST_SECURITY_RELEASE.md` | Quality, threat modelling and release criteria |
| `docs/operations/UNIVERSITY_PC_WORKFLOW.md` | Safe, repeatable routine for temporary machines |
| `docs/operations/sessions/TEMPLATE.md` | Compact evidence-based session handoffs |
| `prompts/` | Versioned, reusable approved prompts (not raw entire chat histories) |

## Product boundaries

- **Snowball Effect:** A manageable start can create voluntary momentum. No pressure to overexert.
- Two original expressive AI Coach characters; users choose a coach/name and Easy, Medium or Hard communication mode. Coach suggests; user approves actions.
- Green = original commitment fully met. Yellow = agreed smaller goal and proportional XP; qualifying minimum rule. Red = missed. Shields/comebacks/pauses do not fabricate completion.
- Daily, fixed-day and flexible weekly-quotas; preserve original full-achievement versus honoured-consistency metrics separately.
- Brand: mountain + path + **snowball on the path; no star**; descriptor `AI Habit Tracker & Coach`; tagline `Small Steps. Real Momentum.`; Snowball Effect is philosophy, not logo subtitle.
- Both dark and light themes; higher-contrast deep purple on light backgrounds.

## Where the original assets live

The *Anti Burnout* Google Drive project folder stores the master product/design document and original UI/UX design ZIP. This repository currently holds a text-only working baseline and a review checklist **not a faithful replacement for those complete assets**. The owner must import/link approved editable Stitch/Figma project files and versioned exports during the design handoff.

**Google Drive project folder:** https://drive.google.com/drive/folders/1hcZw4raqxOxpev9Ke0ZVNT0z8g7tDNAe (access controlled separately).

## Repository conventions

- `main` should contain reviewed, approved work. Changes through small topic branches and pull requests.
- Do not commit API keys, tokens, credentials, `.env` files, real users' health/AI chats, proprietary university files, or complete private AI chat transcripts.
- Never say a document is implemented, tested or locked unless there is evidence and approval.
- GitHub does not sync Antigravity global installations or chat history; repo files/skills and committed artefacts are the portable memory.
- No code generation or install steps are authorised merely by opening this repository.

**Audited workstation:** see [`docs/operations/PHASE0_AUDIT_SUMMARY.md`](docs/operations/PHASE0_AUDIT_SUMMARY.md).
