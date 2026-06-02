# Reliability And Security Interview Pack v1

Current as of 2026-06-02.

Purpose: prepare for practical reliability, debugging, integration, billing/webhook, auth/account, secrets/BYOK, logging, and privacy questions in .NET/full-stack/SaaS/integration interviews.

Use with:
- `rdrive-databridge-case-study.md`
- `refinebridge-case-study.md`
- `codex-interviewer-workflow.md`
- `weak-spot-tracker.md`
- `target-role-matrix.md`
- `practice-log.md`

## Operating Rules

- Do not run a live diagnostic interview here; issue #12 handles the first diagnostic.
- Do not invent real incidents, metrics, customers, production status, or RefineBridge implementation facts.
- Use RDrive DataBridge as the strongest evidence-backed reliability story.
- Use RefineBridge as a cautious modern SaaS/security practice case until repo verification.
- Produce outputs: runbooks, answer drafts, threat models, scoring notes, and follow-up questions.

## Market Mapping

| Topic | Target-role signal | Practice source |
| --- | --- | --- |
| Production debugging and reliability | Repeated market requirement; roles 1, 4, 6, 9, 15, 16 | RDrive DataBridge strongest |
| External API failure handling | Roles 1, 3, 8, 9, 10, 13, 16 | RDrive DataBridge; RefineBridge cautious |
| Background jobs, retries, idempotency | Roles 6, 9, 10, 15 | Both |
| Webhook/billing state | SaaS/product roles; roles 3, 4, 6, 7 | RefineBridge cautious |
| Auth/account boundaries | Roles 4, 7; repeated nice-to-have | RefineBridge cautious |
| Secrets/BYOK/API keys | SaaS/security repeated requirement | RefineBridge cautious; RDrive provider credentials |
| Logging/privacy/support visibility | Repeated market requirement | Both |

## First Recommended Practice

| Order | Scenario | Why first | Expected output |
| --- | --- | --- | --- |
| 1 | RDrive sync missed documents | Strong evidence-backed debugging story | Runbook using debugging format |
| 2 | Provider token expires during job | External API/session handling | Recovery flow and communication note |
| 3 | Duplicate webhook changes billing/access twice | SaaS reliability and idempotency | Event table/state-machine sketch |
| 4 | Cross-account sync-run access attempt | SaaS auth/account boundary | AuthZ test cases |
| 5 | Provider key/BYOK storage threat model | Security interview basics | Threat model and safe wording |

## Debugging Answer Format

Use this for every incident-style prompt:

```text
Symptom:
Immediate risk:
First checks:
Hypotheses:
Isolation steps:
Fix/rollback:
Regression prevention:
Communication:
```

Scoring:

| Score | Meaning |
| --- | --- |
| 0 | No structured diagnosis or unsafe claim. |
| 1 | Jumps to a fix without evidence; misses user/security risk. |
| 2 | Basic diagnosis with notes; weak isolation, prevention, or communication. |
| 3 | Clear, ordered, practical debugging answer with prevention and communication. |
| 4 | Interview-ready: risk-aware, evidence-backed, privacy-safe, tested, and operationally mature. |

## Scenario 1: Sync Created Folders But Missed Documents

Project:
- RDrive DataBridge.

Prompt:

```text
An RDrive DataBridge synchronization created the target folder hierarchy but missed several provider documents. How would you investigate?
```

Expected answer:

```text
Symptom:
The folder structure exists in RDrive, but expected documents are missing after a sync run.

Immediate risk:
Users may trust an incomplete document library, so I would treat it as data completeness risk rather than only a job failure.

First checks:
Check sync run status, logs, provider query filters, pagination, folder permissions, document metadata, retry history, and whether the missing documents match configured filters.

Hypotheses:
Provider search did not return all documents; metadata filters excluded them; pagination failed; permissions blocked download; download succeeded but upload failed; duplicate/idempotency logic skipped them incorrectly.

Isolation steps:
Compare provider-side document list with DataBridge result records, replay a small sanitized subset, inspect one missing document's metadata and permissions, and check correlation IDs across provider download and RDrive upload steps.

Fix/rollback:
Fix the failing query/filter/pagination/permission path, rerun only the affected sync scope, and avoid duplicating already imported documents.

Regression prevention:
Add test coverage or a checklist for pagination/filter/permission cases, improve logs around skipped documents, and expose clearer skipped/failed counts.

Communication:
Tell stakeholders what scope was affected, whether data was incomplete or only delayed, what was rerun, and what will prevent recurrence.
```

Scoring notes:
- Score 3 if the answer is ordered and covers provider query, filters, permissions, and retries.
- Score 4 if it includes completeness risk, correlation IDs, skipped-count visibility, and safe rerun/idempotency.

## Scenario 2: Provider Token Expires During Background Job

Project:
- RDrive DataBridge or RefineBridge cautious.

Prompt:

```text
A provider session expires halfway through a background job. What should happen?
```

Expected output:
- Token/session refresh rule.
- Retry behavior.
- Job status behavior.
- User/admin visibility.
- Secret/privacy boundary.

Answer outline:
- Detect auth/session failure separately from normal provider failure.
- Attempt refresh if allowed and safe.
- Resume from last known idempotent step.
- Mark job as retrying or waiting, not silently failed.
- Stop after bounded retries and surface admin action if credentials need reauthorization.
- Never log tokens or raw credentials.

Scoring notes:
- Score 3 when refresh, retry, status, and user visibility are covered.
- Score 4 when idempotent resume and credential privacy are explicit.

## Scenario 3: Provider Returns 429 During Import

Project:
- RDrive DataBridge or RefineBridge cautious.

Prompt:

```text
A provider returns rate-limit responses during a large import. How do you handle it?
```

Expected output:
- Retry/backoff policy.
- Rate-limit header handling.
- Queue pressure consideration.
- Partial-completion behavior.
- User/admin message.

Scoring notes:
- Score 3 when retries are bounded and visible.
- Score 4 when it avoids hammering the provider and explains partial progress safely.

## Scenario 4: Webhook Fires Twice And Grants Access Twice

Project:
- RefineBridge cautious; do not claim implementation until verified.

Prompt:

```text
A billing webhook is delivered twice. The first handling grants access; the second creates duplicate credits or access state. How do you design against this?
```

Expected output:
- Webhook signature verification note.
- Processed-event table or idempotency key.
- Access-state transition model.
- Credit ledger if credits exist.
- Duplicate-event regression test.

Answer outline:
- Verify webhook signature before any state change.
- Store provider event ID and processing result.
- Make the handler idempotent: same event ID cannot apply side effects twice.
- Prefer ledger-style credit changes if credits exist.
- Audit state transitions.
- Handle delayed/out-of-order events by comparing provider timestamp/version or fetching current subscription state.

Scoring notes:
- Score 3 when duplicate side effects are prevented.
- Score 4 when signature verification, event storage, ordering, auditability, and recovery are covered.

## Scenario 5: Billing Webhook Delayed Or Out Of Order

Project:
- RefineBridge cautious.

Prompt:

```text
An account cancels, then upgrades, but webhooks arrive late or out of order. How should access be decided?
```

Expected output:
- Source-of-truth decision.
- Event ordering strategy.
- Reconciliation job or provider fetch.
- Support/admin visibility.
- User impact note.

Scoring notes:
- Score 3 when it does not trust event arrival order blindly.
- Score 4 when it includes reconciliation and a safe access fallback.

## Scenario 6: Cross-Account Data Access

Project:
- RefineBridge cautious.

Prompt:

```text
A user changes an accountId in a URL/API request and can see another account's sync run. How would you prevent and test against this?
```

Expected output:
- Authentication vs authorization explanation.
- Server-side membership/role check.
- Query scoped by account and user membership.
- Negative tests.
- Logging of suspicious access without leaking data.

Answer outline:
- Authentication proves who the user is.
- Authorization decides whether that user can access the requested account/resource.
- Never trust frontend route guards alone.
- Every account-scoped query must include account boundary enforcement.
- Add tests where a valid user attempts to access another account's resources.

Scoring notes:
- Score 3 when the server-side boundary and tests are clear.
- Score 4 when it includes least privilege, admin exceptions, and privacy-safe security logs.

## Scenario 7: Secrets, Provider Keys, And BYOK

Project:
- RefineBridge cautious; RDrive provider credentials as general integration context.

Prompt:

```text
How would you store external provider credentials or user-supplied provider keys? What are the risks if a BYOK model exists?
```

Safe wording:

```text
For RefineBridge, BYOK/provider-cost controls are a verification gap until the repo confirms implementation. As a design topic, I would treat provider keys as high-risk secrets: encrypted at rest or delegated to a secret manager, never logged, scoped to account access, rotated/revoked when needed, and only exposed through controlled use paths.
```

Expected output:
- Secret storage rule.
- Access control rule.
- Rotation/revocation plan.
- Logging exclusions.
- Abuse/cost-risk notes.

BYOK threat model:

| Risk | Control |
| --- | --- |
| Key leaked through logs | Redact secrets, structured logging exclusions, tests/checklist |
| User accesses another account's key | Server-side account authorization and scoped secret lookup |
| Provider cost abuse | quotas, rate limits, usage visibility, manual suspension |
| Key cannot be rotated | credential versioning and revoke/replace flow |
| Admin overreach | audit logs and least-privilege admin actions |
| Frontend exposure | never send raw secret back after creation; masked display only |

Scoring notes:
- Score 3 when storage, access, and logging are safe.
- Score 4 when rotation, audit, cost abuse, and account isolation are included.

## Scenario 8: Logging And Privacy

Project:
- Both.

Prompt:

```text
What would you log for a failed integration job, and what should never be logged?
```

Log:
- correlation ID
- account/integration ID or sanitized reference
- provider name/type
- job/run ID
- status transition
- retry count
- error category
- timing/duration
- skipped/failed counts
- sanitized provider response summary

Do not log:
- raw credentials, tokens, API keys
- customer document contents
- unredacted customer metadata
- private project names or identifiers in public artifacts
- full provider payloads with PII/secrets
- billing payment details

Expected output:
- Logging field list.
- Privacy exclusion list.
- Support/debugging explanation.

Scoring notes:
- Score 3 when logs are useful and privacy-safe.
- Score 4 when it balances support visibility, audit needs, and minimization.

## Scenario 9: Admin Manual Rerun Or Recovery

Project:
- RDrive DataBridge strongest; RefineBridge cautious.

Prompt:

```text
An admin needs to rerun a failed sync. What controls and safeguards should exist?
```

Expected output:
- Permission boundary.
- Idempotency/duplicate prevention.
- Scope selection.
- Audit log.
- User communication.

Scoring notes:
- Score 3 when rerun does not duplicate successful work.
- Score 4 when auditability and least privilege are included.

## Scenario 10: Provider Behavior Changes Late

Project:
- RDrive DataBridge.

Prompt:

```text
A provider changes download behavior late in implementation, similar to Autodesk-style chunked downloads or folder permission checks. How do you handle it technically and with stakeholders?
```

Expected output:
- Discovery gap statement.
- Revised implementation plan.
- Scope/timeline tradeoff.
- Testing plan.
- Stakeholder update.

Answer outline:
- Confirm the behavior with real provider/account testing.
- Separate reusable pipeline work from provider-specific risk.
- Update estimate with concrete unknowns.
- Offer scope cuts where possible.
- Add provider-specific test/checklist coverage.

Scoring notes:
- Score 3 when technical and stakeholder handling are both present.
- Score 4 when it uses calm, evidence-safe communication and offers options.

## Runbook Templates

### Sync Failure Runbook

```text
Trigger:
Affected scope:
Immediate risk:
User-visible status:
First checks:
- Job/run status:
- Provider status:
- Credential/session status:
- Query/filter/mapping:
- Pagination:
- Permissions:
- Download/upload result:
- Retry history:

Isolation:
Recovery:
Regression prevention:
Stakeholder update:
Open questions:
```

### Billing/Webhook Runbook

```text
Trigger:
Affected account:
Immediate risk: unpaid access / paid user blocked / duplicate credits / stale subscription state
First checks:
- Signature verification:
- Event ID:
- Event type:
- Existing processed-event record:
- Current provider subscription state:
- Local access state:
- Credit ledger/usage state:

Isolation:
Recovery:
Reconciliation:
Regression prevention:
Customer/support update:
Open questions:
```

### Auth/Account Boundary Runbook

```text
Trigger:
Affected resource:
Immediate risk:
First checks:
- Authenticated user:
- Account membership:
- Role/permission:
- Query scope:
- Frontend route:
- Backend policy:
- Logs/audit:

Isolation:
Fix:
Regression tests:
Security/privacy communication:
Open questions:
```

## Security Prompt Bank

Auth/account:
- Explain authentication vs authorization.
- Where are account boundaries enforced?
- What tests prove account isolation?
- What admin actions should require elevated permissions?
- How do you avoid relying only on frontend route guards?

Webhook/billing:
- How do you verify webhook trust?
- How do you handle duplicate events?
- How do you handle delayed events?
- How do you reconcile local state with provider state?
- What access fallback is safest when billing state is uncertain?

External APIs:
- How do you classify retryable vs permanent provider failures?
- How do you handle provider downtime?
- How do you handle token/session expiry?
- How do you avoid duplicate uploads?
- What should users see during a long-running job?

Secrets/BYOK:
- Where are provider keys stored?
- Who can use or rotate them?
- What should never be logged?
- How do you prevent provider-cost abuse?
- How would you revoke compromised credentials?

Logging/privacy:
- What logs help support?
- What logs increase privacy risk?
- How do you use correlation IDs?
- What belongs in metrics vs logs?
- How do you write public case studies without leaking private customer data?

## Interview Answer Drafts

### Reliability One-Liner

```text
For integration systems, I treat reliability as part of the product, not an afterthought. External APIs fail, sessions expire, jobs partially complete, and users need visible state, so the system needs retries, idempotency, health/status checks, logs, and safe rerun paths.
```

### Security One-Liner

```text
For SaaS workflows, the main security boundary is usually account-level access: authentication tells me who the user is, but every backend query and action still has to prove that user can access that account, integration, credential reference, or job.
```

### Privacy One-Liner

```text
I want logs to explain what happened without becoming a data leak, so I would log IDs, status transitions, categories, counts, timing, and correlation IDs, but not raw tokens, credentials, customer document contents, or sensitive provider payloads.
```

## First Two-Week Plan

Week 1:
- Write a Sync Failure Runbook from Scenario 1.
- Write a provider token-expiry answer from Scenario 2.
- Write logging/privacy field list from Scenario 8.

Week 2:
- Write a webhook idempotency answer from Scenario 4.
- Write auth/account boundary test cases from Scenario 6.
- Write BYOK/provider-key threat model from Scenario 7.

Expected outputs:
- 3 runbook/answer drafts.
- 1 webhook state/idempotency sketch.
- 1 auth/account test checklist.
- 1 secrets/BYOK threat model.
- WS-009 and WS-014 score update if practice produces clearer answers.

## Completion Standard

This pack is useful when it produces:
- 3 debugging/runbook answers.
- 2 webhook/billing state answers.
- 2 external API failure answers.
- 2 auth/account/security answers.
- 1 secrets/BYOK threat model.
- 1 logging/privacy checklist.
- practice-log entries with scores and next actions.

