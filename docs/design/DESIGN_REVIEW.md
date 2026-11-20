# Editable UI/UX Review Plan — 26 Screens + 8 Supporting Flows

**Status:** 26 dark/light static screen drafts and 8 interaction flow drafts exist; **editable Stitch/Figma handoff and comprehensive state review remain open**. The master Google Drive document provides the detailed copy/components. Do not infer implementation-ready UI directly from the images.

## Approved visual principles
- Brand lockup: **Anti Burnout** / **AI Habit Tracker & Coach**. Campaign phrase: **Small Steps. Real Momentum.** Snowball Effect stays in onboarding, not under the logo.
- Brand symbol: mountain and path with snowball physically on the path, **no star**.
- Primary colors: dark canvas `#0B0E14`, dark surface `#131826`, light canvas `#F5F7FA`, light-mode deep purple `#4B2BB9`, dark-mode button purple `#5B3DE0`, light lavender highlights `#AC98FF` (not small text on white).
- Green `#22C55E` full original completion; yellow `#F59E0B` agreed smaller commitment; red `#EF4444` missed. Need text/icons in addition to colors.
- Manrope primary; Inter optional for dense data. Dynamic type, 44-point iOS and 48dp Android touch target goals, WCAG 2.2 AA contrast, reduced motion, screen reader semantics.
- Coach avatar is **the AI**, not a profile avatar. Two age-neutral original character choices, user-set name, three modes (Easy/Medium/Hard). Text-based beta with optional pre-rendered expressions.

## Design workflow — per approved screen
1. Import approved product copy and full-size reference screenshot into Stitch or Figma; specify dark/light frame sizes and safe areas.
2. Build with reusable tokens/components: logo, type, button, input, focus, nav, habit row, status chips, quota strip, coach message, banner, modal, error/empty/loading skeleton.
3. Define all supported states and interactions; link source/destination screens; preserve back/cancel paths.
4. Compare with master for copy, semantic accuracy, hierarchy, overflow and contrast.
5. Run accessibility preview at enlarged text and reduced motion; capture evidence.
6. Record version link, owner feedback, unresolved issues and explicit approval. No production implementation without approval.

## Screen inventory and component focus

| Screen | Primary component or flow | Editable visual + interactions | Alt states and accessibility | Owner approved |
| --- | --- | --- | --- | --- |
| 01 Welcome | Brand, coach duo, headline, sign-in CTAs | [ ] | [ ] | [ ] |
| 02 Snowball Effect | Progressive story visual, short explainer, next/skip | [ ] | [ ] | [ ] |
| 03 Account Access | Apple/Google/email, validation, password reset | [ ] | [ ] | [ ] |
| 04 Coach Selection | Coach character, name, Easy/Medium/Hard | [ ] | [ ] | [ ] |
| 05 First Week | Saved first commitment, week calendar, next due | [ ] | [ ] | [ ] |
| 06 Today | Due habits, green/yellow/missed actions, weekly glance | [ ] | [ ] | [ ] |
| 07 My Habits | Active/paused/archive, quota, add, empty/search | [ ] | [ ] | [ ] |
| 08 Insights | Honoured consistency versus original completion | [ ] | [ ] | [ ] |
| 09 AI Coach | Avatar, mode, messages, quick prompts, consent | [ ] | [ ] | [ ] |
| 10 Habit Goal | Goal name, original target, unit, category | [ ] | [ ] | [ ] |
| 11 Schedule/Minimum | Daily/fixed/weekly quota, minimum, reminder | [ ] | [ ] | [ ] |
| 12 Review Commitment | Confirm original/minimum/schedule/rules | [ ] | [ ] | [ ] |
| 13 Habit Detail | Habit history, next due, edit/pause/archive | [ ] | [ ] | [ ] |
| 14 Habit History | Real sessions, status, XP audit, protection | [ ] | [ ] | [ ] |
| 15 Detailed Insights | Filtered trends and interpretations | [ ] | [ ] | [ ] |
| 16 AI Proposal Review | Old/new target, impacts, accept/decline | [ ] | [ ] | [ ] |
| 17 Progress and Levels | Level, earned XP, milestones, explanation | [ ] | [ ] | [ ] |
| 18 Recovery & Shields | Wallet, shield/comeback/pause/history | [ ] | [ ] | [ ] |
| 19 Profile | Display name, account and milestones | [ ] | [ ] | [ ] |
| 20 Settings | Settings categories and navigation | [ ] | [ ] | [ ] |
| 21 Appearance | Dark/light/system, text, reduced motion | [ ] | [ ] | [ ] |
| 22 Reminders | Per-habit notifications and quiet hours | [ ] | [ ] | [ ] |
| 23 Privacy & Data | AI context, consent, export, deletion | [ ] | [ ] | [ ] |
| 24 Plus | Free/paid, price, cancellation, restore purchases | [ ] | [ ] | [ ] |
| 25 Help & Feedback | Definitions, support, reporting | [ ] | [ ] | [ ] |
| 26 Coach Preferences | Character, coach name, mode and responses | [ ] | [ ] | [ ] |

## Eight supporting flow reviews

| Flow | Requirement | Connected prototype | Error/cancel/privacy tested |
| --- | --- | --- | --- |
| F01 Full green | Confirm original target and correct award/feedback | [ ] | [ ] |
| F02 Yellow renegotiation | User confirms reduced goal before logging; XP not pre-awarded | [ ] | [ ] |
| F03 Missed/below minimum | Show actual effort and streak consequences truthfully | [ ] | [ ] |
| F04 Manual shield | Check balance/eligibility, confirm, preserve only not increment | [ ] | [ ] |
| F05 Comeback | Explain eligibility, interrupted history and revival action | [ ] | [ ] |
| F06 Emergency pause | Choose time, extend/restart; no paywall or evidence demand | [ ] | [ ] |
| F07 XP explanation | Transparent ledger, qualified/unqualified distinctions | [ ] | [ ] |
| F08 Notification permission | Opt-in after contextual explanation, denial/retry | [ ] | [ ] |

## Critical end-to-end prototype journeys
- New user sees coach → creates account → chooses character/mode → creates one habit → sees a genuine first-week summary.
- Green check-in versus approved 60→30 yellow; no award on merely choosing reduced target; user's confirmation required.
- Flexible quota across distinct days, midweek progress and week-end evaluation.
- Missed due opportunity → shield or comeback → history remains truthful.
- Sick user starts emergency pause and later resumes without false completions.
- AI suggests change → review shows original vs proposed → decline/accept and navigate back.
- Free user sees core recovery, while optional premium upsell never blocks basic functionality.
- Sign-in recovery and offline error/retry states.

## Review record template
**Screen ID / version URL:**  
**Reviewed date / owner:**  
**Light/dark screenshots:**  
**Status:** Draft / Changes requested / Approved  
**Copy and components match source:**  
**States and navigation verified:**  
**Accessibility findings:**  
**Remaining issues:**  
**Related product decision IDs:**  
