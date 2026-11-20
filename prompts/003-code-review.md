# Anti Burnout — Professional Code Review Workflow

Use this prompt to perform an independent, objective technical code review on any proposed pull request, branch diff, or implementation slice before merging into `main`.

**Guiding Principles:**
- Specification-driven development (`AGENTS.md`).
- Google Engineering Practices (`google/eng-practices`: small reviewable changes, clear explanations, objective standards).
- Official Dart & Flutter Effective Design guidelines.
- Anti Burnout Quality & Security criteria (`docs/quality/TEST_SECURITY_RELEASE.md`).

Reviewers must identify **actual findings with concrete file/line evidence**, not invent hypothetical issues or enforce unapproved personal stylistic preferences.

---

## 10-Point Code Review Checklist

### 1. Requirement Traceability
- [ ] Does the change directly reference an approved Decision ID (`PD-XX`) or Requirement ID?
- [ ] Are all implemented behaviors consistent with `docs/product/PRODUCT_BASELINE.md`?
- [ ] Are unapproved features, numerical game rules, or provisional pricing strictly absent?

### 2. Architecture & Separation of Responsibilities
- [ ] Does the change adhere to approved architectural decisions (or proposed boundaries pending ADR sign-off)?
- [ ] Is presentation logic separated from business logic and data persistence?
- [ ] Is server-authoritative scoring respected where required (critical awards, XP, shields verified by backend)?
- [ ] Does the change avoid mandating unapproved architectural patterns before their relevant ADR is accepted?

### 3. TDD Evidence (Where Applicable)
- [ ] For domain and business logic: is there verifiable evidence of a test-first approach?
- [ ] Were tests executed in the real terminal environment (showing Red $\rightarrow$ Green progress)?
- [ ] Are test descriptions clear, descriptive, and mapped to acceptance scenarios?

### 4. Test Suite Quality (Unit, Widget, Integration)
- [ ] **Unit Tests:** Are edge cases covered (null, 0, boundary values, negative numbers, overflow)?
- [ ] **Widget Tests:** Are loading, error, empty, and populated states tested with `WidgetTester`?
- [ ] **Integration Tests:** Are user flows (back/cancel navigation, confirmations) validated?
- [ ] Do tests use project-standard, approved assertion methods without flaky timeouts or unapproved dependencies?

### 5. Static Analysis, Linting & Formatting
- [ ] Does `dart analyze` pass with **0 errors and 0 warnings**?
- [ ] Is the code formatted according to standard `dart format`?
- [ ] Are there any unused imports, dead code paths, or deprecated API invocations?

### 6. Security, Privacy & Credential Policy
- [ ] **No Server Secrets in Client:** Are server-side secret API keys, Supabase secret/service-role keys, administrative credentials, passwords, private signing keys, or confidential tokens strictly absent from the Flutter client and public GitHub repository?
- [ ] **Public Client Identifiers vs Secrets:** If public client identifiers (such as Supabase publishable / anon keys) are included in client configuration, is it understood that public keys are client identifiers only, and NEVER a substitute for authentication, authorization, Row Level Security (RLS), or server-side validation?
- [ ] **Server-Side Trust Boundaries:** Are sensitive operations, AI provider credentials (e.g. Gemini API), administrative database access, and authoritative XP/streak awards protected behind approved server-side boundaries rather than executed client-side?
- [ ] **Release Build Security:** Do native Android and iOS build configurations enforce relevant release-mode protections (e.g. debug flags disabled, secure network configuration, ProGuard/R8)?
- [ ] **Data Protection & Privacy:** Does `.gitignore` protect local configuration/secrets, and are sensitive user habit, reflection, and behavioral data protected in accordance with project privacy policy (no plain-text confidential storage, no raw logging of personal chats)?

### 7. Accessibility & UI Fidelity
- [ ] Are touch targets at least 48x48dp (Android) / 44x44pt (iOS)?
- [ ] Do interactive widgets provide `Semantics` labels for screen readers?
- [ ] Does the UI render cleanly in both Dark and Light themes with WCAG 2.2 AA contrast?
- [ ] Is dynamic text scaling and reduced motion supported without RenderFlex overflow?

### 8. Error Handling & Edge Cases
- [ ] Are network requests, parsing, and asynchronous operations guarded by explicit `try/catch` or result types?
- [ ] Are user-facing error messages beginner-friendly, actionable, and non-technical?
- [ ] Is offline state handled gracefully (cached display, queued actions, clear pending status)?

### 9. Maintainability & Simplicity
- [ ] Is the change as small and focused as possible (following Google CL size guidance)?
- [ ] Are public methods, classes, and libraries documented with Effective Dart `///` doc comments?
- [ ] Is premature optimization or speculative generalization avoided?

### 10. Regression Risk & Defensible Explanation
- [ ] Could this change break existing habits, streaks, or stored data?
- [ ] Can the author explain *why* this implementation was chosen over alternatives?
- [ ] Is the commit message structured clearly (e.g. `feat(habits): implement daily quota evaluation`)?

---

## Review Output Format

Reviewers must output findings using this structure:

```markdown
### Code Review Summary: [Branch / PR Title]

**Recommendation:** [APPROVE / CHANGES REQUESTED / BLOCKED]

#### 1. Summary of Changes
[Brief 2-3 sentence overview of what was added or modified]

#### 2. Key Strengths
- [Specific positive finding with file reference]

#### 3. Issues & Action Items
- **[CRITICAL / MAJOR / MINOR]** `path/to/file.dart#L12-L18`: [Issue description, evidence, and recommended resolution]

#### 4. Verification Evidence
- `dart analyze` output: [Clean / Warnings]
- Test execution output: [Pass / Fail count]
- Traceability: [Mapped to PD-XX / REQ-XX]
```
