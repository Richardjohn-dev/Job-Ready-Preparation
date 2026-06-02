# System Design Practice Pack v1

Current as of 2026-06-02.

Purpose: practice system-design and architecture conversations using RDrive DataBridge and RefineBridge as the source material, aligned to practical .NET/full-stack/SaaS/integration roles.

Use with:
- `rdrive-databridge-case-study.md`
- `refinebridge-case-study.md`
- `target-role-matrix.md`
- `codex-interviewer-workflow.md`
- `behavioral-story-bank.md`
- `weak-spot-tracker.md`

## Operating Rules

- Do not run a live diagnostic interview here; GitHub issue #12 handles the first diagnostic.
- Practice can be solo: outlines, diagrams, written answers, recordings, and self-scoring.
- Keep RefineBridge implementation claims cautious until verified from repo or Richard.
- Use `Problem -> Constraint -> Decision -> Tradeoff -> Result`.
- Treat architecture as evidence of judgment, not buzzword collection.
- Prioritize practical .NET/SaaS/integrations roles over big-tech distributed-systems theater.

## Market Mapping

| System-design topic | Target-role evidence | Project source |
| --- | --- | --- |
| APIs, .NET backend, SQL/ORM | Roles 1, 2, 3, 6, 7, 9, 12, 13, 16 | Both |
| External APIs and integration failure | Roles 1, 3, 8, 9, 10, 13, 16 | RDrive DataBridge strongest; RefineBridge cautious |
| Background jobs, retries, status | Roles 6, 9, 10, 15; repeated market pattern | Both |
| SaaS account/auth boundaries | Roles 4, 7; repeated nice-to-have | RefineBridge cautious |
| Billing/webhooks/access state | SaaS/product role pattern | RefineBridge cautious |
| Admin/support visibility | Workflow/product/internal tools roles | Both |
| Remote ownership and communication | Repeated market summary | Both, especially RDrive DataBridge |

## First Recommended Practice

| Order | Session | Why first | Expected output |
| --- | --- | --- | --- |
| 1 | RDrive DataBridge 10-minute architecture walkthrough | Strongest evidence-backed commercial system | One diagram, 10-minute outline, score |
| 2 | Failed sync design/deep dive | Directly maps to integrations/reliability target roles | Failure-mode table and recovery flow |
| 3 | RefineBridge cautious SaaS architecture walkthrough | Current-stack proof point; needs bounded claims | Verified/unknown/planned claim table plus diagram |
| 4 | ADR sprint: background jobs, idempotency, account boundaries | Builds senior tradeoff language | 3 short ADRs |
| 5 | 30-minute mock structure dry run, written only | Prepares for #12 without running live practice | Session agenda and likely follow-ups |

## Scoring Rubric

| Score | Meaning |
| --- | --- |
| 0 | Cannot explain the system or makes unsafe/unsupported claims. |
| 1 | Names components but weak flow, weak tradeoffs, or unclear evidence. |
| 2 | Basic flow is correct with notes, but failure modes/results are thin. |
| 3 | Clear system explanation with constraints, tradeoffs, and bounded claims. |
| 4 | Interview-ready: concise, evidence-backed, failure-aware, business-aware, and adaptable to follow-ups. |

Score dimensions:
- clarity
- technical accuracy
- evidence support
- requirements framing
- data model/API boundaries
- background work and failure handling
- security/account boundaries
- tradeoff awareness
- business impact
- claim/privacy safety

## Walkthrough Template

```text
System:
Target role family:
Problem:
Users/stakeholders:
Core workflows:
Constraints:
Main components:
Data model:
API boundaries:
Background jobs:
Failure modes:
Security/account/privacy boundaries:
Observability/support:
Tradeoffs:
What I would improve now:
Evidence-safe result:
Open verification gaps:
Score:
Next improvement:
```

## RDrive DataBridge Walkthrough

Use confidently:
- Long-term independent developer/contractor-style work for Snagr/RDrive.
- Major ownership of RDrive DataBridge.
- Implemented/evidence-backed providers: Aconex, Azure Blob Storage, Autodesk, Asite.
- Two primary workflow areas: Form Events and Synchronization.
- Configuration, admin UI, background processing, health/status visibility, retries, token/session handling, provider-specific behavior handling.

Do not claim:
- SharePoint implementation.
- 4Projects implementation.
- sales, adoption, revenue, user counts, or formal employee status.
- private client/project identifiers, live URLs, credentials, screenshots, or tenant data.

### 30-Second Architecture Version

```text
RDrive DataBridge was a configurable integration platform for moving RDrive form packages and provider document libraries between RDrive and external platforms such as Aconex, Azure Blob Storage, Autodesk, and Asite. The architecture evolved from a provider-specific uploader into shared integration concepts: mappings, credentials, metadata-driven folder rules, provider handlers, background jobs, health/status visibility, retries, and token/session handling.
```

### Core Flow: Form Events

```text
RDrive form/status event
  -> DataBridge endpoint
  -> project integration lookup
  -> form/status mapping lookup
  -> RDrive package download
  -> file and metadata extraction
  -> provider destination resolution
  -> provider-specific upload
  -> logs, status, retries, health visibility
```

Practice prompts:
- Explain why Form Events were not just a simple webhook receiver.
- What data must be stored to make this configurable?
- Where does provider-specific behavior belong?
- What happens when the provider token expires during upload?
- What would you log for support?

Expected output:
- One flow diagram.
- 5-minute explanation.
- One failure-mode table.

Scoring notes:
- Score 3 if the configurable mapping and provider-specific behavior are clear.
- Score 4 if token/session failure, retries, and user-visible status are explained.

### Core Flow: Synchronization

```text
Provider document library
  -> provider search/read metadata
  -> synchronization mapping/filter lookup
  -> dynamic RDrive folder path generation
  -> create missing RDrive folder hierarchy
  -> download provider documents
  -> upload into RDrive
  -> sync logs, results, status updates
```

Practice prompts:
- Explain why metadata-driven folder generation mattered.
- How would you prevent duplicate document imports?
- How would you handle a partial sync failure?
- What should be visible to an admin user?
- How would you estimate a new provider sync?

Expected output:
- Folder-path example using sanitized placeholder metadata.
- Data model sketch.
- Partial-failure recovery plan.

Scoring notes:
- Score 3 if the push/pull distinction is clear.
- Score 4 if idempotency, pagination, permissions, and partial failure recovery are included.

### Architecture Evolution Prompt

Prompt:

```text
DataBridge began closer to an Aconex-focused uploader. Explain how you would evolve it into a reusable provider pipeline as Azure Blob Storage, Autodesk, and Asite were added.
```

Expected answer outline:
- Problem: one-provider assumptions were becoming hard to extend.
- Constraint: existing workflows had to keep working while provider behavior differed.
- Decision: introduce reusable integration concepts and provider-specific handlers/capabilities.
- Tradeoff: generic pipeline reduced duplication but did not remove provider discovery/testing.
- Result: supported configurable Form Events and Synchronization across multiple implemented providers with operational visibility.

Follow-ups:
- Which abstraction would you avoid over-generalizing?
- How would tests prove provider-specific behavior still works?
- What would you document before estimating a new provider?

## RefineBridge Walkthrough

Claim boundary:
- Safe: modern .NET, Nuxt/Vue 3, PostgreSQL product/SaaS proof point.
- Safe: product themes include workflow automation, SaaS-style delivery, APIs, admin workflows, auth/account boundaries, billing/webhook-aware flows, background jobs, integrations, and operational clarity.
- Cautious: WorkOS, Lemon Squeezy, Outscraper, GoHighLevel, Hangfire, SignalR, credits, BYOK, provider-cost controls, production status, customer usage, revenue, or launch state.

Use this wording until repo verification:

```text
RefineBridge is my modern .NET/Nuxt/PostgreSQL product project. I use it to demonstrate current SaaS engineering concerns: backend APIs, frontend workflows, account boundaries, billing/webhook-aware flows, background jobs, integrations, admin operations, and operational clarity. Specific providers and implementation status need repo verification before I claim them as shipped.
```

### Cautious System Shape

```text
Nuxt/Vue 3 frontend
  -> ASP.NET/.NET API
  -> PostgreSQL
  -> background jobs for long-running workflows
  -> external providers / CRM-style destinations
  -> billing and webhook provider
  -> auth/account provider or internal auth
  -> admin/status views
```

Practice prompts:
- What is safe to say about RefineBridge today?
- What must be verified before it becomes an interview claim?
- How do account boundaries shape the API and database?
- Why should long-running provider/CRM work be outside request/response?
- What billing/webhook state needs to be auditable?

Expected output:
- One architecture diagram.
- A `verified / planned / unknown` table.
- One 5-minute explanation that does not overclaim.

Scoring notes:
- Score 3 if the architecture is coherent and uncertainty is labelled.
- Score 4 if it cleanly separates implemented facts from design intent and still sounds valuable.

### RefineBridge Claim-Safety Table

| Topic | Safe current wording | Needs verification before claiming |
| --- | --- | --- |
| Stack | .NET backend, Nuxt/Vue 3 frontend, PostgreSQL direction | exact framework versions, architecture pattern, deployment |
| Auth/account | product needs account/workspace boundaries | WorkOS, SSO/SAML, exact role model |
| Billing/webhooks | billing/webhook-aware flows are a practice topic | Lemon Squeezy implementation, live billing, state machine |
| Background jobs | long-running provider/CRM workflows should use jobs | Hangfire/SignalR implementation and retry model |
| Integrations | integration-aware product direction | GoHighLevel, Outscraper, BYOK, provider-cost controls |
| Product status | modern SaaS/workflow product project | customers, revenue, production stability, launch/adoption |

## System-Design Prompt Bank

### Requirements And Constraints

- Design a configurable integration platform for document workflows.
- Design a SaaS workflow product where account access, billing state, and background jobs interact.
- What requirements would you clarify before building the first version?
- Which constraints are technical, and which are business or operational?
- What would you deliberately leave out of v1?

Expected output:
- Functional requirements.
- Non-functional requirements.
- Explicit non-goals.
- Risks/unknowns.

### API And Data Boundaries

- Design endpoints for creating integration mappings and listing sync runs.
- Design data ownership boundaries between account, integration, sync run, document, and credential reference.
- Where should validation live?
- Which operations need transactions?
- What should be projected rather than fully loaded?

Expected output:
- Endpoint list.
- Entity/table sketch.
- Transaction notes.
- Query/index notes.

### Background Jobs And Idempotency

- Design a sync job lifecycle from user request to completion.
- How do you prevent duplicate uploads or duplicate webhook side effects?
- How do you resume after a partial failure?
- What status should a user see while work is running?
- How do you handle retryable vs permanent failures?

Expected output:
- Job states.
- Idempotency key strategy.
- Retry/backoff rule.
- Recovery plan.

### Auth, Account, And Billing State

- Where are account boundaries enforced?
- How do you prevent cross-account access when IDs are guessed?
- How should billing state affect access?
- What happens when a billing webhook is delayed or duplicated?
- What admin actions need audit logs?

Expected output:
- Authorization rules.
- Billing/access state diagram.
- Audit/logging notes.
- Test cases.

### Observability And Support

- What logs, metrics, and traces matter for an integration product?
- How would support know whether a sync is stuck, failed, or waiting on a provider?
- What should never be logged?
- How do correlation IDs help?
- What would you expose in an admin view?

Expected output:
- Logging field list.
- Metrics list.
- Privacy exclusions.
- Admin status table.

## ADR Practice

Write short ADRs. Do not turn them into essays.

Template:

```text
# ADR: [Decision]

Status: Draft

Context:

Decision:

Alternatives considered:

Tradeoffs:

Failure modes:

Business impact:

Evidence/verification:

Open questions:
```

First ADR prompts:

| ADR | Project | Why it matters |
| --- | --- | --- |
| Use background jobs for long-running sync work | Both | Repeated market requirement; avoids request-bound work |
| Separate provider-specific handlers from generic workflow concepts | RDrive DataBridge | Strong integration-platform story |
| Store webhook event records for idempotency | RefineBridge cautious | Billing/access reliability |
| Enforce account boundaries server-side | RefineBridge cautious | SaaS security and auth |
| Use metadata-driven folder rules | RDrive DataBridge | Business workflow configurability |
| Expose sync/job status to users/admins | Both | Operational visibility and support |
| Keep RefineBridge claims verified/unknown/planned | RefineBridge | Interview credibility |
| Use PostgreSQL/SQL as source of truth for core state | RefineBridge cautious | Data modeling and consistency |
| Treat provider discovery as explicit estimate risk | RDrive DataBridge | Stakeholder communication |
| Keep LeetCode prep light unless target roles change | Career system | Market fit and opportunity cost |

Expected output:
- 3 ADRs in first week.
- 10 ADRs across the full practice cycle.

Scoring notes:
- Score 3 when context, decision, and tradeoff are clear.
- Score 4 when failure mode and business impact are included without overclaiming.

## Mock-Session Structures

These are structures for later practice. Do not treat them as issue #12's first diagnostic unless Richard explicitly asks.

### 15-Minute Solo Dry Run

```text
Minute 0-2: State the problem and users.
Minute 2-5: Draw or describe main components.
Minute 5-8: Walk one core workflow.
Minute 8-11: Discuss failure modes and reliability.
Minute 11-13: Discuss security/account/privacy boundary.
Minute 13-15: Tradeoffs and what I would improve now.
```

Output:
- Recording or written transcript.
- Score.
- One revised answer.

### 30-Minute Project Design Mock

```text
0-3: Problem framing and requirements.
3-7: High-level architecture.
7-12: Data model and API boundaries.
12-18: Background jobs, retries, idempotency.
18-22: Security/account/privacy.
22-26: Observability/support and failure recovery.
26-30: Tradeoffs, alternatives, and improvement plan.
```

Output:
- Diagram.
- Follow-up questions missed.
- Stronger answer draft.

### 45-Minute Senior-Style Mock

```text
0-5: Requirements and constraints.
5-10: System shape.
10-18: Deep dive into one workflow.
18-25: Data model/API/background job details.
25-32: Failure modes, consistency, idempotency, retries.
32-37: Security/account/privacy.
37-42: Observability, operations, support.
42-45: Tradeoffs, alternatives, and business impact.
```

Output:
- Diagram.
- ADR candidate.
- Weak-spot update.
- Follow-up practice action.

## Diagram Prompts

Create simple diagrams, not polished portfolio art.

RDrive DataBridge:
- Form Events flow.
- Synchronization flow.
- Provider handler/capability model.
- Background job/status flow.

RefineBridge:
- Cautious system shape.
- Billing/webhook/access state.
- Account boundary model.
- Background job/run/status model.

Expected output:
- Box-and-arrow diagram or Mermaid diagram.
- 3 tradeoffs.
- 3 failure modes.
- 3 open questions.

## First Two-Week System Design Plan

Week 1:
- RDrive DataBridge 10-minute walkthrough.
- RDrive Synchronization failure-mode table.
- ADR: background jobs for long-running sync work.
- ADR: provider-specific handlers vs generic workflow.

Week 2:
- RefineBridge cautious architecture walkthrough.
- RefineBridge verified/planned/unknown claim table.
- ADR: webhook idempotency.
- ADR: server-side account boundaries.

Expected outputs:
- 2 diagrams.
- 4 ADRs.
- 2 scored walkthroughs.
- 1 list of verification questions for RefineBridge.

## Completion Standard

This pack is useful when it produces:
- RDrive DataBridge architecture diagram.
- RefineBridge cautious architecture diagram.
- 10 short ADRs.
- 4 recorded or written system-design walkthroughs.
- 1 mock-session debrief after issue #12 establishes the first diagnostic baseline.

