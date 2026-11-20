# Product Decision Register — Proposed, Not Automatically Approved

**Owner update:** 20 Nov 2026 — nine product directions and four-tier subscription structure selected. This table is a decision register, not a complete implementation-ready specification.

**Rules:** `LOCKED` = explicitly owner-approved. `WORKING` = existing proposal awaiting approval. `OPEN` = decision to make. `DEFERRED` = out of initial beta. A recommendation below is **not** a locked decision. Update `Decision`, `Owner approval date`, `Reason`, `Tests` when a decision is settled. Do not convert a proposed value into code merely because it appears here.

| ID | Topic | Current status | Recommendation / alternatives to review | Must specify before code? |
| --- | --- | --- | --- | --- |
| PD-01 | Base XP and effort measurement | LOCKED direction / OPEN measurement edge cases | Retain full completion = 100 reference XP, reduced completion proportional; decide whether non-measurable habits use explicit binary steps and rounding | Yes |
| PD-02 | XP abuse, multiple habits, level curve | LOCKED increasing curve / OPEN concrete thresholds | Simulate 1, 3 and 10 habits/week before deciding XP caps, bonus thresholds, names and shield economy. Avoid rewarding creating dummy habits | Yes for gamification |
| PD-03 | Daily/fixed/weekly streak accounting | LOCKED dual quota modes / OPEN edge cases | Daily/fixed: evaluate only scheduled opportunities; flexible quota: successful weeks. A qualifying yellow counts as honoured, not full green | Yes |
| PD-04 | Weekly quota boundary/partial weeks | OPEN | Proposed: defined week in user's configured timezone; weekly quota checked at period close, not midweek; decide onboarding partial-week handling | Yes |
| PD-05 | Repeated sessions / duplicate submissions | OPEN | Proposed: only distinct eligible sessions count; initial beta limit one qualifying session per habit per local day unless specified; require idempotency | Yes |
| PD-06 | Yellow renegotiation timing | LOCKED principle / OPEN cutoff | Must be chosen before marking reduced work complete; decide whether last-minute negotiation and same-day corrections need a grace period | Yes |
| PD-07 | Below-minimum effort | LOCKED distinction / OPEN scoring | Partial effort is not qualifying streak/full completion. Proportional XP is permitted in working plan; decide precise rules and display name | Yes |
| PD-08 | Shield earn rate, wallet, max consecutive | LOCKED selected Option A / OPEN economy validation | 600 XP earns 1 shield; max 2 stored; manual use; up to 2 consecutive eligible missed scheduled commitments. Test economy before implementation | Yes |
| PD-09 | Shields on flexible weekly quota | OPEN | Recommended: protect one missing quota opportunity at week close only if eligible; clarify multiple shortfalls and usage window | Yes |
| PD-10 | Comeback eligibility | LOCKED restore + badge / OPEN timing | Restore continuity after qualifying return and award comeback badge; missed history retained. Define missed-opportunity window, elapsed time and cooldown | Yes |
| PD-11 | Emergency pause | LOCKED indefinite manual resume / OPEN boundaries | Free pause until user explicitly resumes; no XP/false completion. Define retrospective coverage, reminders, restarts | Yes |
| PD-12 | Account authentication/recovery | LOCKED provider direction / OPEN workflows | Apple/Google and passwordless email codes; verified provider linking and fallback recovery. Define lost-access, deletion and abuse controls | Yes |
| PD-13 | Offline and sync conflict policy | LOCKED offline A / OPEN conflict policy | Cached reads and queued check-ins; XP final only after trusted server receipt. Define retries/idempotency and UX for pending vs confirmed | Yes |
| PD-14 | AI context, consent and chat retention | LOCKED explicit consent / OPEN retention | Optional personalised context/memory, user permission and deletion controls; retention and provider processing details need decisions | Yes |
| PD-15 | Coach modes and boundaries | LOCKED core / OPEN UX | Easy/Medium/Hard only changes tone; decide default, mode-change confirmation and response settings; non-clinical safety in all modes | Yes |
| PD-16 | Four-tier features and AI limits | LOCKED structure / OPEN pricing | Free / Starter / Plus / Premium; unlimited basic habits and recovery free, premium AI/insights. Example prices and usage allowances remain UNAPPROVED | Yes for billing |
| PD-17 | Initial beta feature scope | OPEN | Decide whether side quests, campfire, weekly care packages, streak multipliers, leaderboards are deferred. Do not implement historical brainstorming by accident | Yes |
| PD-18 | Notifications, times and timezones | OPEN | Decide quiet hours, DST, travel/timezone changes, missed-day cutoffs, daily reminder consent; avoid silent streak changes | Yes |

## Suggested review order — approval interviews

### Round A — XP and habit accounting (PD-01 through PD-07)
- How should fractional or subjective habits be scored (minutes, chapters, sessions, tasks)?
- Which records count as a qualified opportunity? Can a habit have >1 qualifying session per day?
- For a weekly target of three sessions, if two are green and one is qualifying yellow, the quota is achieved while full achievement is 2/3. Confirm this stays true across week boundaries.
- When a user creates a weekly quota on Saturday, should it begin in the next full week or require a prorated introductory week?
- How should a user correct a genuine mistaken entry while preserving the audit history?

### Round B — Recovery economics (PD-08 through PD-11)
- Should a shield protect one missed *opportunity* or a whole calendar day containing multiple habits? (Recommendation: one opportunity, visible choice.)
- For a flexible quota shortfall, how many shields can be spent at the deadline and when should the user be prompted?
- How long can a comeback revive a broken streak; what qualifies as proof of return?
- During illness, is a pause future-only or can it cover recent missed scheduled opportunities? (Recommend reasonable retrospective exception, with explicit history marker.)

### Round C — Accounts, offline and AI (PD-12 through PD-15)
- Which sign-in methods must be in the first beta? What happens when email/SSO providers are unavailable?
- Should check-in actions be queued offline, or only drafted pending connection? How do we show pending vs confirmed XP?
- What personal data may the coach use; for how long may chat history be stored and who can delete it?
- What does Hard mode do in a health, illness or vulnerability-related conversation? (Firm tone must never override safety.)

### Round D — Subscription and launch scope (PD-16 through PD-18)
- Can a free user complete the entire core habit/recovery journey? (Must be yes.)
- What recurring premium benefit is sufficiently valuable to pay for, and at what cost per user?
- Which proposed gamification features are deferred to maintain simplicity?
- How do reminders, timezone changes, and user-controlled quiet hours interact with due dates and weekly boundaries?

## Testable examples to include with approved decisions
- 60 min promised and 60 logged: full green / reference 100 XP.
- 60 min promised and 30 min *approved before completion*, with user minimum ≤30: yellow / reference 50 XP / honoured but not full.
- 60 min promised and 10 logged below user minimum: partial effort / no honoured streak; XP policy open.
- 3 weekly sessions: two green plus qualifying yellow = 3/3 consistency, 2/3 full original achievement.
- Two habits due same day: one green and one red are separate outcomes, not a single global day colour.
- Shielded miss: 0 XP and protection marker, no forged completion.
- Replay, double tap and two-device concurrency must never double-award confirmed XP.

## Decision template (copy under this line)
**ID:** PD-XX  
**Decision:**  
**Status:** OPEN → LOCKED only after user approval  
**Alternatives:**  
**Why:**  
**Approval date/reference:**  
**Affected screens and API/data rules:**  
**Acceptance tests:**  
**Revisit trigger:**  
