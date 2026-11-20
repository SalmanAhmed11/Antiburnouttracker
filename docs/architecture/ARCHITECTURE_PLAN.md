# Architecture, Database and API Design Backlog

**Status: proposed architecture only. No production choices approved by this document.** Do not start source code, schema or cloud provisioning merely because this plan exists.

## Architecture decision records to produce before code

| ADR | Question | Alternatives / necessary evidence |
| --- | --- | --- |
| ADR-001 | Flutter UI architecture and state | Flutter guidance, layer boundaries; Riverpod/BLoC/other; testability vs complexity |
| ADR-002 | Routing and deep links | `go_router` vs standard navigation, onboarding guards and resume flows |
| ADR-003 | Backend boundary | Supabase native + Edge Functions vs separate API server; latency, costs, service limits |
| ADR-004 | Data ownership and scoring | Server-authoritative XP/streak ledger, atomic transaction & idempotency |
| ADR-005 | Data model and migrations | Users/habits/recurrence/targets/negotiations/check-ins/XP/recovery/chat/purchases; migration strategy |
| ADR-006 | Authn/authz | Apple/Google/email, account link/recovery, RLS by subject, server token verification |
| ADR-007 | Offline and reconciliation | Read-only cache/drafts versus queued commands; timezone, conflict, replay and pending UI |
| ADR-008 | AI Coach architecture | LLM API security, limited context, tool permissions, safety, evaluation and memory retention |
| ADR-009 | Billing and entitlements | iOS/Android store handling, receipts, grace, refund, restoration and offline feature enforcement |
| ADR-010 | Observability and operations | Sanitised logs, error reporting, alerting, backups, restores, SLO/RTO/RPO targets |
| ADR-011 | App release | Android signing, iOS macOS build, beta channels, CI/CD gates and rollback |
| ADR-012 | Notification and time policy | Quiet hours, delivery reliability, consent, DST/travel, reminder and due-time semantics |

## Provisional logical boundaries (illustrative)
- Flutter UI components: presentation only; show pending vs confirmed outcomes truthfully.
- Domain/application services: coordinate approved business rules; **critical awards are verified by a trusted server**.
- Authenticated storage: PostgreSQL/other selected persistent backend, row-level ownership and audited changes.
- Backend commands: validate requests, prevent replay/double XP, record ledger and check-in atomically; authorize every object access.
- AI orchestration: minimum necessary user context, no secrets in mobile client, restricted operations and explicit user approvals.
- Client offline draft/cache: behaviour depends on PD-13; no fabricated confirmed progress.

## Required design outputs
- Context, data-flow, sequence and trust-boundary diagrams.
- Entity relationship diagram, keys, indexes, access-control matrix and RLS denial tests.
- API contract with method/path, request/response schemas, validation, errors, auth, idempotency and rate limits.
- XP/streak event lifecycle, duplicate/offline submission handling and complete invariants.
- Backup/restore, migration strategy, data retention/deletion and threat model.
- Numeric, testable non-functional goals with explicit assumptions (not guessed benchmarks).

## ADR template
**Title / ID:**  
**Status:** Proposed / Accepted / Superseded  
**Context and requirement IDs:**  
**Options evaluated:**  
**Decision:**  
**Why / tradeoffs / risk:**  
**Security and privacy implications:**  
**Implementation boundary:**  
**How tested:**  
**Approval date:**  
**Revisit conditions:**  
