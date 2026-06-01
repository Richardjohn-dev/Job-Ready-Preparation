# RDrive DataBridge Case Study

Current as of 2026-06-01.

Purpose: private case study for CV bullets, LinkedIn phrasing, interviews, system-design practice, and mentor review. Keep public versions sanitized.

## Claim Boundary

Use confidently:
- Long-term independent developer/contractor work for Snagr/RDrive.
- Built and owned major engineering work on RDrive DataBridge.
- Implemented/evidence-backed providers: Aconex, Azure Blob Storage, Autodesk, and Asite.
- Built two primary workflow areas: Form Events and Synchronization.
- Built configuration, admin UI, background processing, health/status visibility, retries, token/session handling, and provider-specific behavior handling.

Do not claim from current evidence:
- SharePoint implementation.
- 4Projects implementation.
- Sales, marketing, adoption, revenue, user counts, or formal employee status.
- Raw client/project identifiers, live URLs, usernames, credentials, screenshots, or unredacted customer data.

## 30-Second Explanation

I built RDrive DataBridge, a configurable integration platform for Snagr/RDrive. It had two main sides: Form Events pushed RDrive form packages and metadata out to providers such as Aconex, Azure Blob Storage, Autodesk, and Asite; Synchronization pulled existing provider document libraries back into RDrive and organized them with metadata-driven folder rules. The technical growth was moving from an Aconex-focused uploader toward a generic integration pipeline with provider strategies, mappings, background jobs, health checks, retries, token/session handling, and user-visible status.

## 2-Minute Explanation

RDrive DataBridge solved a document workflow problem: project teams had forms, PDFs, files, and metadata in RDrive, while clients or partners often required documents to move through external systems such as Aconex, Azure Blob Storage, Autodesk, or Asite.

The first side was Form Events. When a form changed in RDrive, an event payload came into DataBridge. The system checked whether that project had an integration configured, checked whether the form/status matched a mapping from the admin UI, downloaded the RDrive PDF/export package, extracted files and metadata, built the target folder path, and uploaded the package to the configured provider.

The second side was Synchronization. A key scenario was pulling an existing external document library into RDrive. DataBridge could search provider documents, read metadata, apply configured filters and folder rules, create the matching folder hierarchy inside RDrive, download the provider files, and upload them into the correct RDrive project folders.

The two sides could also be composed. For example, a workflow could push signed-off RDrive form packages into a provider folder, then a scheduled synchronization could pull that provider folder back into a selected RDrive project. That made the product configurable workflow plumbing rather than a collection of one-off scripts.

Architecturally, the project evolved from provider-specific upload behavior into reusable concepts: integrations, credentials, mappings, metadata fields, folder paths, vendor capabilities, task state, sync logs, health checks, and provider-specific handlers. The hard part was not only calling external APIs; each provider had different authentication, permissions, folders, metadata, upload/download behavior, token/session lifetimes, and failure modes.

## Product Problem

Problem:
Project teams needed RDrive to fit into external document-management workflows instead of forcing manual upload, download, renaming, metadata entry, and folder organization.

Constraint:
Each external provider behaved differently. Authentication, folders, permissions, metadata schemas, transfer APIs, token/session handling, and failures were not uniform across Aconex, Azure Blob Storage, Autodesk, and Asite.

Decision:
Build a configurable integration platform with shared workflow concepts and provider-specific implementation layers.

Tradeoff:
The platform took more design work than a single hardcoded connector, but it reduced repeated custom work as more providers and customer workflows were added.

Result:
RDrive could support repeatable push/pull document workflows through configuration: form/status-triggered exports, provider document imports, dynamic folder structures, scheduled background sync, and operational status visibility.

## System Shape

```text
RDrive form/status event
  -> DataBridge endpoint
  -> project integration lookup
  -> form/status mapping lookup
  -> RDrive export/PDF package download
  -> file and metadata extraction
  -> provider-specific folder/upload behavior
  -> logs, status, retries, health visibility

Provider document library
  -> provider search/read metadata
  -> synchronization mapping/filter lookup
  -> dynamic RDrive folder path generation
  -> create missing RDrive folders
  -> download provider documents
  -> upload into RDrive project hierarchy
  -> sync logs, results, status updates
```

## Form Events

Form Events handled RDrive-to-provider automation.

Typical flow:
1. RDrive or Azure event sent a form-event history payload.
2. DataBridge identified the RDrive project and form code.
3. The API checked for a configured integration for that project.
4. The API checked whether the form/status had a configured mapping.
5. DataBridge downloaded the generated RDrive PDF/export package.
6. The package could include PDFs, attached files, zip content, and metadata.
7. The pipeline built the provider destination from mapping and metadata rules.
8. Vendor-specific code uploaded files and metadata.
9. Logs/status were recorded for operational visibility.

Interview example:
A field user updates a safety or project form. When it reaches a configured status, DataBridge finds the matching integration rule, downloads the RDrive package, builds the provider destination from metadata such as location, drawing, project code, or template, and uploads the documents to Aconex, Azure Blob Storage, Autodesk, or Asite according to that provider's rules.

## Synchronization

Synchronization handled provider-to-RDrive imports.

Typical flow:
1. A provider already held an existing document library.
2. DataBridge searched provider folders/documents and read metadata.
3. Users configured synchronization locations and mappings in the admin UI.
4. The configured RDrive folder path could use provider metadata tokens.
5. DataBridge created missing RDrive folder levels.
6. It downloaded provider files and uploaded them into RDrive.
7. It recorded sync logs/results and exposed status.

Example folder concept:

```text
/Sync Location/Category/{category}/Location/{location}/Sub Contractor/{name}/...
```

Product value:
Instead of dumping a large provider document library into a flat folder, DataBridge could preserve useful organization by using provider metadata to create the RDrive folder hierarchy.

## Composition

Form Events and Synchronization were separate capabilities, but they could be configured together.

Example:
1. Form Events upload matching RDrive form packages into a provider folder.
2. A scheduled Synchronization mapping watches or pulls that provider folder.
3. Matching documents are pulled back into a selected RDrive project hierarchy.

Why this matters:
The system was not only "upload to vendor" or "download from vendor." It could support round-trip or chained document workflows through configuration.

## Architecture Evolution

Starting point:
The project began closer to an Aconex-specific upload workflow.

Pressure:
Azure Blob Storage, Autodesk, and Asite introduced different provider behaviors. Provider-specific assumptions became harder to maintain.

Evolution:
- Pulled common concepts into reusable types: integrations, credentials, mappings, statuses, metadata, folders, upload/download results, health state, and task state.
- Moved vendor differences into provider handlers/strategies and capability metadata.
- Modeled vendor variation through generic conditions and behavior groups where possible.
- Added background queues for synchronization, health checks, token rotation, and reruns.
- Added status/history visibility so long-running integration work was not invisible to users.

Tradeoff:
Generic abstractions helped reuse, but each provider still needed discovery and real API testing. The reusable pipeline did not eliminate provider-specific work.

## Provider Complexity

Each provider differed across:
- Authentication and session/token lifecycle.
- Folder/project model.
- Permission checks.
- Metadata schema.
- Upload/download APIs.
- Large file and chunked transfer behavior.
- Error responses and retry behavior.
- Rate limits or operational constraints.
- UI configuration needs.

Concrete example:
Autodesk introduced late complexity because drawing downloads were chunked rather than a simple file download, and folder creation required permission checks at each level. This is a useful estimation and stakeholder-communication story: new providers often look like "another connector" from the outside, but each one can change the real implementation shape.

## Operational Reliability

Reliability concerns:
- Long-running sync work should not depend on a single request lifecycle.
- External APIs fail, expire sessions, throttle, or return partial failures.
- Users need to know whether jobs are running, idle, failed, paused, or recoverable.

Capabilities evidenced in local notes/code evidence:
- Hangfire-style background queues.
- Synchronization, health-check, token-rotation, and status-history rerun jobs.
- Retry and circuit-breaker policies.
- Health checks for RDrive and providers.
- Token/session refresh and rotation.
- Sync logs and result records.
- Pause/disable behavior when integrations are unhealthy.
- SignalR-style UI updates for task/status visibility.

Interview framing:
Integrations are reliability problems, not just API problems. DataBridge needed retries, health checks, token/session handling, queue coordination, logs, and user-visible status so external failures did not silently break document workflows.

## Admin And Configuration UI

The admin UI exposed integration behavior as configuration:
- Vendor selection.
- RDrive credentials.
- Provider credentials.
- Provider-specific options.
- Form-event mappings by process/template/status.
- Dynamic folder structures.
- Synchronization locations and mappings.
- Provider folder/source selection.
- Metadata filters.
- Background service status and manual controls.
- Health/status/history views.

Why this matters:
The product let users adjust workflows without asking for a code change every time a form status, destination folder, or metadata-driven structure changed.

## Business Value

Public-safe value statement:
DataBridge reduced manual document handling by letting teams configure repeatable rules for moving documents and metadata between RDrive and external systems.

More detailed version:
- RDrive form packages could be pushed to required external platforms when forms reached configured statuses.
- Existing provider document libraries could be pulled into RDrive and organized by metadata-driven folders.
- Admin users could configure mappings, folder rules, provider credentials/options, and job controls.
- Operational status made integration work easier to monitor and recover than silent manual or script-based transfers.

Avoid saying:
- How many customers used it.
- How much revenue it generated.
- That the work drove adoption.
- That every public-product-page connector was implemented.

## Interview Stories This Supports

- Complex project ownership.
- Ambiguous requirements becoming a real system.
- Refactoring from one-off provider logic into a reusable platform.
- Third-party API integration and provider-specific failure modes.
- Background jobs, retries, health checks, and operational visibility.
- Metadata-driven folder and document workflows.
- Estimation under uncertainty.
- Working independently while making hidden engineering work visible.
- What I would design differently now.

## What I Would Improve Now

- Document provider-specific discovery before committing timelines.
- Make unknowns explicit: auth, permissions, metadata, transfer behavior, error handling, and real-account testing.
- Add stronger automated integration-test boundaries where provider APIs allow it.
- Improve public-safe documentation and diagrams earlier.
- Separate reusable pipeline work from provider-specific risk in stakeholder estimates.
- Continue moving frontend architecture from early Vue/Vuetify patterns toward more deliberate modern Vue/Nuxt practices.

## Confidentiality Boundaries

Private-only:
- Raw screenshots unless redacted.
- Live system URLs.
- Client/project names or IDs.
- Usernames, roles, credentials, account details, or tenant data.
- Any customer document metadata or project-specific folder names that identify a live project.

Public-safe:
- Sanitized architecture descriptions.
- Provider list limited to Aconex, Azure Blob Storage, Autodesk, and Asite.
- High-level workflow diagrams.
- Redacted screenshots only after manual review.
- No sales/adoption/revenue/user-count claims.

## Reusable CV Bullets

- Built and owned RDrive DataBridge, a configurable two-way integration platform connecting RDrive with Aconex, Azure Blob Storage, Autodesk, and Asite across form-event workflows and document synchronization.
- Designed metadata-driven synchronization flows that searched provider document libraries, generated RDrive folder hierarchies, transferred files, retried failures, and recorded sync results.
- Refactored an Aconex-focused upload flow into a broader provider pipeline with reusable integration, credential, mapping, folder, metadata, health, and task-status concepts.
- Implemented operational capabilities around background synchronization, health checks, token/session rotation, retries, pause/disable behavior, and user-visible status.
- Built admin workflows for integration setup, provider credentials/options, form-event mappings, synchronization locations, metadata filters, folder rules, and job controls.

## Open Questions

- Exact date range for DataBridge ownership.
- Preferred public role/title wording for Snagr/RDrive.
- Which screenshots can be redacted into a public portfolio version.
- Whether any verified impact metrics can be safely used without implying sales/adoption ownership.
- Whether there are additional production-implemented providers beyond Aconex, Azure Blob Storage, Autodesk, and Asite.
