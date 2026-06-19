# Diagnostic Interview Session 001

Status: Completed

- Date: 2026-06-19
- Project: RDrive DataBridge
- Mode: Project walkthrough with architecture and stakeholder follow-ups
- Target role: .NET backend/integrations
- Format: Live, one interview question at a time
- Burnout/growth-path consent: Not requested; no questions asked

## Protocol Note

Only prompts explicitly labelled as interview questions are scored. Factual clarifications and wording confirmations are not scored. An early contextual response was initially scored in error; that score was withdrawn during the session.

## Questions, Raw Answers, And Scores

### Q1: Explain RDrive DataBridge in about 30 seconds to a hiring manager

Raw answer:

> so rdrive was a tool that connected RDrive to different CRMs. it automated getting drawings / forms that were updated on site, which arrived to my 'databridge', which essentiallly checked and piped the drawing to the right destination, tagged with metadata, organised however they configured, e.g sorted in a hierarchitcal folder based on the meta data from the downloaded form. That was one side of it (form events), and another later role was synchronication which sent data from the CRM > Rdrive Project, our UI allowed them to again make use of the mata data on the files, and build a hierarchical folder structure within the RDrive internal documents to sort htem. e.g /Drawings/Locations/DrawingName.jpg

- Score: 2/4
- Strongest part: Distinguished Form Events from Synchronization and explained metadata-driven folder organization.
- Weakest part: Too long for 30 seconds; used inaccurate "CRM" terminology; business result and tradeoff were unclear.
- Missing evidence exposed: The manual workflow replaced by DataBridge.

### Q2: Why make Form Events configurable through mappings instead of sending every event?

Raw answer:

> well across a project, there can be hundreds if not thousands of documents being sent over the wire, and not all of them want backing up, e.g every draft form created, or they just werent interested in tracking some forms over others. They needed this configurable otherwise for example, everytime 'john the builder' opened a drawing and clicked saved this would be backed up to storage. They needed control on what projects, what drawings, and what specific events in those drawings would be backed up. E.g 'import all that close and failed', or 'Import Safety form 1 when its Open'.

- Score: 3/4
- Strongest part: Connected event volume and user intent directly to the mapping design.
- Weakest part: Tradeoff and operational result were implicit; terminology moved between forms and drawings.
- Confirmed clarification: Mappings could be status-wide or specific to a form/version and status.

### Q3: What made Autodesk harder than expected, and how was that complexity communicated?

Raw answer:

> autodesk was at the time the 4th integration that I did. One key thing was, within autodesk, no folders were treated the same. Each folder could have its own users allowed into it, its own permissions, meaning there were far more hurdles to jump through. This made simple things such as creating sub folders, or uploading files, more challenging at times compared to other integrations. Where we had to check the user had permissions before any action could be made.

- Score: 2/4
- Strongest part: Concrete folder-level permission constraint.
- Weakest part: Answered the technical half only; no communication, estimate impact, tradeoff, or result.

### Q3 Follow-Up A: What was communicated about the changed scope or estimate, and what options were offered?

Raw answer:

> well stakeholders I was just working with one manager. Over the years we had build a trust together, and given his own busy schedule, would just let me get on with things and let him know when they were done. There were not really options on the table. They did offer me to be able to do 2 further integrations, and asked how long they would take. I gave my best estimates, and knowing that the integrations in questions would involve the external data providers own internal folder structure, I gave an honest answer that was longer than they thought, as in their mind I was just 'filling out the interfaces for a new intergration' which was quite an over simplification of the system

- Score: 2/4
- Strongest part: Corrected the premise instead of inventing a formal negotiation or scope options.
- Weakest part: Rambling structure and no concrete estimate decomposition.

### Q3 Follow-Up B: How was the hidden work behind the estimate explained?

Raw answer:

> I backed this up based on experience. I said to him, Im trying to build this system so that each next integration is easier. But I said the same thing before we did Asite (the 3rd integration) and that one took longer than expected, as it was the first where we're having to make/manage folders within the external provider. All these little things add up and are unknown untill you start thigns. How do they handle auth / permissions / files / folders etc, they all have their own little quirks which you cant know untill you start. My line response was, we said the same at the start of the Asite integration, and that one took 6 months. That was 'just filling out the contracts for a new integration'. So I was never just 'doing the integration' I was always trying to evolve the whole architecture together.

- Score: 3/4
- Strongest part: Used prior provider experience to make hidden discovery and architecture work visible.
- Weakest part: Tone could become defensive; exact Asite/Autodesk duration is uncertain; conversation result was not stated.
- Claim boundary: Use "several months" unless the provider-specific timeline is verified.

### Q4: Working mostly alone, how was the risk of evolving DataBridge without breaking existing providers managed?

Raw answer:

> just with careful planning, and thankfully the majority of my decisions from early on were in keeping things as generic overall as possible, so often things did just involved creating a new branch in logic. I was careful to never tie any specific functinoality to any specific provider, and made things as modular as possible at the domain level.

- Score: 2/4
- Strongest part: Clear intent to keep shared domain concepts provider-neutral and provider rules modular.
- Weakest part: Risk controls were asserted rather than demonstrated; wording was too absolute.
- Confirmed clarification: Shared DataBridge concepts remained generic while providers supplied concrete rules through capability and permission metadata.

### Q4 Follow-Up: How were existing integrations verified after shared architecture changed?

Raw answer:

> well database backups would confirm migrations worked successfully so any tables were updated and tested working locally first, and then on dev envrionment, and then in production. This was also confirmed through manual testing. Testing each previous integration could still recieve form events / synchronications correctly locally, on dev. Once everything seemed good in local / dev, the manager would update main.

- Score: 3/4
- Strongest part: Concrete local-to-development progression and manual regression checks across existing providers.
- Weakest part: Backups were described as validation rather than recovery; automated tests, deployment details, and production monitoring were not covered.
- Confirmed correction: A copy of the live database was sometimes used locally to test migrations. Only Azure Blob Storage was actively used by a client at that time, reducing live regression exposure for other providers.

## Confirmed Improved Answer

Problem:
Teams manually uploaded documents to external platforms and entered metadata one file at a time.

Constraint:
Projects generated many form events, but only configured project, form, and status combinations should trigger transfers, and every provider behaved differently.

Decision:
I built DataBridge as a configurable two-way integration platform. Form Events matched incoming events against user mappings, fetched the latest document package, and sent it through provider-specific implementations. Synchronization handled the reverse flow into metadata-driven RDrive folders.

Tradeoff:
A generic pipeline required more architectural work and still needed provider-specific discovery.

Result:
It automated selected document transfers, metadata entry, and folder organization while keeping users in control of what moved.

Richard confirmed this answer as accurate on 2026-06-19.

## Top Weak Spots

- Concision: strong technical context expands beyond the requested answer length.
- Structure: constraints and implementation details appear before the problem and result are established.
- Terminology: use "external document platforms" rather than "CRMs"; distinguish forms, generated document packages, and drawings.
- Stakeholder framing: describe the real one-manager trust relationship instead of inventing formal scope options.
- Evidence: pair architectural intent with concrete migration, environment, and regression checks.
- Precision: avoid absolutes such as "never" and uncertain exact provider timelines.

## Strengths Observed

- Strong recall of event mapping, metadata, folder, permission, and provider behavior.
- Corrected interviewer assumptions instead of accepting an inaccurate story.
- Clearly understood why reusable architecture did not eliminate provider-specific discovery.
- Maintained customer, project, account, and credential privacy.

## Claim And Privacy Boundaries

- No customer names, project IDs, live URLs, credentials, screenshots, or tenant data recorded.
- Compensation details discussed during clarification are intentionally excluded.
- Do not imply that an estimate or compensation discussion caused a proposed integration not to proceed.
- Exact Asite versus Autodesk duration remains uncertain; use "several months" until verified.
- Do not generalize active client usage beyond the confirmed Azure Blob Storage context.
- Exact internal type names should remain private; use capability/permission metadata publicly.

## Next Practice

1. Deliver the confirmed improved DataBridge answer aloud in 30-45 seconds without notes.
2. Re-answer the Autodesk/estimation question in 60 seconds using one constraint, one prior example, and one result.
3. Prepare a 60-second solo-risk answer covering provider-neutral design, local migration testing against a database copy, dev deployment, manual provider regressions, and recovery.
4. Clarify what automated tests, production monitoring, rollback, and deployment controls existed.

## Open Questions

- Was the approximately six-month implementation Asite, Autodesk, or both?
- What automated tests existed for shared pipeline and provider behavior?
- What exactly did "the manager would update main" involve: merge, deployment, or both?
- What production monitoring or rollback steps followed deployment?
- Is "backup" the correct business term, or should public answers consistently use transfer/archive?

## Issue #12 Acceptance Criteria

- Complete: One live diagnostic session completed with Richard.
- Complete: Session note includes date, mode, project, questions, raw answers, scores, and notes.
- Complete: One confirmed answer improved using Problem -> Constraint -> Decision -> Tradeoff -> Result.
- Complete: Improved answer copied into `rdrive-databridge-case-study.md`.
- Complete: Top weak spots added to `weak-spot-tracker.md`.
- Complete: Next practice actions listed.
- Complete: Privacy and claim boundaries documented and enforced.
