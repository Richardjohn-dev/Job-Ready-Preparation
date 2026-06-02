# Practical Technical Drills v1

Current as of 2026-06-02.

Purpose: build practical coding confidence for .NET/full-stack/SaaS/integration interviews without drifting into heavy FAANG-style algorithm prep.

Use with:
- `target-role-matrix.md`
- `weak-spot-tracker.md`
- `learning-system-plan.md`
- `modern-dotnet-interview-readiness-map.md`
- `practice-log.md`
- `codex-interviewer-workflow.md`

## Positioning

Target role signal:

> Backend-leaning .NET/product engineer with visible Vue/Nuxt full-stack capability, strongest around SaaS, integrations, workflow automation, background jobs, and remote-first product delivery.

Market mapping from `target-role-matrix.md`:

| Market requirement | Role-matrix evidence | Drill coverage |
| --- | --- | --- |
| C#/.NET, ASP.NET Core APIs | Roles 1, 2, 3, 4, 6, 7, 9, 12, 13, 16 | API endpoint, validation, error handling, auth, background jobs |
| REST APIs and third-party integrations | Roles 1, 2, 3, 6, 7, 8, 10, 13, 16 | Provider client, webhook handler, retry/idempotency, sync run |
| SQL, EF Core, Postgres/SQL Server | Roles 1, 2, 3, 6, 7, 9, 12, 15 | EF query, schema design, indexes, transactions |
| TypeScript/frontend capability | Roles 1, 3, 4, 5, 6, 7, 8, 12, 16 | Nuxt/Vue workflow, form validation, loading/error states |
| Testing and maintainability | Roles 2, 4, 6, 9, 15, 16 | Unit test, integration test, regression test notes |
| Background jobs and async workflows | Roles 6, 9, 10, 15; repeated domain pattern | Hosted service/Hangfire-style job, job status, retry handling |
| Reliability, observability, production debugging | Repeated requirement summary | Logs, correlation IDs, runbook, failed-sync debugging |
| Security/auth/account boundaries | Roles 4, 7; repeated nice-to-have | AuthZ guard, tenant/account isolation, secrets handling |

Recommended balance:
- 70% practical .NET/TypeScript/debugging drills.
- 20% talking through solutions and self-review.
- 10% light data-structure pattern practice.

Avoid for the first market test:
- Dynamic programming grind.
- Graph-heavy problem sets.
- 150+ problem LeetCode plans.
- Algorithm practice that does not improve interview explanation or target-role fit.

## How To Run A Drill

Every drill must produce an output. Passive reading does not count.

Minimum output:
- code, pseudocode, SQL, diagram, or written answer
- spoken explanation notes
- score and next action

Recommended session length:
- 25-45 minutes for a narrow drill
- 60-90 minutes for a take-home-style feature slice

Answer shape while coding:

```text
Problem:
Constraint:
Approach:
Tradeoff:
Tests/checks:
Result:
```

Scoring:

| Score | Meaning |
| --- | --- |
| 0 | Could not start or solution is unsafe/incorrect. |
| 1 | Partial solution; unclear reasoning; major correctness or claim gaps. |
| 2 | Working basic solution with notes, but weak tests, structure, or explanation. |
| 3 | Solid solution with clear explanation, reasonable tests, and tradeoffs. |
| 4 | Interview-ready: concise, tested, maintainable, and handles edge cases/failure modes. |

## First Recommended Drills

Do these first because they hit repeated market requirements and current weak spots WS-007, WS-008, and WS-009.

| Order | Drill | Why first | Expected output |
| --- | --- | --- | --- |
| 1 | API endpoint with validation and error handling | Direct .NET/SaaS requirement; fastest confidence baseline | Endpoint sketch/code, validation cases, 2-3 tests |
| 2 | EF Core query and schema/index explanation | SQL/ORM appears repeatedly in target roles | Query, index note, performance risks |
| 3 | Webhook handler with idempotency | Integrations, billing, reliability, SaaS boundary | Handler sketch, idempotency rule, duplicate-event test |
| 4 | Failed external API call debugging | Strong RDrive DataBridge interview fit | Debugging notes using symptom/risk/checks/hypotheses/fix |
| 5 | Nuxt/Vue form workflow with loading/error states | Keeps full-stack signal visible | Component/page sketch, state table, validation/error cases |

## Light DSA Baseline

Goal: avoid freezing on common patterns, not become a FAANG algorithm candidate.

Use C# or TypeScript. Explain Big-O aloud.

| Pattern | Practice task | Target output | Score notes |
| --- | --- | --- | --- |
| Arrays/lists | Remove duplicate file names while preserving order | Function plus edge cases | Score 3 if O(n), clear null/empty behavior |
| Dictionary/map | Count provider error codes by integration | Function plus sample input/output | Score 3 if key selection and missing values are clear |
| Set | Find repeated webhook event IDs | Function plus duplicate handling note | Score 3 if duplicate detection is O(n) |
| Sorting | Sort sync runs by priority, status, then created date | Comparator plus test cases | Score 3 if stable ordering is explained |
| Binary search | Find first failed run in timestamp-sorted status history | Function plus boundary cases | Score 3 if off-by-one cases are handled |
| Two pointers | Merge two sorted event streams by timestamp | Function plus duplicate timestamp rule | Score 3 if ordering tradeoff is stated |
| Sliding window | Find a burst of more than N failures within 10 minutes | Function plus time-window tests | Score 3 if window movement is correct |
| Stack/queue | Validate nested template tokens in folder paths | Function plus invalid examples | Score 3 if malformed input is handled |
| Basic recursion | Walk a folder tree and collect eligible documents | Function plus max-depth or cycle note | Score 3 if termination is explicit |
| Basic tree | Find the nearest parent folder with provider permissions | Function plus missing-permission case | Score 3 if null/empty tree behavior is clear |

## Practical Drills

### Drill 1: API Endpoint With Validation

Market signal:
- ASP.NET Core APIs, validation, error handling.
- Target roles: 1, 2, 3, 6, 7, 12, 13.

Prompt:

```text
Build or sketch an endpoint that creates an integration mapping.
Inputs: accountId, provider, sourceStatus, destinationFolderTemplate, enabled.
Validate required fields, supported provider, folder-template tokens, and account access.
Return clear errors.
```

Expected output:
- Endpoint code or pseudocode.
- Validation rules.
- Error response examples.
- 2-3 unit or integration test cases.

Scoring notes:
- Score 3 when validation, auth boundary, and error shape are clear.
- Score 4 when tests cover invalid provider, missing account access, and malformed folder token.

### Drill 2: EF Core Query And Index Reasoning

Market signal:
- EF Core, SQL, Postgres/SQL Server, query performance.
- Target roles: 1, 2, 3, 6, 7, 9, 12, 15.

Prompt:

```text
Write a query to list the latest 50 sync runs for an account and integration.
Include status, startedAt, completedAt, failureReason, and document count.
Explain what indexes matter and what should not be loaded.
```

Expected output:
- EF-style query or SQL.
- Index recommendation.
- N+1 and pagination risks.
- Test data cases.

Scoring notes:
- Score 3 when filtering, ordering, projection, and pagination are correct.
- Score 4 when the answer explains projection, composite indexes, and avoiding full graph loads.

### Drill 3: Small Schema Design

Market signal:
- Data modeling for SaaS/integrations.
- Target roles: 2, 3, 7, 9, 12, 16.

Prompt:

```text
Design tables for account integrations and sync runs.
Include account boundary, provider type, credential reference, status, timestamps, and retry count.
Do not store raw secrets in the integration row.
```

Expected output:
- Tables/entities.
- Key constraints.
- Index notes.
- Short explanation of credential reference vs secret value.

Scoring notes:
- Score 3 when account isolation and common queries are supported.
- Score 4 when secret storage, auditability, and status transitions are considered.

### Drill 4: Webhook Handler With Idempotency

Market signal:
- Billing/webhooks, SaaS access state, duplicate events.
- Target roles: 3, 4, 6, 7, 8, 13.

Prompt:

```text
Sketch a billing webhook handler.
It receives subscription.updated and subscription.cancelled events.
Events may arrive twice or out of order.
Update account access safely.
```

Expected output:
- Handler flow.
- Signature verification note.
- Idempotency/event table design.
- Duplicate and out-of-order test cases.

Scoring notes:
- Score 3 when duplicates cannot create duplicate side effects.
- Score 4 when ordering, audit logs, signature verification, and access-state recovery are covered.

### Drill 5: External Provider API Client

Market signal:
- REST integrations, retries, provider-specific behavior.
- Target roles: 1, 3, 8, 9, 10, 13, 16.

Prompt:

```text
Design a provider client method that uploads a document package.
It must handle auth token refresh, timeout, retryable failure, permanent failure, and status logging.
```

Expected output:
- Interface or method sketch.
- Retry/permanent-failure classification.
- Logging fields.
- Token/session refresh rule.

Scoring notes:
- Score 3 when transient vs permanent failures are separated.
- Score 4 when correlation IDs, retry budget, and user-visible status are included.

### Drill 6: Background Job Lifecycle

Market signal:
- Background jobs, async workflows, long-running work.
- Target roles: 6, 9, 10, 15; repeated market summary.

Prompt:

```text
Move a long-running sync out of an HTTP request.
Show request -> job creation -> worker execution -> status query -> retry/rerun.
```

Expected output:
- Flow diagram or code sketch.
- Job status states.
- Retry and cancellation notes.
- Test strategy.

Scoring notes:
- Score 3 when request lifecycle and worker lifecycle are separated.
- Score 4 when idempotency, status visibility, and partial failure recovery are covered.

### Drill 7: Integration Test For API + Database Behavior

Market signal:
- Testing, maintainability, code review readiness.
- Target roles: 2, 4, 6, 9, 15, 16.

Prompt:

```text
Write an integration-test plan for creating an integration mapping.
Test database persistence, account isolation, validation errors, and authorization failure.
```

Expected output:
- Test cases.
- Fixture/database setup note.
- Assertions.
- One regression-risk note.

Scoring notes:
- Score 3 when happy path and one failure path are testable.
- Score 4 when account isolation and database cleanup are handled.

### Drill 8: TypeScript/Nuxt Form Workflow

Market signal:
- Vue/Nuxt/TypeScript full-stack capability.
- Target roles: 3, 4, 5, 8; React/Angular roles still value frontend adaptability.

Prompt:

```text
Sketch a Nuxt/Vue page for configuring a provider integration.
Include form fields, validation, submit state, loading state, empty state, error state, and success state.
```

Expected output:
- Component/page pseudocode.
- State table.
- Validation rules.
- API-call error handling.

Scoring notes:
- Score 3 when states are explicit and user feedback is clear.
- Score 4 when auth/account loading and retryable submit errors are handled.

### Drill 9: Debug A Failed Sync

Market signal:
- Production debugging, integrations, reliability.
- Target roles: 1, 4, 6, 9, 15, 16.

Prompt:

```text
A sync created the target folder hierarchy but missed several documents.
Diagnose it.
```

Expected output:
- Symptom, immediate risk, first checks, hypotheses, isolation steps, fix/rollback, regression prevention, communication.

Scoring notes:
- Score 3 when diagnosis is ordered and avoids guessing.
- Score 4 when provider API behavior, permissions, filters, pagination, retry logs, and user communication are included.

### Drill 10: AuthZ Guard And Account Boundary

Market signal:
- Auth/account boundaries, SaaS security.
- Target roles: 4, 7; repeated nice-to-have.

Prompt:

```text
Protect an endpoint so a user can only read sync runs for accounts they belong to.
Explain authentication vs authorization.
```

Expected output:
- Guard/policy sketch.
- Account-membership query.
- Failure behavior.
- Test cases for cross-account access.

Scoring notes:
- Score 3 when account boundary is enforced server-side.
- Score 4 when tests prove another account's data cannot be read even if IDs are guessed.

### Drill 11: Webhook Duplicate Side Effects

Market signal:
- Idempotency, billing, external events.
- Target roles: 3, 4, 6, 7, 8.

Prompt:

```text
A webhook fires twice and credits are added twice.
Fix the design.
```

Expected output:
- Root-cause hypothesis.
- Event idempotency table or ledger model.
- Regression test.
- Communication note.

Scoring notes:
- Score 3 when duplicate side effects are prevented.
- Score 4 when ledger/audit design and replay safety are explained.

### Drill 12: Provider Rate Limit Handling

Market signal:
- External APIs, retries, operational status.
- Target roles: 1, 8, 9, 10, 13, 16.

Prompt:

```text
The provider returns 429 during a large document import.
Design handling for retry, backoff, status, and user expectations.
```

Expected output:
- Retry/backoff strategy.
- Job status updates.
- Max retry or pause rule.
- User/admin message.

Scoring notes:
- Score 3 when retries are bounded and visible.
- Score 4 when rate-limit headers, queue pressure, and partial completion are handled.

### Drill 13: Error Response And Logging Shape

Market signal:
- API quality, support visibility, privacy.
- Target roles: repeated market summary.

Prompt:

```text
Design API error responses and logs for provider upload failure.
Keep users informed without exposing secrets or private provider payloads.
```

Expected output:
- Error response examples.
- Log fields.
- Privacy exclusions.
- Correlation ID approach.

Scoring notes:
- Score 3 when logs are useful and safe.
- Score 4 when support/debugging needs and privacy boundaries are both explicit.

### Drill 14: Take-Home Feature Slice

Market signal:
- Product engineering, end-to-end delivery.
- Target roles: 1, 2, 3, 4, 6, 8, 12, 16.

Prompt:

```text
Build a small "sync runs" page and API.
Backend: list runs filtered by account/integration/status.
Frontend: table with loading, empty, error, retry, and status labels.
Testing: one API test and one frontend state test or manual test checklist.
```

Expected output:
- Small working feature or detailed pseudocode.
- Test/checklist.
- 5-minute explanation.

Scoring notes:
- Score 3 when the feature is coherent and testable.
- Score 4 when failure states, account boundary, and query performance are handled.

### Drill 15: Refactor A Provider-Specific Branch

Market signal:
- Maintainability, architecture judgment, integration platform work.
- Target roles: 2, 4, 8, 9, 16.

Prompt:

```text
Given repeated if/else provider logic for upload behavior, refactor toward a provider capability/handler model.
Explain what should stay generic and what must remain provider-specific.
```

Expected output:
- Before/after sketch.
- Tradeoff note.
- Test strategy.

Scoring notes:
- Score 3 when duplication is reduced without hiding real provider differences.
- Score 4 when the answer avoids over-abstraction and includes provider-specific tests.

### Drill 16: Communicate A Technical Fix

Market signal:
- Remote collaboration, async communication, stakeholder clarity.
- Target roles: repeated market summary.

Prompt:

```text
Write a short async update after fixing a failed integration job.
Audience: engineering manager plus non-technical product stakeholder.
Include impact, cause, fix, risk, and next prevention step.
```

Expected output:
- Developer-facing update.
- Stakeholder-facing update.
- One follow-up action.

Scoring notes:
- Score 3 when it is clear, concise, and evidence-safe.
- Score 4 when it separates technical detail from business impact without overclaiming.

## Practice Log Template

```text
Date:
Drill:
Target role signal:
Minutes:
Output:
Score before:
Score after:
What failed:
What improved:
Next drill:
```

## First Two-Week Drill Plan

Do not wait for issue #12's live diagnostic. These are solo artifact drills.

Week 1:
- Drill 1: API endpoint with validation.
- Drill 2: EF Core query and index reasoning.
- Drill 4: webhook handler with idempotency.
- One light DSA pattern: dictionary/map or set.

Week 2:
- Drill 6: background job lifecycle.
- Drill 8: TypeScript/Nuxt form workflow.
- Drill 9: failed sync debugging.
- Drill 16: communicate a technical fix.

Expected two-week outputs:
- 6-8 completed drill notes or code snippets.
- 1 improved technical explanation.
- 1 weak-spot score update for WS-007 or WS-009.
- Clear list of the next 3 drills.

## Completion Standard

This pack is useful when it produces:
- at least 12 completed practical drills
- 30-50 light DSA pattern reps or reviewed examples
- 2 rough mock technical screens later, after issue #12 establishes the first diagnostic baseline
- practice-log entries with scores and next actions

