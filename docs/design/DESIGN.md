# Anti Burnout — Slice 0 Design Token Handoff

**Status:** DRAFT / SOURCE-VERIFIED VALUES / NOT YET OWNER-SIGNED-OFF
**Date:** 2026-11-23
**Purpose:** Provide precise native Flutter design-system inputs without inventing visuals.

## Source evidence

Directly inspected six actual `code.html` Stitch exports in the connected **Anti Burnout** Google Drive folder:

| Screen | Dark-theme folder | Light-theme folder |
| --- | --- | --- |
| 01 Welcome | `screen_01_welcome_dark` | `01_welcome_light` |
| 06 Today | `screen_06_today_home_dashboard` | `06_today_light` |
| 21 Appearance | `screen_21_appearance_accessibility` | `21_appearance_accessibility_light` |

The same shared Tailwind token configuration was observed in **all six**. Source folder: https://drive.google.com/drive/folders/1hcZw4raqxOxpev9Ke0ZVNT0z8g7tDNAe . Other screens/flows, imagery and native font assets have **not** been fully validated in this pass. The six exports are HTML visual references, **not** Flutter source files or approved native assets. No UI has been implemented or tested.

## Approved brand direction (repository baseline)

- Product: **Anti Burnout** / **AI Habit Tracker & Coach**. Campaign phrase: **Small Steps. Real Momentum.**
- Mountain/path logo with round snowball resting on path, **no star**. Native asset is still pending separate verification.
- Four primary tabs: **Today, Habits, Insights, Coach**. Coach avatar represents the AI Coach, not the user profile.
- Dark, light and system appearance modes; Manrope primary, Inter body/supporting.
- Green, yellow and red meanings must include text/icons, never only colour.

## Verified colour tokens in all six exports

| Source token | Hex | Proposed Flutter semantic use |
| --- | --- | --- |
| primary | `#5B3DE0` | Dark-theme filled primary action |
| on-primary | `#FFFFFF` | Filled-primary label/icon |
| primary-hover | `#6E52EB` | Dark interactive feedback |
| primary-light | `#4B2BB9` | Light-theme filled primary action |
| primary-light-hover | `#3C218F` | Light interactive feedback |
| lavender | `#AC98FF` | Accent (not normal text on white) |
| on-lavender | `#1A0064` | Text on lavender |
| lavender-light-surface | `#EFEAFF` | Light accent surface |
| light-background | `#F5F7FA` | Light page background |
| light-on-background | `#191C22` | Main text in light mode |
| light-surface | `#FFFFFF` | Light card |
| light-surface-elevated | `#EEF1F7` | Elevated light surface |
| light-on-surface | `#191C22` | Light card text |
| light-on-surface-variant | `#525763` | Secondary light text |
| light-outline | `#DCE1EB` | Light border |
| dark-background | `#0B0E14` | Dark page background |
| dark-on-background | `#FFFFFF` | Main text in dark mode |
| dark-surface | `#131826` | Dark card |
| dark-surface-elevated | `#1C2236` | Elevated dark surface |
| dark-on-surface | `#F4F5F9` | Dark card text |
| dark-on-surface-variant | `#A9ABB3` | Secondary dark text |
| dark-outline | `#2E3037` | Dark border |
| success | `#22C55E` | Green status accent |
| on-success | `#052E16` | Text on green fill |
| on-success-light | `#166534` | Dark green for light-mode label |
| warning | `#F59E0B` | Yellow status accent |
| on-warning | `#451A03` | Text on yellow fill |
| on-warning-light | `#92400E` | Dark amber for light-mode label |
| danger | `#EF4444` | Red status accent |
| on-danger | `#1C1C1C` | Text on red fill |
| on-danger-light | `#B91C1C` | Dark red for light-mode label |

**Contrast warning — calculated 23 Nov 2026 from WCAG sRGB luminance:** `#4B2BB9` on white 8.95:1; `#5B3DE0` on white 6.59:1. Conversely, `#5B3DE0` directly on dark background `#0B0E14` is 2.93:1; green `#22C55E` on white is 2.28:1; yellow `#F59E0B` on white is 2.15:1; red `#EF4444` on `#F5F7FA` is 3.51:1. Therefore **do not use raw status accent green/yellow/red for normal small text on light surfaces**; use approved darker on-light foreground tokens and test actual component contrast. These pair checks do not establish overall WCAG compliance.

## Verified typography and spacing

Font families in six exports: display/headline/title/label = **Manrope**; body = **Inter**, with sans-serif fallback. Font licensing and local Flutter asset bundling must be reviewed; no runtime network-font dependency assumed.

| Text token | Size / line height | Weight / letter spacing |
| --- | --- | --- |
| display-lg | 36px / 42px | 800 / -0.75px |
| display-lg-mobile | 30px / 36px | 800 / -0.5px |
| headline-lg | 34px / 40px | 700 / -0.5px |
| headline-lg-mobile | 28px / 34px | 700 / -0.4px |
| headline-md | 24px / 30px | 700 / -0.3px |
| title-md | 16px / 22px | 600 / 0px |
| body-md | 15px / 22px | 400 / 0px |
| label-md | 14px / 20px | 600 / 0px |
| label-xs | 11px / 16px | 600 / +1.4px |

| Layout token | Source CSS value |
| --- | --- |
| gutter-xs / sm / md / lg / xl | 4 / 8 / 16 / 24 / 32px |
| section / page-margin | 40 / 24px |
| radius-sm / default / md / lg / xl / full | 8 / 12 / 16 / 20 / 24 / 9999px |
| state-change transition | 120ms, ease-out |
| surface-enter transition | 280ms, cubic-bezier(0.2,0,0,1) |

CSS pixels/durations above are **source-observed**; their Flutter logical-pixel/motion mapping requires native verification and accessibility adjustment. Flutter Android `disableAnimations` and iOS `reduceMotion` preferences are not identical and must be tested separately.

## Slice 0 observations for screens 01/06/21

- **01 Welcome:** source text includes “Small Steps. Real Momentum.”, “Your AI coach helps you build habits, find your pace, and keep going.”, “Get Started”, and “I already have an account”. Character/background artwork is present as images; native local, usage-approved asset exports remain open.
- **06 Today:** bottom tab order is Today → Habits → Insights → Coach. Static cards show example commitments/weekly progress; they must **never** appear as confirmed live XP or real personal data in a Slice 0 shell.
- **21 Appearance:** options System / Dark / Light; copy references following system text size, reducing motion and high-contrast labels. Only implemented controls should look functional; deferred controls must be visibly deferred or absent.

## Slice 0 implementation boundaries and open reviews

- Material 3 theme mapping should explicitly preserve source token values; `ColorScheme.fromSeed` alone may not match exact screens.
- In scope: Welcome, four-tab native preview shell, Appearance, light/dark/system themes, accessible essential microinteractions. **No Flutter Web/PWA**.
- Out of scope: real login, persistence, XP/check-ins, AI API, paid features, 3D character animation, embedded remote Stitch HTML.
- Never commit unreviewed Stitch base64 imagery, remote URLs as runtime dependencies, or font files without rights review.

**Required before Slice 0 UI implementation:** owner confirms screen versions/asset choices; validate sample native styling; approve ADR-001 and ADR-002; capture screen/state/overflow review in `docs/design/DESIGN_REVIEW.md`.
