# RDrive DataBridge Code Evidence

Current as of 2026-05-30.

Repo inspected:

`F:\Projects\SnagR\RDrive-Aconex-Integrator`

## High-Level Read

This project is strong evidence of real product ownership.

It was not just a one-off Aconex connector. The repo shows a configurable two-way integration platform with:

- ASP.NET Core API.
- Vue 2/Vuetify SPA.
- Entity Framework/SQL Server persistence.
- ASP.NET Identity.
- MediatR command/query style.
- Hangfire background processing.
- SignalR UI status updates.
- Vendor health checks.
- Token/session rotation.
- RDrive document/PDF services.
- Vendor-specific services for Aconex, Azure Blob, Autodesk, and Asite.
- Configurable form-event mapping.
- Configurable document synchronization.
- Generic vendor conditions/behaviour groups.
- PowerBI/reporting endpoints.

## Product Flows

DataBridge had two main product flows.

### 1. Form Events: RDrive -> Provider

1. A field user creates or updates a form in RDrive.
2. RDrive/Azure events send a form-event history payload to DataBridge.
3. DataBridge checks whether the project URL/project identity has a saved integration.
4. It checks whether the form code/status has mappings configured in the Vue UI.
5. If matched, it downloads the RDrive PDF/export package.
6. The package can include a PDF, zip/files, and metadata.
7. DataBridge uses metadata and mapping rules to build the destination folder/file structure.
8. It uploads files and metadata into Aconex, Azure Blob, Autodesk, or Asite.
9. It records logs/results and updates the UI.

### 2. Synchronization: Provider -> RDrive

1. A customer has an existing document library in a provider such as Aconex, Asite, or Autodesk.
2. DataBridge searches/reads the provider documents and metadata.
3. Users configure synchronization locations in the UI.
4. The configured RDrive folder path can be dynamic, using provider metadata fields.
5. DataBridge creates the missing RDrive folder hierarchy.
6. It downloads vendor files and uploads them into the generated RDrive project folders.
7. It records sync logs/results and updates the UI.

Example folder concept:

```text
/Sync Location/Category/{category}/Location/{location}/Sub Contractor/{name}/...
```

This let customers sync thousands of provider documents into RDrive already organized by metadata.

### 3. Composed Workflows

Because Form Events and Synchronization were both configurable, they could be used together.

Example:

1. Configure Form Events to upload matching RDrive form packages into vendor folder `XYZ`.
2. Configure Synchronization to pull vendor folder `XYZ` into a selected RDrive project.
3. Run that synchronization on a schedule, for example every few hours.

This matters because the product was not just two isolated features. It allowed configurable workflow composition across RDrive and external platforms.

Simple mental model:

```text
Form Events:
RDrive/Azure form event
  -> DataBridge endpoint
  -> integration lookup
  -> form/status mapping lookup
  -> RDrive export/PDF package download
  -> metadata/files parsed
  -> vendor-specific upload strategy
  -> logs/status/results

Synchronization:
Vendor document library
  -> vendor search/read metadata
  -> synchronization mapping lookup
  -> dynamic RDrive folder path
  -> create missing RDrive folders
  -> download vendor files
  -> upload into RDrive hierarchy
  -> logs/status/results

Composed workflow:
RDrive form event
  -> vendor folder XYZ
  -> scheduled synchronization
  -> RDrive project hierarchy
```

## Tech Stack Evidence

Backend:

- `.NET 9` target in `RDAIntegrator.API.csproj`.
- EF Core + SQL Server.
- ASP.NET Identity.
- MediatR.
- Hangfire.
- SignalR.
- Polly retry/circuit-breaker policies.
- Serilog file logging.
- LazyCache.
- Azure Blob SDK.
- Autodesk Forge SDK.
- CsvHelper.
- FluentValidation.

Frontend:

- Vue 2.
- Vue Router.
- Vuex.
- Vuetify.
- SignalR client.

## Main Domains In The Code

Application folders:

- `Document Synchronization`
- `Form Events`
- `Health Checks`
- `Integrations`
- `PowerBI`
- `Shared`
- `Task Management`

Approximate file concentration under `Application`:

- `Integrations`: 182 files
- `Shared`: 158 files
- `Document Synchronization`: 90 files
- `Form Events`: 64 files
- `Task Management`: 54 files
- `Health Checks`: 36 files
- `PowerBI`: 8 files

This supports the claim that the project grew into a platform with multiple operational subsystems.

## Core Data Model Evidence

`ApplicationDbContext` contains first-class tables for:

- Integrations
- Integration logs
- RDrive credentials/options
- Vendor conditions
- Vendor behaviour groups
- Tokens
- Basic and advanced file-storage credentials
- Synchronization locations
- Synchronization mappings
- Synchronization mapping folder options
- Synchronization vendor filters
- Synchronization logs/results
- Form event logs
- Form event process/status mappings
- Form event options
- Form event documents/details

This is useful interview evidence because it shows:

- The project had persistent configuration, not hardcoded flows.
- It tracked sync history/results.
- It separated form-event workflows from document synchronization.
- It modeled vendor-specific variation without creating totally separate products per vendor.
- It supported both RDrive-to-provider event workflows and provider-to-RDrive bulk synchronization.
- Those flows could be composed, for example event upload into a provider folder followed by scheduled synchronization back into RDrive.

## Vendor Support Evidence

The `IntegrationType` enum defines:

- `Aconex`
- `AzureBlob`
- `Asite`
- `AutoDesk`

Vendor-specific code exists for:

- Aconex form events, document schema, document upload/search, and sync fields.
- Azure Blob form-event upload.
- Autodesk folder/project selection, document service, and chunked download flow.
- Asite workspaces, folders, profile/session, upload metadata, and form events.

## Configurable Vendor Behaviour Pattern

The `CustomConditionalsAndBehaviours.md` file documents a reusable pattern:

- Backend defines vendor-specific meaning statically.
- Database stores generic condition/behaviour identifiers.
- SPA receives vendor metadata plus integration-specific selections.
- Frontend overlays saved selections onto static vendor definitions.
- Runtime backend maps generic selections back into vendor-specific behaviour.

This is an important senior-level story:

> Instead of creating bespoke tables and forms for every vendor-specific option, I modeled vendor variation as generic conditions and behaviour groups. That allowed the product to support different vendor capabilities while keeping persistence and UI flows reusable.

## Background Processing Evidence

`QueueMaster` coordinates:

- Synchronization queue.
- Health check queue.
- Token rotation queue.
- Overflow queues when one service is already active.
- SignalR notifications to the SPA.
- Background service status changes.

Service registration shows:

- Hangfire server with multiple synchronization queues.
- Dedicated health-check queue.
- Dedicated token-rotation queue.
- Status-history rerun queue.
- Hosted services for synchronization, health checks, and token rotation.

This supports stories about:

- Long-running work outside request/response.
- Preventing competing background jobs from stepping on each other.
- Real-time UI visibility.
- Operational recovery when work is queued or delayed.

## Reliability Evidence

Reliability mechanisms found:

- Polly retry policies.
- Circuit breaker policies for vendor HTTP clients.
- Health checks for RDrive and vendor endpoints.
- Integration pause/disable flows when health checks fail.
- Token/session refresh/rotation.
- Sync logs and mapping result records.
- Retry handling for failed document uploads.
- Separate handling for full failure vs partial success.
- Status-history rerun service for missed form status histories.

Good interview framing:

> I learned that integrations are reliability problems more than just API problems. The system needed health checks, retries, pause/disable behavior, token refresh, queue coordination, and user-visible status so failed external systems did not silently break customer workflows.

## Document Synchronization Evidence

`VendorSynchronizationService` coordinates:

- Checking sync mappings and credentials.
- Building RDrive request details.
- Requesting vendor access/session tokens.
- Searching vendor documents.
- Restoring RDrive folders if needed.
- Preparing folder hierarchies.
- Creating missing RDrive folders by depth.
- Uploading vendor documents back into RDrive.
- Handling individual documents and document version stacks.
- Retrying failed uploads.
- Updating sync logs/results.

This supports a detailed system design explanation:

1. Load integration and mapping configuration.
2. Validate credentials and token/session requirements.
3. Search vendor documents using vendor-specific handlers.
4. Resolve or create RDrive folder hierarchy.
5. Download vendor documents via stream or chunk strategy.
6. Upload into RDrive.
7. Record sync results and failures.
8. Notify UI through background-task status updates.

The important product point:

> Synchronization was the reverse of Form Events. Instead of pushing a new RDrive form package out, it pulled existing vendor documents down into RDrive and built a clean RDrive folder hierarchy from vendor metadata.

## Frontend Evidence

The Vue SPA includes:

- Integration creation stepper.
- Vendor credential forms.
- Form-event mapping UI.
- Document synchronization view.
- Folder tree/mapping components.
- Background service status UI.
- Sync trigger/result/status components.
- Vendor-specific Autodesk, Asite, Aconex, Azure Blob configuration components.

This matters because the project was not backend-only. It had customer-facing configuration UI.

## Strong Resume Bullets

- Built and owned RDrive DataBridge, a configurable two-way integration platform connecting RDrive with Aconex, Azure Blob Storage, Autodesk, and Asite across form-event workflows and document synchronization.
- Designed reusable vendor capability modeling using generic conditions and behaviour groups, reducing the need for bespoke persistence/UI paths for each vendor.
- Implemented background synchronization, health-check, token-rotation, and status-history rerun queues with Hangfire and SignalR-backed UI status updates.
- Built document synchronization workflows that searched vendor systems, resolved folder hierarchies, transferred documents into RDrive, handled version stacks, retried failures, and recorded sync results.
- Implemented metadata-driven synchronization locations that could bulk-import thousands of provider documents into dynamically generated RDrive folder hierarchies.
- Enabled composed workflows where event-driven provider uploads and scheduled provider-to-RDrive synchronizations could work together through shared folder/configuration conventions.
- Integrated reliability patterns including Polly retries, circuit breakers, health-state tracking, pause/disable flows, token/session refresh, and sync logging.

## Interview Answer Upgrade

Weak:

> I made integrations from RDrive to Aconex, Azure Blob, Autodesk, and Asite.

Stronger:

> I built a configurable two-way integration platform for RDrive that supported both form-event automation and document synchronization across Aconex, Azure Blob, Autodesk, and Asite. Form Events pushed RDrive forms and metadata out to vendors. Synchronization pulled existing vendor document libraries back into RDrive and built folder hierarchies from metadata. The hard part was not just calling APIs; each vendor had different credentials, metadata, folder models, token/session behavior, and failure modes. I modeled common integration concepts generically, then handled vendor-specific behavior through capability metadata, background queues, health checks, retries, and user-visible sync status.

## What This Proves

This project proves:

- You can own a complex product over years.
- You can start from vague business requirements.
- You can adapt architecture as more vendors are added.
- You understand integrations, background jobs, sync state, credentials, and failure handling.
- You have already solved problems very similar to RefineBridge.

RefineBridge did not come from nowhere. It is the next iteration of a pattern you had already learned through RDrive DataBridge.
