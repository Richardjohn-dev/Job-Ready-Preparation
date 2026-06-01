# Experience Story Bank

Current as of 2026-05-30.

Purpose: turn past work into clear interview, resume, LinkedIn, and mentor-review material.

## Core Positioning

You are not just "a solo dev who built a SaaS."

Stronger positioning:

> Full-stack .NET/SaaS engineer with deep experience building configurable integration pipelines, background processing systems, document/data sync workflows, and customer-facing admin tools across construction, CRM, storage, and SaaS platforms.

Even sharper:

> I build integration-heavy SaaS systems where users configure business rules, external APIs move documents/data in both directions, and reliability, metadata mapping, background jobs, and operational visibility matter.

## Major Experience 1: RDrive DataBridge

### Company Context

Snagr/RDrive was the company/product context.

Before DataBridge, you worked on their legacy web application in VB.NET, maintaining frontend/backend areas and fixing bugs independently. That work was less formal and less structured, but it built familiarity with the domain before RDrive DataBridge became the larger owned project.

### Raw Description

Worked for Snagr Software for a long period in a non-standard/family-friend arrangement, including time in England and later from Thailand. Most work was solo: business stakeholders would describe the needed outcome, then you would design and build it.

Interview/resume-safe phrasing:

> Long-term independent developer/contractor for Snagr Software, owning integration-heavy product work across RDrive and external enterprise platforms.

Use the informal/family-friend context only if specifically asked about employment structure. Do not lead with it.

The largest project was `RDrive DataBridge`, built over roughly 3-4 years.

It connected `RDrive` with:

- Aconex
- Azure Blob Storage
- Autodesk
- Asite

SharePoint and 4Projects were also discussed/requested as next integrations, but the implemented work to claim confidently is Aconex, Azure Blob Storage, Autodesk, and Asite unless later evidence shows otherwise.

### Public Product-Page Alignment

RDrive has a public product page for RDrive Data Bridge:

https://rdrive.io/en/products/rdrive-data-bridge/

Useful interview framing:

> I was the main engineer behind the platform now described publicly as RDrive Data Bridge: a central integration hub for push/pull document workflows between RDrive and external construction/document systems.

What the public page validates:

- It is a named product, not just an internal script.
- It is positioned as a data integration platform.
- It covers push and pull data/document workflows.
- It includes document-management systems such as Aconex, Asite, Autodesk Construction Cloud, SharePoint, 4Projects, and Azure Blob Storage.
- It describes configurable file organisation, metadata-driven workflows, and automated syncing.

Important boundary:

> I owned the engineering of the platform and several core connectors. I did not own sales, marketing, client adoption, or whether specific commercial opportunities converted.

### Live Product Evidence

You can still access the live DataBridge-style UI, which is useful private validation of the story.

Observed from the live UI screenshot:

- Product area: `Integrations`.
- Vendor filter includes `Aconex`, `Azure Blob`, `Asite`, and `Autodesk Construction Cloud`.
- Table includes columns for `Form Events` and `Synchronization`.
- Active integration rows exist for Azure Blob.
- Azure Blob file-structure configuration lets users compose uploaded folder paths from RDrive metadata fields and custom folders.
- Creating an integration uses a stepper-style flow: select vendor, enter RDrive credentials, enter provider credentials, then configure integration options.
- Form Event Mappings let users choose an RDrive process/form template and map each form status to a vendor-side action/destination.
- Background service controls show scheduled Synchronization, Health Check, and Token Rotation jobs with last run, next run, idle/running state, and manual run/config controls.
- Synchronization Locations let users define destination folder structures such as `Test File / File Name / Purpose Of Issue`, using vendor/RDrive metadata fields and custom folders.
- Synchronization Mappings let users select a provider folder/source tree, optionally include subfolders, filter by metadata/status such as `Purpose of Issue = RDrive-Drawing` and `Status = Fire Approved`, then sync matching documents into the configured RDrive folder structure.
- Editing an integration exposes operational controls and settings: active status, general settings, RDrive credentials, provider account credentials, health check, status history, form-event PDF options, mapping/export options, and pause/disable actions.

Confidentiality boundary:

> Do not share raw screenshots publicly or in a portfolio without redacting project/client names, IDs, usernames, roles, and any customer data. Use sanitized screenshots only, or describe the evidence verbally in interviews.

Interview-safe framing:

> The live product still shows the integration admin UI I worked on, including vendor selection, active integrations, Form Events, and Synchronization. That lines up with the product story: configurable push/pull workflows across external document platforms.

The system had two main product halves:

- Form Events: RDrive -> provider.
- Synchronization: provider -> RDrive.

Form Events provided a configurable UI where users could define automation rules, for example:

> When this form is updated and its status is `Draft`, send matching draft documents to Aconex, apply metadata extracted from the attached PDF, and upload it to the correct destination.

Synchronization synced files back from connected accounts into the user's RDrive project, organizing files hierarchically. This mattered because customers might already have thousands of documents in Aconex/Asite/Autodesk and needed them pulled into RDrive.

The two halves could be configured to work together. For example:

> Form Events could upload matching RDrive form packages to a provider folder such as `XYZ`; Synchronization could then be configured to pull that `XYZ` folder back into a selected RDrive project every few hours.

### Actual Event Flow

Form Events flow:

The original flow started around RDrive form events.

1. RDrive/Azure events sent a form-event history payload to your exposed endpoint.
2. The payload contained details like project URL/project identity and form code.
3. The API checked whether that project URL had a saved integration configured.
4. If an integration existed, the API checked whether that form code had mappings configured in the Vue UI.
5. If mappings existed, the system downloaded the PDF/export payload from an RDrive endpoint.
6. That payload contained a zip/files/metadata package.
7. The integration pipeline interpreted the mapping rules and uploaded the files/metadata to the configured destination.
8. Each destination had its own quirks: folder structure, permissions, metadata format, tokens/sessions, upload flow, and error handling.

Form-event configuration example:

> In the Form Event Mappings screen, a user selected an RDrive process template, such as a `Petty Cash Report`, then mapped each status to a provider-side target or action. That let the business say "when this form reaches this status, send it to the configured destination" without asking for a new code change every time.

Practical example:

> A field user creates or updates a safety form. If the form is signed off, DataBridge detects the event, matches the project/form/status against configured mappings, downloads the generated RDrive PDF/package, extracts the files and metadata, builds the target folder path from metadata such as drawing/location, then uploads the files and metadata into Aconex/Asite/Autodesk/Azure Blob according to that customer's rules.

Concrete Azure Blob example:

> In the Azure Blob integration, users could configure the folder structure for uploaded form-update documents. For example, uploads could be organised as `Processes / Process profile code / Process profile title / Client id`, with optional fields such as category title, controlled-by team, created-by user, project code, drawing title, external reference, location title, process template, and subcategory. This is a good simple example of the product being configuration-driven rather than hardcoded.

Integration setup example:

> Creating an integration was a guided admin flow. The user selected the vendor, supplied RDrive credentials, supplied the vendor credentials, then configured provider-specific options. That matters because the product had to handle both common integration concepts and vendor-specific setup differences.

Integration operations example:

> Editing an integration exposed the operational side of the system: active/paused state, RDrive credentials, provider account credentials, health checks, status history, form-event PDF download options, export templates, and pause/disable controls. This is useful to mention because it shows the product included ongoing administration and recovery, not only initial setup.

Synchronization flow:

1. A customer had an existing document library in a provider such as Aconex or Asite.
2. DataBridge searched/read the vendor documents and metadata.
3. Users configured synchronization locations in the UI.
4. The folder path could be dynamic, using vendor metadata fields.
5. DataBridge created the corresponding RDrive folder hierarchy.
6. It downloaded the provider files and uploaded them into the correct RDrive project folders.

Synchronization configuration example:

> Users could create a Synchronization Location such as `Test File / File Name / Purpose Of Issue`, using metadata tokens like document reference, revision, document title, status, and revision notes. Then they could create a Synchronization Mapping by selecting a provider folder/source tree, choosing whether to include subfolders, and applying filters such as `Purpose of Issue = RDrive-Drawing` and `Status = Fire Approved`. Matching documents were then pulled into RDrive and organised into the configured folder structure.

Practical example:

> Aconex might have thousands of files with metadata like category, location, drawing name, file type, subcontractor, and drawing location. DataBridge could use that metadata to create RDrive paths such as `/Sync Location/Category/{category}/Location/{location}/Sub Contractor/{name}/...`, then sync the files into that hierarchy. This let customers pull large document sets into RDrive already sorted the way they wanted.

Composed workflow example:

> A customer could configure Form Events to upload signed-off forms into vendor folder `XYZ`, then configure a scheduled Synchronization location to pull `XYZ` back into a chosen RDrive project every X hours. That made the system more like configurable workflow plumbing than a collection of one-off upload/download scripts.

Background operations example:

> The product also had scheduled operational jobs for Synchronization, Health Check, and Token Rotation. The UI showed last run, next run, current state, and controls to run or configure jobs. This matters because the integration was not only "call an API once"; it needed ongoing background processing and operational visibility.

### Main Learning Arc

The project started closer to an "Aconex uploader."

The main technical growth was refactoring that into a more generic integration pipeline:

- From one vendor-specific flow to multiple vendor strategies.
- From hardcoded behavior to configuration-driven mappings.
- From simple upload logic to reusable types for integrations, credentials, mappings, documents, metadata, folders, statuses, and results.
- From "if Aconex do X" branching toward vendor capabilities, strategies, and reusable pipeline stages.
- From request-bound thinking toward background work, health checks, retries, token/session handling, and UI-visible status.
- From first-time SPA/Vue/Vuetify delivery toward more deliberate frontend architecture later with Nuxt and Vue 3.

Personal technical arc:

> DataBridge was the first large system where I owned nearly everything end-to-end: backend, database, external API integrations, background jobs, admin UI, and the SPA. It was also my first time building a SPA with Vue/Vuetify, so I learned a lot while delivering real production functionality. Since then I have moved toward Nuxt/Vue 3 on the frontend while keeping .NET as my backend base, and I have become more deliberate about modular monolith structure, DDD-ish boundaries, and functional design where it helps without overengineering.

Code-backed detail from `F:\Projects\SnagR\RDrive-Aconex-Integrator`:

- ASP.NET Core API with Vue/Vuetify SPA.
- EF Core/SQL Server persistence.
- ASP.NET Identity.
- MediatR command/query style.
- Hangfire background processing.
- SignalR UI updates.
- Polly retry/circuit-breaker policies.
- Health-check, synchronization, token-rotation, and status-history rerun queues.
- Vendor capability model using generic conditions and behaviour groups.
- Document synchronization, form-event mapping, integration management, PowerBI/reporting, and task-management modules.

### Cleaner Interview Version

> I built a configurable integration platform for Snagr/RDrive called RDrive DataBridge. It had two main sides. Form Events pushed RDrive form packages and metadata out to platforms like Aconex, Azure Blob, Autodesk, and Asite when forms matched configured project/form/status mappings. Synchronization worked the other way: it pulled large existing vendor document libraries into RDrive projects and built RDrive folder hierarchies dynamically from vendor metadata. Over time I refactored it from an Aconex-specific uploader into a more generic pipeline with vendor strategies, configurable mappings, background processing, health checks, token/session handling, and user-visible sync status.

Variant with composition:

> The two sides could also be composed. For example, a workflow could push matching RDrive forms into a vendor folder, then a scheduled synchronization could pull that same folder back into a selected RDrive project every few hours.

### Business Impact Version

> The business problem was that construction/project teams had documents spread across RDrive and external platforms. RDrive held important form data, PDFs, files, and metadata, while systems like Aconex or Asite often already held thousands of drawings/photos/documents. Manual upload/download and folder organization was slow and error-prone. DataBridge let users configure repeatable rules to push RDrive form packages out when forms reached the right status, and to pull vendor document libraries back into RDrive with metadata-driven folder structures.

### Seniority Signals

- Multi-year ownership.
- Solo delivery from vague business request to working product.
- End-to-end full-stack ownership: backend, SPA, database, integrations, background jobs, and operations UI.
- Multiple third-party integrations.
- Evolving architecture as integrations were added.
- Configurable user-facing automation, not hardcoded scripts.
- Generic vendor capability modeling through conditions and behaviour groups.
- Bi-directional sync.
- Metadata extraction/mapping.
- Background processing and external API reliability concerns.
- Health checks, token/session rotation, retries, circuit breakers, and sync/result logging.
- SignalR-backed user-visible task status.
- Enterprise document-management context.
- Burnout/growth-path lesson: learned the risk of being isolated with no fallback/network.

### Likely Technical Topics To Explain

- Rule/configuration model.
- How users defined triggers and destinations.
- Exposed endpoint that received form-event history payloads.
- Project URL/integration lookup.
- Form code/status mapping lookup.
- RDrive PDF/export package download.
- Zip/files/metadata parsing.
- API integration differences between Aconex, Azure Blob, Autodesk, and Asite.
- Late provider-specific transfer behavior, such as Autodesk drawing downloads being chunked rather than simple file downloads.
- Folder-level permission checks when creating nested provider/RDrive structures.
- Metadata mapping and extraction from attached PDFs.
- Folder hierarchy creation from metadata such as drawing/location.
- Sync direction: RDrive to external systems and external systems back to RDrive.
- Synchronization locations and dynamic folder path configuration.
- Vendor metadata fields used as folder path variables.
- Bulk synchronization of thousands of provider documents into RDrive.
- Workflow composition between Form Events and scheduled Synchronization.
- Folder/project hierarchy mapping.
- Error handling, retries, logging, and recovery.
- Health checks and pause/disable behavior for unhealthy integrations.
- Background queues and overflow handling.
- Token/session refresh and rotation.
- SignalR status updates back to the UI.
- How architecture changed as integrations grew.
- What you would design differently now.

### Interview Questions This Story Can Answer

- Tell me about a complex project you owned.
- Tell me about a time requirements evolved over time.
- Tell me about integrating with third-party APIs.
- Tell me about dealing with ambiguity.
- Tell me about a technical design that changed as the product grew.
- Tell me about burnout or wanting a different growth path.
- Tell me about working independently.
- Tell me about a time you had to balance business requests with architecture.

## STAR Story: Evolving Integration Architecture

Situation:

Snagr/RDrive first needed a way to react to form events and upload matching RDrive form packages into Aconex. Over time, the same business need expanded to Azure Blob, Autodesk, and Asite.

Task:

Build a configurable system that let users define project/form/status mappings and vendor destinations instead of hardcoding every customer workflow.

Action:

Designed and implemented RDrive DataBridge over several years. The system received form-event history payloads, matched projects and form codes to configured integrations/mappings, downloaded RDrive PDF/export packages, extracted files/metadata, and uploaded them to external systems. As new platforms were added, refactored the architecture from Aconex-specific upload logic toward a generic pipeline with vendor strategies, reusable mapping types, metadata handling, folder creation, and background task processing.

Result:

RDrive could fit into customer environments that already depended on external document platforms. Users could automate repeatable document workflows, such as sending signed-off safety forms into the right vendor folder with the correct metadata, and also bulk-sync existing vendor libraries into RDrive already organized by metadata.

## STAR Story: Metadata-Driven Synchronization

Situation:

Some customers already had thousands of documents in systems like Aconex or Asite, with important metadata such as category, location, drawing name, file type, subcontractor, and drawing location.

Task:

Pull those documents into RDrive projects while preserving useful organization, instead of dumping thousands of files into a flat folder.

Action:

Built synchronization locations and dynamic folder-path configuration. DataBridge searched the provider, read document metadata, built RDrive folder paths from configured metadata tokens, created missing folders, downloaded the provider files, and uploaded them into the generated RDrive hierarchy.

Result:

Customers could sync large document libraries into RDrive with a click and have the files sorted into a structure that matched their project workflow.

## STAR Story: Composable Workflows

Situation:

Form Events and Synchronization solved opposite directions of the same integration problem: pushing RDrive events out to providers, and pulling provider folders/documents back into RDrive.

Task:

Allow customers to combine those capabilities without building a hardcoded custom workflow for every case.

Action:

Kept Form Events and Synchronization separately configurable through project/form/status mappings, provider destinations, synchronization locations, folder paths, and background schedules. That meant users could configure one flow to upload documents to a provider folder and another flow to periodically pull that folder back into RDrive.

Result:

Customers could create round-trip or chained workflows, such as uploading signed-off forms to vendor folder `XYZ` and scheduled-syncing that folder back into a chosen RDrive project every few hours.

## STAR Story: Hidden Integration Complexity

Situation:

RDrive DataBridge was mostly built solo, without regular code review or another engineer seeing the day-to-day complexity. From the outside, adding a new provider could look like "just implement the same interface for another integration."

Task:

Estimate and deliver new integrations honestly while dealing with the fact that each provider had different authentication, permissions, folder structures, metadata formats, upload/download behavior, API constraints, and failure modes.

Action:

Quoted based on previous integration experience rather than best-case assumptions. Pushed the architecture from one-off provider code toward reusable concepts such as vendor strategies, credentials, mappings, metadata, folder paths, task state, health checks, and sync logs. Each new integration still required architectural adjustment because it exposed new provider-specific behavior.

Concrete example:

During the Autodesk integration, a late discovery was that drawing downloads were chunked rather than a simple file download. That added about six extra implementation steps near the end. Folder creation also required checking permissions at each level, because folders could have different access rules. That kind of risk was hard to know at the beginning of an integration.

Result:

The system became more flexible over time, but the amount of invisible engineering work was not always obvious to stakeholders. The lesson was that honest estimates need visible decomposition: what is reusable, what is unknown, what must be tested with the provider, and what risks could extend the timeline.

Interview-safe phrasing:

> One lesson from DataBridge is that integration work can look simple from the outside because the UI might just say "add another provider." In practice, every provider had different auth, permissions, folders, metadata, transfer behavior, and failure behavior. For example, Autodesk introduced chunked drawing downloads and folder-level permission checks late in the implementation. I learned that I needed to make that complexity visible earlier by breaking estimates into reusable pipeline work, provider-specific discovery, implementation, testing, failure handling, and explicit risk buffer.

## STAR Story: Integration Reliability

Situation:

RDrive DataBridge depended on external systems with different APIs, credentials, folder models, token/session lifetimes, and failure behavior.

Task:

Make synchronization and form-event processing reliable enough that failures were visible, recoverable, and did not silently break customer workflows.

Action:

Added background processing with queues, health checks for RDrive/vendor connections, token/session refresh paths, retry/circuit-breaker policies for HTTP clients, sync/result logging, pause/disable behavior for unhealthy integrations, and SignalR status updates back to the UI.

Result:

The system became more operationally manageable: users could see sync progress/results, integrations could be paused when unhealthy, and transient vendor/API failures were handled more deliberately.

## STAR Story: Generic Vendor Options

Situation:

As more vendors were added, each platform needed different options: booleans, grouped choices, upload styles, folder behavior, synchronization filters, and vendor-specific metadata handling.

Task:

Avoid building a separate database schema and UI flow for every vendor-specific option.

Action:

Modeled vendor variation as generic `VendorConditions` and `VendorCustomBehaviourGroups`, with static backend definitions describing what each option meant for each vendor. The SPA received both vendor metadata and saved integration selections, then rendered reusable configuration flows.

Result:

The product could support vendor-specific behavior while keeping the persistence and UI patterns reusable as Aconex, Azure Blob, Autodesk, and Asite were added.

## Career Narrative

The honest story:

> I spent years working in a very independent setup, often receiving business-level requests and turning them into working systems mostly on my own. That gave me strong ownership and problem-solving ability, but it also meant I had little formal interview practice, limited team exposure, and almost no network. After DataBridge, I wanted a growth path that was not available there, and I also realized I did not want to depend on one informal work source again. That is why I am now building both job-market skill and my own SaaS/product optionality.

Shorter version:

> My background gave me unusually strong solo ownership, especially around integration-heavy products. The gap I am actively closing now is formal interview/team-market readiness: explaining decisions clearly, getting outside feedback, and building a stronger professional network.

Technical growth version:

> RDrive DataBridge was where I proved I could own a full-stack integration product end-to-end, including learning Vue/Vuetify while shipping. RefineBridge is the continuation of that same pattern with a more modern and deliberate stack: .NET, Nuxt/Vue 3, PostgreSQL, modular monolith structure, DDD-ish boundaries, background jobs, billing, and operational concerns.

## Major Experience 2: RefineBridge

Use RefineBridge as the modern SaaS/product story:

- .NET/Nuxt/Postgres SaaS.
- Nuxt/Vue 3 frontend after earlier Vue/Vuetify experience on DataBridge.
- More deliberate modular monolith and DDD-ish structure.
- Functional design influence where it reduces complexity, without forcing purity.
- Billing/subscriptions/webhooks.
- Credits/BYOK/provider-cost control.
- Background jobs.
- CRM/source integrations.
- Admin workflows.
- Auth/account boundaries.
- Deployment and operational concerns.

RefineBridge shows current technical stack and product ownership.

RDrive DataBridge shows long-term commercial integration-system experience.

Together they create a clear pattern:

> You repeatedly build configurable systems that connect external platforms, move data/documents reliably, and turn messy business workflows into software.
