# Quality, Security, Privacy and Release Checklist

**No test has passed and no code has been built merely because this checklist exists.** Use it as the basis for future CI and manual gates. Test against official Flutter guidance, OWASP MASVS/MASTG, OWASP ASVS/API Security, NIST SSDF and LLM-specific guidance.

## Test levels
- [ ] Requirement → unit test traceability for all state calculations (Green/Yellow/minimum, XP, quota, shield, comeback, pause).
- [ ] Flutter widget tests for main interactions, inputs and accessibility semantics.
- [ ] Integration tests for sign-in, creating a habit, completing, renegotiating, recovery and billing.
- [ ] Backend authorization and schema migration tests; two users cannot read/alter each other's records.
- [ ] Idempotency/retries, simultaneous requests, cross-device ordering, offline queued/draft reconciliation.
- [ ] Date/time boundary tests: DST changes, travel, local weeks, pausing during boundary, week-start changes.
- [ ] AI Coach evaluation: modes, hallucinated progress, inappropriate advice, tool calls, consent, prompt injection and quota/cost controls.
- [ ] Visual regression review dark/light, small screens, orientation policy, large type, reduced motion and no text baked into images.

## Security and privacy
- [ ] Threat model trust boundaries, mobile device, backend commands, database and AI provider.
- [ ] Secrets never stored in public repo, mobile binary or screenshots; `.env` examples contain placeholders only.
- [ ] Authn/authz: provider/callback validity, recovery, account linking, RLS and object-level authorization verified.
- [ ] Validate data limits/schema server-side; prevent replay, duplication, price/entitlement spoofing and XP manipulation.
- [ ] Rate limits and API abuse/cost protections; safe logging (no raw coach chat or sensitive details by default).
- [ ] Privacy requirements: legal basis and notices, account deletion, export, consent/data minimisation, retention and provider agreements.
- [ ] Dependency license/provenance/vulnerability and supply-chain scan; lock supported versions.
- [ ] Verify restore from backup and secure deletion procedure.

## Non-functional performance measurements (targets need approval)
- [ ] App startup on representative low/mid Android and iOS devices.
- [ ] P95 API latency, offline UX and sync retry limits.
- [ ] App size, battery impact, crash-free session rate.
- [ ] Backend availability, error budget and ongoing API/AI operational costs.
- [ ] Accessibility testing with real devices/assistive technologies.

## CI and release gates (future implementation)
- [ ] Small PR with requirement IDs, acceptance tests and ADRs where warranted.
- [ ] Dart formatting, static analysis, dependency audit and relevant automated tests all run and show evidence.
- [ ] Secret checks; vulnerability findings triaged with owner approval.
- [ ] Release signing, Android/iOS platform requirements, versioned migrations and rollback/runbook.
- [ ] App Store/Play subscription policy, privacy disclosures, financial/medical marketing claims and beta consent verified.
- [ ] Incident escalation, restore practice, rollbacks, user support and post-release review ownership defined.

## Definition of Done for a future feature
Accepted requirement + linked design + tests (passing real execution) + negative paths + reviewable diff + security/privacy checks proportional to risk + implementation explanation the owner can defend + PR approval. No self-attested green badges.
