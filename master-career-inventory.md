# Master Career Inventory

Current as of 2026-06-01.
Primary sources: `career-readiness-local-issues.md`, `career-readiness-system-prd.md`, `handoff-career-readiness-orchestrator.md`, `experience-story-bank.md`, `rdrive-databridge-code-evidence.md`, `rdrive-databridge-explanation-cheatsheet.md`, `stakeholder-communication-lessons.md`, `modern-dotnet-interview-readiness-map.md`.

## Purpose

Build one local evidence inventory for future CV/LinkedIn/system-design/story work.
Not a final positioning.  
No formal interview history is claimed here.

## Evidence Labels

- **confirmed from user notes**: explicitly stated by user in prior notes or handoff context.
- **code-evidence-backed**: backed by `rdrive-databridge-code-evidence.md` repo/evidence references.
- **public-page-aligned**: validated by public product messaging, not equal to implementation proof.
- **likely claim (needs confirmation)**: reasonable from context but missing hard confirmation in current artifacts.
- **needs confirmation**: missing or personal-detail dependent (dates, compensation, scope boundaries, team metrics).
- **do not claim yet**: explicitly disallowed or risky claims.

## Summary Of Strongest Claims

- Long-term .NET/full-stack work in an independent / informal contractor-style arrangement (not a formal employment claim unless confirmed).
  - Labels: confirmed from user notes.
- Built/owned major work on `RDrive DataBridge` after VB.NET maintenance context.
  - Labels: confirmed from user notes, code-evidence-backed, public-page-aligned.
- Built `RDrive DataBridge` as a configurable two-way integration platform: Form Events (RDrive -> provider) and Synchronization (provider -> RDrive), with background operational controls.
  - Labels: confirmed from user notes, code-evidence-backed.
- Current product path includes `RefineBridge` as the modern .NET/Nuxt/Postgres SaaS direction.
  - Labels: confirmed from user notes.
- Core claim boundary: no formal claim of sales, marketing ownership, user counts, conversion outcomes, or employee management duties.
  - Labels: do not claim yet.

## Work History Inventory

### High-level timeline (workstreams)

- **Long-term independent context (non-standard family-friend arrangement)**: confirmed from user notes.
- **Legacy VB.NET work (pre-DataBridge)**: legacy maintenance and bug-fix ownership, with domain familiarity built before DataBridge expansion.
- **RDrive DataBridge era**: primary integration-heavy ownership with multiple vendor providers and operational workflows.
- **RefineBridge era**: modern stack evolution and platform growth beyond legacy architecture.

### Work history framing

- Keep employment wording conservative: `independent contractor/developer` unless explicit legal employment documentation is confirmed.
- Do not introduce company-level legal titles without verification.
- Do not replace missing dates with fabricated ranges.

## Project Inventory

### Legacy Snagr/RDrive VB.NET Work

Responsibilities:
- Frontend/backend maintenance on legacy RDrive web applications.
- Bug fixing and smaller product improvements before major DataBridge ownership.
- Early domain onboarding for later integration-platform work.

Evidence:
- confirmed from user notes: long-term Snagr/RDrive context and legacy maintenance mention.
- likely claim (needs confirmation): exact scope by module and whether VB.NET ownership was continuous.

Do not overclaim:
- Do not present this as a full enterprise modernization program without evidence.

### RDrive DataBridge

Confirmed scope:
- Main project focus for the long-term integration body of work.
- Confirmed implemented providers:  
  - Aconex  
  - Azure Blob Storage  
  - Autodesk  
  - Asite
- Major product architecture components:
  - Form Events: form/process/status-triggered RDrive exports.
  - Synchronization: provider document-library import into RDrive with metadata-driven structures.
  - Integration admin + status/health/job controls.
- Responsibility evidence includes backend API, SPA administration, persistence, background jobs, reliability patterns (retries/health/token/job status), and mapping configuration.

Evidence labels:
- code-evidence-backed: domain folders for Form Events, Synchronization, Health Checks, Integrations, PowerBI; queue/job handling; auth/session/token handling; mapping and provider-specific implementations.
- confirmed from user notes: working two-way direction, years of ownership, and independent/developer context.
- public-page-aligned: public product positioning validates product intent and integration-heavy identity.

Likely claims needing confirmation:
- Any precise start/end dates and full ownership phrasing.
- Whether every listed implementation module was in every month of the period.
- Any formal performance metrics or production impact numbers.

Not claimed:
- SharePoint and 4Projects are not implemented claims from evidence-backed implementation.
- No ownership claim for sales, marketing, client acquisition, product adoption outcomes, or formal role authority.

### RefineBridge

Confirmed scope:
- Current/product-facing work described as modern stack direction.
- .NET + Nuxt/Vue 3/Postgres style platform positioning with billing/webhook/background-job/admin concerns in planning and experience notes.

Evidence labels:
- confirmed from user notes: direction and stack position.
- likely claim (needs confirmation): exact architecture maturity, live production complexity, and ownership boundaries.

Known responsibilities from notes:
- Product architecture evolution toward modern full-stack workflow.
- SaaS/system thinking in billing, auth/account boundaries, and operations-conscious delivery.
- Shift away from older Vue/Vuetify implementation style.

### Other Work / Additional Workstream

- No other large projects were strongly evidenced in this issue set.
- Keep a placeholder section here so future human-confirmed projects can be appended cleanly without replacing this inventory baseline.

## Skills And Themes

- Core technical themes (evidence-backed):
  - Configurable integration architecture.
  - API adapters and provider strategy pattern work.
  - Background processing and operational visibility.
  - Metadata-driven mapping and folder model handling.
  - Practical .NET API/EF/identity/background job patterns.
  - Vue/Vuetify legacy and Nuxt/Vue 3 progression.
- Communication themes (evidence-backed):
  - Problem -> Constraint -> Decision -> Tradeoff -> Result framing.
  - Explaining hidden complexity, especially in integrations.
  - Conservative claim framing for interview safety.

## Evidence-Backed Claims

- Ownership style: long-term independent/informal arrangement with Snagr/RDrive context.
- Legacy context: VB.NET maintenance before DataBridge ownership increase.
- RDrive DataBridge:
  - two-way integration flow exists as primary functional model;
  - provider implementations/variation are evidence-backed for Aconex/Azure Blob/Autodesk/Asite;
  - background operations exist (job scheduling/health/token/visibility).
- RefineBridge:
  - current project direction and modern stack direction are consistent across notes.

## Likely Claims Needing Confirmation

- Exact tenure windows for:
  - legacy VB.NET phase;
  - RDrive DataBridge principal ownership.
- Exact role/title used in public-facing narratives.
- Whether RefineBridge includes all stated modern features in currently shipped form.
- Scope of private operational evidence available per module.
- Whether any additional client-facing integrations were production-stable beyond the confirmed list.

## Do Not Claim Unless Confirmed

- SharePoint and 4Projects were discussed in product context but not confirmed as implemented.
- Sales ownership.
- Marketing ownership.
- Client adoption numbers or outcomes.
- Employee-level management claims (team lead/hiring manager ownership) without confirmation.
- Formal employment status (use independent/developer/contractor language unless proven otherwise).
- Full-stack ownership of every project layer at all times (unless evidence confirms it each period).
- Any operational details that identify live customers.

## Public vs Private Evidence Boundaries

- Public-safe evidence:
  - public product page references;
  - high-level architecture stories;
  - sanitized bullet stories from experience notes.
- Private/sensitive evidence (do not share publicly):
  - raw live-product screenshots;
  - client names, IDs, usernames, roles, or contact details;
  - live credentials, endpoints, tenant/project IDs, account links;
  - unreduced internal system identifiers.
- Communication rule:
  - share raw screenshots only in private review contexts with redaction, or use sanitized verbal summaries.
- DataBridge provider boundary:
  - only claim implemented integrations as Aconex, Azure Blob Storage, Autodesk, Asite unless new evidence is added.
  - public page mentions can be presented as public-positioning only.

## CV/LinkedIn Reusable Raw Material

### Reuse-ready labels
- **Safe headline language**: Full-stack .NET and SaaS engineer with integration-heavy product delivery.
- **Work framing sentence (safe)**:  
  "Long-term independent developer/contractor for Snagr/RDrive, owning integration-heavy product work across document/data workflows."
- **RefineBridge sentence (safe)**:  
  "Current modernization path using .NET + Nuxt/Vue 3 + Postgres to build SaaS-style workflow systems."
- **RDrive sentence (safe + bounded)**:  
  "Built configurable two-way integration workflows (push/pull document/data flows) for Snagr/RDrive, including operations controls and provider-specific behavior handling."

## Open Questions For Human

- Confirm formal employment vs independent status language and include legal-safe wording.
- Confirm exact date ranges for each major workstream.
- Confirm which RDrive providers were production-implemented vs planned.
- Confirm current RefineBridge public/private visibility and what can be safely described.
- Confirm whether any additional client/project details are permitted in private-only appendices.
- Confirm whether a short personal statement should call the family-friend context only in private notes or also in public profiles (currently: private-safe only).
- Provide any verified outcomes/impact metrics (if available) and permission boundaries for sharing.
