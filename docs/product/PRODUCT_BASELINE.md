# Anti Burnout — Product Baseline (Confirmed vs Provisional)

**Source:** Consolidated Product/Brand/UIUX/Engineering Master v3 (20 Nov 2026) and owner follow-up decisions. The master is in the linked Drive folder; these notes are a portable summary. Never claim this reproduces all 79 pages.

## LOCKED — Product identity and design principles
- Name: **Anti Burnout**. Descriptor: **AI Habit Tracker & Coach**. Marketing message: **Small Steps. Real Momentum.**
- Snowball Effect: one manageable action can start voluntary momentum. It is the core philosophy/onboarding story, not a logo tagline.
- Logo: purple mountain and sweeping path, round snowball **resting on path**, **no star**.
- Deep-purple accents on light UI, graphite dark UI, both dark/light/system preferences; Manrope primary and Inter optional supporting type.
- Two original approachable, semi-realistic 3D-looking AI Coach character choices (male/female); users name/select their coach and choose **Easy, Medium or Hard** tone. Hard is firm, not abusive; tone does not alter scoring/rights.
- Primary tabs: Today, Habits, Insights, Coach. Avatar represents the **coach**, not user profile avatar. Text AI first; voice/live high-complexity avatar animation deferred.
- Status rule: **Green** means original target fully met; **Yellow** is a genuinely negotiated smaller target with proportional XP; **Red** is a missed due commitment. The original target remains historically auditable.
- Yellow counts toward a **consistency** streak and weekly quota only if the agreed **meaningful minimum** was met. Full original-target achievements remain a distinct metric.
- Scheduled activity can be daily, fixed days or weekly quota. Unscheduled days are neutral. Multiple habits are tracked independently.
- Shields, comebacks and emergency pauses are manual and cannot falsify completion/XP; pause is accessible without payment/medical proof.
- AI advises and proposes: user must confirm any schedule/target/recovery modification; LLM does not directly grant XP, spend shields or mutate user data.
- Free tier must support meaningful habit tracking and basic recovery; paid AI features may include adaptive coaching/insights, not essential protections.

## OWNER-APPROVED DIRECTIONS — 20 November 2026
These choices were expressly selected by the product owner in conversation on 2026-11-20. They are product directions, not final API schemas or all numeric edge cases.

- **Platform & Delivery:** Native iOS and Android application built using a shared Flutter/Dart codebase; platform-specific implementations only when technically necessary. Flutter Web deployment, Progressive Web Apps (PWA), Cloudflare Pages hosting, and separate web-based betas are **explicitly out of current scope**.
- **Backend Architecture Candidate:** Supabase is the preferred backend candidate (authentication, PostgreSQL, Row Level Security, Edge Functions, server-authoritative scoring), preserved for formal evaluation under ADR-003, ADR-004, ADR-006, and ADR-007.
- **XP:** 100 base XP for a completed original target; proportional XP for an agreed qualifying reduction; level thresholds increase progressively. Exact curve, minimum scoring and anti-farming protections OPEN.
- **Weekly goals:** both session-count and quantity-based quotas supported. Distinct eligible days for session-count goals as a current direction; partial weeks, deadlines and duplicate checks OPEN.
- **Shields:** manually earned and used; **one shield per 600 XP, maximum two stored**; an eligible shielded miss awards no XP. The originally offered Option A specified protection of up to two consecutive scheduled misses. Detailed weekly-shortfall interaction OPEN.
- **Comebacks:** after a genuine qualifying return, continuity may be restored **with a comeback badge**; missed history must remain true, no retroactive XP. Final time window and frequency limits OPEN.
- **Emergency pause:** free, indefinite until explicitly resumed by the user, without XP or false completion. Detailed retrospective/timing rules OPEN.
- **Account access:** Apple and Google plus passwordless email codes, verified provider linking and fallback recovery; technical flows OPEN.
- **Offline:** cached viewing and queued check-in actions; only validated server confirmation makes XP final. Conflict/idempotency policy OPEN.
- **AI privacy:** explicit contextual authorisation, optional long-term memory and user deletion controls; precise retention and data-sharing detail OPEN.
- **Freemium:** unlimited basic habit tracking, truthful progress and recovery free. Paid plans differentiate AI personalisation and advanced insights.
- **Tier structure:** **Free / Starter / Plus / Premium** and high-level feature boundaries accepted. **£2.99/£4.99/£9.99 monthly and all annual prices remain proposals**, pending costs, market testing and user approval. Do not represent pricing as final.

## WORKING — Open balances and mechanics
- Full-completion baseline and proportional yellow scoring are approved directions; **exact progression thresholds**, XP caps, below-minimum scoring and rounding remain OPEN.
- Earlier 50/25 XP, flow bonuses, care packages, automatic shield usage and older app-stack proposals were historical brainstorming, not approved current behaviour.
- Shield exchange **600 XP** and wallet limit **two** were selected; weekly quota protection and comeback time/cooldown are still OPEN.
- Unlimited basic habits and recovery are free; four subscription tiers are agreed as a structure only. **All concrete prices and AI allowances remain unapproved.**
- Server-authoritative scoring and transaction log are recommended architectural controls, not implemented yet.

## REFERENCE / NOT BUILT
- Twenty-six screen templates and eight supporting flows exist as static design drafts and review prototype; no native Flutter app verified.
- All status numbers in static screens are illustrative; they are **not real user data**.
- Source-of-truth screen requirements are in the owner-provided UI/UX package and master document; link/transfer reviewed versions before using them to implement UI.

## Nonclinical accountability boundaries
- This is a habit/accountability companion, not therapy, diagnosis or treatment.
- Do not recommend overexertion simply because the founder's motivating story involved a long walk/run.
- Data privacy and user autonomy are core product principles.
