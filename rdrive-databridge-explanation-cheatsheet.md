# RDrive DataBridge Explanation Cheatsheet

Current as of 2026-05-30.

## 30-Second Version

> I built RDrive DataBridge, a configurable integration platform for Snagr/RDrive. It had two main sides: Form Events pushed RDrive forms and metadata out to platforms like Aconex, Azure Blob, Autodesk, and Asite; Synchronization pulled large existing document libraries back from those platforms into RDrive. The big learning experience was refactoring it from an Aconex-specific uploader into a generic pipeline with vendor strategies, dynamic folder mapping, background jobs, health checks, retries, token/session handling, and user-visible status.

## Product-Page Version

Use this when you want to connect your experience to the public RDrive page:

> I was the main engineer behind RDrive Data Bridge, the product RDrive now describes as a data integration platform for automating push/pull document workflows across systems like Aconex, Asite, Autodesk Construction Cloud, and Azure Blob Storage. My work was the engineering platform underneath that: configurable mappings, provider integrations, metadata handling, dynamic folder organisation, background sync, retries, health checks, and status visibility.

Careful boundary:

> SharePoint and 4Projects were discussed as next integrations and appear in the product positioning, but the integrations I should claim directly are the ones I built or substantially implemented: Aconex, Azure Blob Storage, Autodesk, and Asite.

## 90-Second Version

> Snagr/RDrive had field users creating forms such as safety or health forms. When those forms changed status, RDrive/Azure events sent a form-event history payload to my endpoint. The payload included details like project and form code. My API checked whether that project had a saved integration, then whether that form code/status had mappings configured in our Vue UI.
>
> If it matched, DataBridge downloaded the generated RDrive PDF/export package, which could include a zip, attached files, and metadata. Then it uploaded the files and metadata to the configured destination. For example, a signed-off safety form might need to go to a specific Aconex folder, with folders built from metadata like drawing or location.
>
> The second side was Synchronization, which worked the opposite direction. Customers often already had thousands of documents in Aconex or Asite, and they needed those pulled into RDrive projects. Users could configure synchronization locations and dynamic folder paths, such as building RDrive folders from vendor metadata like category, location, subcontractor, drawing name, file type, and filename.
>
> It started as an Aconex uploader, but the main growth was turning it into a generic integration pipeline as Azure Blob, Autodesk, and Asite were added. Each vendor had different credentials, folder models, permissions, metadata rules, and upload/download behavior, so I introduced stronger types, strategies, configurable mappings, background processing, health checks, retries, and status updates.

## Two Product Halves

| Area | Direction | What it did |
| --- | --- | --- |
| Form Events | RDrive -> provider | Reacted to RDrive form/status events, downloaded the RDrive PDF/export package, then uploaded files and metadata to Aconex/Azure Blob/Autodesk/Asite. |
| Synchronization | Provider -> RDrive | Pulled existing documents from Aconex/Asite/Autodesk into RDrive projects, creating RDrive folder hierarchies dynamically from vendor metadata. |

They could also be composed:

> A user could configure Form Events to upload matching RDrive forms into a vendor folder such as `XYZ`, then configure Synchronization to pull that same vendor folder back into an RDrive project on a schedule, for example every few hours.

## Simple Mental Model

```text
Form Events:
RDrive/Azure form event
  -> DataBridge endpoint
  -> find project integration
  -> find form/status mapping
  -> download RDrive PDF/export package
  -> parse files and metadata
  -> build destination folder path
  -> upload files + metadata to vendor
  -> log result and show status

Form Event Mapping:
RDrive process template
  -> list available form statuses
  -> user maps statuses to vendor-side targets/actions
  -> matching future events follow those rules

Synchronization:
Vendor document library
  -> search/read vendor metadata
  -> match synchronization mappings
  -> build dynamic RDrive folder path
  -> create missing RDrive folders
  -> download vendor files
  -> upload into RDrive project hierarchy
  -> log result and show status

Composed workflow:
RDrive form event
  -> upload to vendor folder XYZ
  -> scheduled synchronization watches/pulls folder XYZ
  -> documents appear back in configured RDrive project hierarchy

Background operations:
Scheduled synchronization / health check / token rotation
  -> show last run, next run, state
  -> allow manual run/configuration
```

## Explain It Like A Product

> DataBridge let non-developers configure document workflow rules in both directions. It could push RDrive form packages out to external platforms when forms reached certain statuses, and it could also pull thousands of existing vendor documents back into RDrive while automatically creating a clean folder hierarchy from metadata. Because both sides were configurable, customers could compose workflows, such as pushing forms to a vendor folder and then scheduled-syncing that folder back into a selected RDrive project.

Simple configuration example:

> For Azure Blob, a user could configure the uploaded folder path from RDrive fields instead of asking a developer to hardcode it. For example: `Processes / Process profile code / Process profile title / Client id`, with optional fields like project code, location title, drawing title, category, created-by team, or custom folders.

Setup example:

> Creating an integration was a guided admin flow: select the vendor, enter RDrive credentials, enter provider credentials, then configure provider-specific options. The hard part was making that flow generic enough for multiple vendors while still allowing each provider's auth, folders, permissions, and options to differ.

## Explain It Like An Engineer

> Architecturally, it became two related integration pipelines that could be composed. Form Events handled RDrive-to-vendor workflows triggered by form status changes. Synchronization handled vendor-to-RDrive workflows by searching vendor document libraries, reading metadata, building dynamic folder paths, creating missing RDrive folders, downloading vendor files, and uploading them into the RDrive project hierarchy. Shared concepts included integration credentials, mappings, metadata, folder paths, task state, health checks, and sync logs. Vendor-specific behavior lived behind capability metadata and strategy-style handlers.

## Explain The Refactor

Bad:

> I refactored it to be more generic.

Better:

> The first version was mostly an Aconex upload flow. Once the business asked for Azure Blob, Autodesk, and Asite, the Aconex-specific assumptions became a problem. I started pulling out common concepts like integration type, credentials, form mappings, status mappings, metadata, folder paths, upload result, and health state. Then vendor-specific logic moved into separate strategies/handlers. That let the pipeline stay mostly the same while each vendor handled its own upload quirks.

## Explain Why New Integrations Took Time

Bad:

> Every integration had quirks and took longer than they expected.

Better:

> From the outside, a new provider could look like "just implement the same interface again." In practice, each provider changed the shape of the system: authentication, permissions, folder models, metadata fields, upload/download APIs, token/session behavior, rate limits, and failure handling were all different. Some of the pipeline was reusable, but each provider still required discovery, architecture adjustment, implementation, testing against real API behavior, and reliability work.

Concrete example:

> Autodesk looked like another provider integration, but late in the work I discovered that drawings were downloaded in chunks rather than through a simple file download. That added about six extra implementation steps near the end. Folder creation also required checking permissions at each level, because each folder could have different access rules. Those are the kinds of provider-specific details you do not fully know until you exercise the real API with real project data.

## Explain The Estimation Lesson

> One lesson I took from DataBridge is that honest estimates need visible decomposition. If I say "this will take two months," I need to show why: provider discovery, auth/session handling, metadata mapping, folder model, upload/download behavior, background processing, error handling, UI configuration, testing, and rollout. Otherwise stakeholders only see "add another integration" and assume it is mostly copy/paste.

Practical estimate framing:

```text
Reusable pipeline work: already exists / minor changes
Provider discovery: unknowns around auth, folders, metadata, permissions
Implementation: API client, mapping, upload/download, UI config
Reliability: retries, health checks, logging, token/session handling
Validation: real account testing, edge cases, failed uploads, permissions
Risk: provider API gaps, chunked transfers, per-folder permissions, or unexpected metadata behavior
```

Better wording when challenged:

> Part of the work is reusable, but the risky part is discovering where this provider is not actually equivalent to the last one. In previous integrations, the delays came from late API behavior such as chunked downloads, folder-level permissions, auth/session differences, or metadata rules that only became clear with real project data.

## Explain Synchronization

Bad:

> It synced documents from Aconex to RDrive.

Better:

> Synchronization handled the opposite direction from Form Events. Many customers already had thousands of documents in Aconex or Asite. DataBridge could search those vendor libraries, read each document's metadata, and use configurable synchronization locations to build a matching folder hierarchy inside RDrive. For example, a rule could create paths like `/Sync Location/Category/{category}/Location/{location}/Sub Contractor/{name}/...`, then download and store the documents in the right place. That meant a customer could sync thousands of drawings or photos into RDrive with a click, already organized the way they wanted.

Concrete UI example:

> A user could define a Synchronization Location like `Test File / File Name / Purpose Of Issue`, using metadata fields such as doc ref, revision, doc title, status, and revision notes. Then they could create a mapping by selecting a provider folder/source tree, optionally including subfolders, and filtering documents by metadata such as `Purpose of Issue = RDrive-Drawing` and `Status = Fire Approved`. The sync job would then pull matching documents into RDrive under the configured folder structure.

## Explain How The Two Sides Worked Together

> The two halves were separate but could be configured to work together. For example, Form Events could upload signed-off forms into a vendor folder called `XYZ`. Then Synchronization could be configured to watch or pull that same `XYZ` folder back into a selected RDrive project every few hours. So customers could build a round-trip workflow without hardcoding a special case: event-driven upload on one side, scheduled folder synchronization on the other.

## Explain The Admin UI

> The admin UI exposed the system as configuration instead of code. Users could create an integration, choose a vendor, enter RDrive and provider credentials, map RDrive form templates and statuses to vendor actions, configure dynamic folder structures, and monitor scheduled jobs like Synchronization, Health Check, and Token Rotation.

Operational admin example:

> Editing an integration showed the active/paused state, RDrive credentials, provider account credentials, health check, status history, form-event PDF download options, export templates, and pause/disable controls. That matters because integrations need lifecycle management: setup, monitoring, recovery, and controlled shutdown when something is unhealthy.

## Business Impact

> The impact was reducing manual document admin in both directions. Field users could create or close forms in RDrive and have those packages pushed to the external platforms their clients required. Customers could also pull large existing document libraries from Aconex/Asite/Autodesk into RDrive and automatically organize them by metadata-driven folder rules. In some cases, the two sides could be chained together as a configurable workflow rather than a one-off integration.

## Strong Interview Angles

- Ambiguous requirements: "They would say, now we need this to work for Azure Blob/Asite, and I had to work out the architecture."
- Refactoring under growth: "The system grew from one vendor into a generic pipeline."
- Estimation under uncertainty: "Each provider exposed different auth, metadata, folder, and permission models."
- Two-way integration: "Form Events pushed RDrive data out; Synchronization pulled vendor libraries back into RDrive."
- Workflow composition: "The two sides could be configured together, e.g. upload to vendor folder XYZ, then scheduled-sync XYZ back to RDrive."
- Dynamic folder mapping: "Vendor metadata became RDrive folder hierarchy."
- Integration reliability: "External APIs fail differently, so health checks/retries/status were essential."
- Late provider discovery: "Autodesk added late complexity because drawing downloads were chunked and folder permissions had to be checked at each level."
- User-facing configuration: "Users configured mappings in the UI instead of developers hardcoding rules."
- Business impact: "It automated manual document transfer and metadata entry."
- Solo ownership: "I owned the design and implementation, mostly independently."

## Questions You Can Answer With This Story

- Tell me about a complex project you owned.
- Tell me about a system you had to refactor.
- Tell me about working with vague requirements.
- Tell me about integrating third-party APIs.
- Tell me about a time architecture evolved.
- Tell me about reliability/failure handling.
- Tell me about a project that gave you confidence.

## One-Sentence Link To RefineBridge

> RefineBridge came from the same pattern I learned with RDrive DataBridge: configurable integrations, external APIs, background jobs, metadata mapping, and making messy business workflows reliable enough for users.

## Technical Growth Arc

> DataBridge was the first large product where I owned almost everything end-to-end: .NET backend, database, vendor APIs, background jobs, admin workflows, and a Vue/Vuetify SPA that I learned while delivering. RefineBridge is the more deliberate continuation: .NET backend, Nuxt/Vue 3 frontend, PostgreSQL, modular monolith structure, DDD-ish boundaries, and functional design where it makes the code clearer without becoming dogmatic.
