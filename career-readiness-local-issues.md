# Career Readiness Local Issues

Current as of 2026-06-01.

Parent PRD: `career-readiness-system-prd.md`

Status: proposed local backlog. Not published to any tracker.

## Proposed Breakdown

| ID | Title | Type | Blocked by | User stories covered |
| --- | --- | --- | --- | --- |
| CRI-001 | Define target role and positioning v1 | HITL | None | 1, 3, 4, 9, 86 |
| CRI-002 | Build master career inventory and evidence boundaries | AFK | CRI-001 | 9, 10, 23-26, 33, 35 |
| CRI-003 | Draft sendable CV v1 | HITL | CRI-001, CRI-002 | 5, 6, 10, 11 |
| CRI-004 | Draft LinkedIn profile v1 | HITL | CRI-001, CRI-002 | 7, 8, 9, 11 |
| CRI-005 | Create target-role matrix v1 | HITL | CRI-001 | 1, 2, 3, 4 |
| CRI-006 | Create application tracker and outreach scripts | AFK | CRI-003, CRI-004, CRI-005 | 12-20 |
| CRI-007 | Package RDrive DataBridge case study v1 | AFK | CRI-002 | 23, 24, 30-33, 38, 39 |
| CRI-008 | Package RefineBridge case study v1 | AFK | CRI-002 | 25, 26, 30, 31, 36, 81 |
| CRI-009 | Build behavioral and stakeholder story bank v1 | HITL | CRI-007, CRI-008 | 27-40 |
| CRI-010 | Create Codex interviewer workflow v1 | AFK | CRI-007, CRI-008 | 41-60 |
| CRI-011 | Run first diagnostic interview session | HITL | CRI-009, CRI-010 | 40, 43-56, 63, 70 |
| CRI-012 | Create weak-spot tracker and practice log | AFK | CRI-011 | 61-66, 70-73, 87-90 |
| CRI-013 | Create practical technical drill pack v1 | AFK | CRI-005, CRI-012 | 75-77 |
| CRI-014 | Create system-design practice pack v1 | AFK | CRI-007, CRI-008, CRI-012 | 78, 80 |
| CRI-015 | Create reliability and security interview pack v1 | AFK | CRI-007, CRI-008, CRI-012 | 79, 80 |
| CRI-016 | Create feedback and mentorship workflow v1 | HITL | CRI-003, CRI-004, CRI-007, CRI-008 | 16, 40, 93 |
| CRI-017 | Create first 30-day operating plan | AFK | CRI-005, CRI-012, CRI-016 | 17, 65-74, 95 |
| CRI-018 | Run first small market test | HITL | CRI-003, CRI-004, CRI-005, CRI-006, CRI-017 | 17-20, 94 |
| CRI-019 | Create RefineBridge customer-discovery track | HITL | CRI-008, CRI-017 | 81-86 |
| CRI-020 | Decide whether to build Notion/dashboard layer | HITL | CRI-012, CRI-017, CRI-018 | 87-96 |

## CRI-001: Define target role and positioning v1

Type: HITL

## Parent

`career-readiness-system-prd.md`

## What to build

Create a first-pass positioning document that defines the target role family, preferred market, and core professional story. This should turn the current broad identity into something recruiters and hiring managers can understand quickly.

The output should answer:

- What roles are being targeted first?
- What roles are delayed or treated as reach roles?
- What is the short positioning statement?
- How should Snagr/RDrive be framed?
- How should RefineBridge be framed?
- What should not be overclaimed?

## Acceptance criteria

- [ ] A local positioning artifact exists.
- [ ] It includes 2-3 target role titles.
- [ ] It includes one primary positioning statement.
- [ ] It includes a safe Snagr/RDrive employment framing.
- [ ] It includes a RefineBridge positioning paragraph.
- [ ] It explicitly avoids unsupported claims around SharePoint, 4Projects, sales, marketing, and product adoption.
- [ ] It has a short list of open questions for human review.

## Blocked by

None - can start immediately.

## CRI-002: Build master career inventory and evidence boundaries

Type: AFK

## Parent

`career-readiness-system-prd.md`

## What to build

Create a structured career inventory from the existing notes. It should separate confirmed evidence, likely claims, uncertain claims, and things that need user confirmation.

This becomes the source material for CV, LinkedIn, case studies, and interview answers.

## Acceptance criteria

- [ ] A master inventory artifact exists.
- [ ] It lists major projects and responsibilities.
- [ ] It separates RDrive DataBridge, RefineBridge, legacy Snagr/VB.NET work, and other work.
- [ ] It marks evidence-backed claims separately from uncertain claims.
- [ ] It includes safe public/private boundaries for screenshots, client names, and live product access.
- [ ] It includes a reusable "do not claim unless confirmed" section.

## Blocked by

- CRI-001

## CRI-003: Draft sendable CV v1

Type: HITL

## Parent

`career-readiness-system-prd.md`

## What to build

Create a first CV draft that is good enough to review and iterate. It does not need to be perfect, but it should be materially sendable after basic personal details are filled in.

The CV should emphasize practical .NET/full-stack/SaaS/integration ownership, not tutorial work or vague tool lists.

## Acceptance criteria

- [ ] `cv-draft.md` exists.
- [ ] It has a clear headline/title.
- [ ] It has a concise professional summary.
- [ ] It includes a skills section focused on .NET, Vue/Nuxt, integrations, background jobs, SaaS, databases, and reliability.
- [ ] It includes Snagr/RDrive experience with safe employment framing.
- [ ] It includes RDrive DataBridge bullets using business-impact language.
- [ ] It includes RefineBridge bullets using modern SaaS/product language.
- [ ] It includes placeholders for contact/location/link details that need user confirmation.
- [ ] It avoids unsupported claims.

## Blocked by

- CRI-001
- CRI-002

## CRI-004: Draft LinkedIn profile v1

Type: HITL

## Parent

`career-readiness-system-prd.md`

## What to build

Create LinkedIn profile copy that can be pasted into LinkedIn after review. It should make the same positioning as the CV visible in recruiter-friendly language.

## Acceptance criteria

- [ ] `linkedin-profile-draft.md` exists.
- [ ] It includes 5-10 headline options.
- [ ] It includes an About section.
- [ ] It includes Snagr/RDrive experience copy.
- [ ] It includes RefineBridge/project copy.
- [ ] It includes a featured/projects section suggestion.
- [ ] It includes a keyword list aligned with target roles.
- [ ] It includes notes on what not to mention publicly.

## Blocked by

- CRI-001
- CRI-002

## CRI-005: Create target-role matrix v1

Type: HITL

## Parent

`career-readiness-system-prd.md`

## What to build

Create a target-role matrix using real job ads. The goal is to test whether the positioning fits the market and identify repeated requirements.

The matrix should not become a giant job hunt yet. It is a calibration tool first.

## Acceptance criteria

- [ ] `target-role-matrix.md` exists.
- [ ] It includes at least 15 real target roles for v1.
- [ ] Each role includes title, company, location/timezone, remote policy, stack, seniority, fit notes, and link.
- [ ] Repeated requirements are summarized.
- [ ] Requirements are grouped as "must have", "nice to have", and "ignore for now".
- [ ] Role families are ranked by fit.
- [ ] Unknowns are listed for later research.

## Blocked by

- CRI-001

## CRI-006: Create application tracker and outreach scripts

Type: AFK

## Parent

`career-readiness-system-prd.md`

## What to build

Create a simple local hiring funnel tracker and message scripts for recruiters, warm contacts, mentor requests, and follow-ups.

This should make the process operational before applications start.

## Acceptance criteria

- [ ] `application-tracker.md` exists.
- [ ] It includes fields for role, company, source, CV version, contact, date applied, status, response, interview stage, and follow-up.
- [ ] `outreach-scripts.md` exists.
- [ ] It includes recruiter message, warm intro request, hiring manager note, mentor feedback request, and follow-up templates.
- [ ] `recruiter-screen-script.md` exists.
- [ ] It covers target role, location/timezone, availability, salary/rate placeholder, work history framing, and project summary.
- [ ] Scripts are concise and do not sound desperate.

## Blocked by

- CRI-003
- CRI-004
- CRI-005

## CRI-007: Package RDrive DataBridge case study v1

Type: AFK

## Parent

`career-readiness-system-prd.md`

## What to build

Create a polished private case study for RDrive DataBridge that can feed CV bullets, LinkedIn copy, interview stories, and system-design practice.

It should explain the product simply, then show enough technical depth to defend the work.

## Acceptance criteria

- [ ] `rdrive-databridge-case-study.md` exists.
- [ ] It includes a 30-second explanation.
- [ ] It includes a 2-minute explanation.
- [ ] It explains Form Events.
- [ ] It explains Synchronization.
- [ ] It explains how both sides could be composed.
- [ ] It includes the main architecture evolution from Aconex uploader to configurable integration platform.
- [ ] It includes business impact and stakeholder value.
- [ ] It includes technical topics likely to come up in interviews.
- [ ] It includes confidentiality and claim-boundary notes.

## Blocked by

- CRI-002

## CRI-008: Package RefineBridge case study v1

Type: AFK

## Parent

`career-readiness-system-prd.md`

## What to build

Create a polished private case study for RefineBridge as the modern .NET/Nuxt/SaaS product example.

It should connect implementation choices to product value and interview-relevant topics.

## Acceptance criteria

- [ ] `refinebridge-case-study.md` exists.
- [ ] It includes a 30-second explanation.
- [ ] It includes a 2-minute explanation.
- [ ] It covers target user, problem, product workflow, and business value.
- [ ] It covers backend, frontend, database, jobs, integrations, billing/webhooks, auth, and admin concerns where known.
- [ ] It includes a "what changed from earlier product direction" section.
- [ ] It includes a "what I would improve next" section.
- [ ] It marks areas needing repo inspection or user confirmation.

## Blocked by

- CRI-002

## CRI-009: Build behavioral and stakeholder story bank v1

Type: HITL

## Parent

`career-readiness-system-prd.md`

## What to build

Create a story bank for behavioral, stakeholder, product, estimation, and ownership questions. Each story should use Problem -> Constraint -> Decision -> Tradeoff -> Result by default.

## Acceptance criteria

- [ ] `behavioral-story-bank.md` exists.
- [ ] It includes at least 8 reusable stories.
- [ ] It includes stories for ambiguity, estimation, refactoring, solo ownership, learning under pressure, product underuse, changed direction, and burnout/growth path.
- [ ] Each story has a short version and a fuller version.
- [ ] Each story lists interview questions it can answer.
- [ ] Weak or missing result sections are marked for follow-up.

## Blocked by

- CRI-007
- CRI-008

## CRI-010: Create Codex interviewer workflow v1

Type: AFK

## Parent

`career-readiness-system-prd.md`

## What to build

Turn the existing Codex interviewer concept into a usable local workflow with prompts, session types, output templates, and a first question bank.

## Acceptance criteria

- [ ] `codex-interviewer-workflow.md` exists or the existing workflow file is updated.
- [ ] It includes session modes for project walkthrough, architecture grill, behavioral, debugging, and stakeholder interviews.
- [ ] It includes copy/paste prompts.
- [ ] It includes session output format.
- [ ] It includes scoring rubric.
- [ ] It includes first-session order.
- [ ] It includes rules for when Codex can inspect local repos.
- [ ] It includes privacy boundaries for RDrive material.

## Blocked by

- CRI-007
- CRI-008

## CRI-011: Run first diagnostic interview session

Type: HITL

## Parent

`career-readiness-system-prd.md`

## What to build

Run the first live practice session using Codex as interviewer. The session should be short and should produce a weak-spot report plus one improved answer.

## Acceptance criteria

- [ ] One interview session is completed.
- [ ] The session has a date, mode, project, questions, and scores.
- [ ] At least one answer is improved.
- [ ] Top weak spots are listed.
- [ ] Next practice actions are listed.
- [ ] Any useful improved answer is copied into the appropriate story/case-study file.

## Blocked by

- CRI-009
- CRI-010

## CRI-012: Create weak-spot tracker and practice log

Type: AFK

## Parent

`career-readiness-system-prd.md`

## What to build

Create the manual tracking layer for weak spots, practice minutes, artifacts, confidence scores, and weekly reviews.

## Acceptance criteria

- [ ] `weak-spot-tracker.md` exists.
- [ ] It includes the 0-4 score definitions.
- [ ] It includes priority factors: market demand, anxiety, evidence, score, and blocking impact.
- [ ] It includes initial weak spots from known context and first diagnostic session.
- [ ] `practice-log.md` exists.
- [ ] Practice log entries include date, tree, subskill, minutes, activity, resource, artifact, confidence before/after, and next action.
- [ ] `weekly-review-template.md` exists.
- [ ] The system discourages logging passive study without output.

## Blocked by

- CRI-011

## CRI-013: Create practical technical drill pack v1

Type: AFK

## Parent

`career-readiness-system-prd.md`

## What to build

Create a practical interview drill pack for .NET/full-stack roles. It should include light DSA, practical .NET tasks, TypeScript/Vue tasks, debugging prompts, and take-home style slices.

## Acceptance criteria

- [ ] `practical-technical-drills.md` exists.
- [ ] It includes 30-50 light DSA topics/problems at pattern level.
- [ ] It includes at least 12 practical .NET/TypeScript drills.
- [ ] It includes at least 5 debugging drills.
- [ ] Each drill has expected output and scoring notes.
- [ ] The first 4 drills are marked for the diagnostic sprint.
- [ ] Drills are mapped to target-role requirements from the role matrix.

## Blocked by

- CRI-005
- CRI-012

## CRI-014: Create system-design practice pack v1

Type: AFK

## Parent

`career-readiness-system-prd.md`

## What to build

Create a system-design practice pack based on RDrive DataBridge and RefineBridge. The pack should focus on explaining real systems, not memorizing generic diagrams.

## Acceptance criteria

- [ ] `system-design-practice-pack.md` exists.
- [ ] It includes a walkthrough outline for RDrive DataBridge.
- [ ] It includes a walkthrough outline for RefineBridge.
- [ ] It includes prompts for requirements, constraints, data model, async work, retries, idempotency, security, observability, and failure modes.
- [ ] It includes at least 10 ADR prompts.
- [ ] It includes a 45-minute mock system-design session structure.
- [ ] It marks missing diagrams or repo-inspection tasks.

## Blocked by

- CRI-007
- CRI-008
- CRI-012

## CRI-015: Create reliability and security interview pack v1

Type: AFK

## Parent

`career-readiness-system-prd.md`

## What to build

Create runbooks, threat-model prompts, and reliability/security interview questions for the main systems.

## Acceptance criteria

- [ ] `reliability-security-interview-pack.md` exists.
- [ ] It includes at least 3 debugging/runbook scenarios.
- [ ] It includes webhook/billing failure prompts.
- [ ] It includes external API failure prompts.
- [ ] It includes auth/account/tenant boundary prompts.
- [ ] It includes secrets/API key/BYOK prompts.
- [ ] It includes logging/privacy prompts.
- [ ] It includes answer structure for debugging questions.

## Blocked by

- CRI-007
- CRI-008
- CRI-012

## CRI-016: Create feedback and mentorship workflow v1

Type: HITL

## Parent

`career-readiness-system-prd.md`

## What to build

Create a workflow for getting external feedback without asking vague questions. The output should include who to ask, what to ask, and how to convert feedback into revisions.

## Acceptance criteria

- [ ] `mentor-feedback-workflow.md` exists.
- [ ] It includes target reviewer types: senior engineer, hiring manager/recruiter, founder/product person, mock interviewer.
- [ ] It includes specific request templates.
- [ ] It includes a feedback log template.
- [ ] It includes first 3 recommended feedback asks.
- [ ] It defines how feedback updates CV, LinkedIn, stories, weak spots, and practice plan.
- [ ] It avoids vague "can you mentor me?" asks.

## Blocked by

- CRI-003
- CRI-004
- CRI-007
- CRI-008

## CRI-017: Create first 30-day operating plan

Type: AFK

## Parent

`career-readiness-system-prd.md`

## What to build

Create a practical 30-day plan that combines hiring package work, interview practice, technical drills, feedback, and light market testing.

## Acceptance criteria

- [ ] `30-day-operating-plan.md` exists.
- [ ] It has weekly goals for 4 weeks.
- [ ] It has a default weekly time split.
- [ ] It includes daily/weekly minimum viable actions.
- [ ] It includes diagnostic sprint tasks.
- [ ] It includes review checkpoints.
- [ ] It identifies the first market-test batch.
- [ ] It explicitly protects time from dashboard overbuilding.

## Blocked by

- CRI-005
- CRI-012
- CRI-016

## CRI-018: Run first small market test

Type: HITL

## Parent

`career-readiness-system-prd.md`

## What to build

Run a small real-world hiring funnel test with the current CV, LinkedIn, role matrix, tracker, and scripts. The goal is feedback, not perfect outcomes.

## Acceptance criteria

- [ ] 5-10 suitable roles are selected from the target-role matrix.
- [ ] CV version used is recorded.
- [ ] Applications or outreach messages are sent.
- [ ] Every action is logged in the application tracker.
- [ ] Response/no-response data is reviewed after a defined period.
- [ ] At least one material change is made based on market response.
- [ ] Weak spots discovered from the market test are added to the tracker.

## Blocked by

- CRI-003
- CRI-004
- CRI-005
- CRI-006
- CRI-017

## CRI-019: Create RefineBridge customer-discovery track

Type: HITL

## Parent

`career-readiness-system-prd.md`

## What to build

Create a parallel customer-discovery track for RefineBridge so that job readiness does not completely replace product optionality.

The goal is to keep product decisions tied to real user conversations, not just building.

## Acceptance criteria

- [ ] `refinebridge-customer-discovery-track.md` exists.
- [ ] It includes target customer hypotheses.
- [ ] It includes discovery questions.
- [ ] It includes objection log template.
- [ ] It includes offer/version notes.
- [ ] It includes 10-20 conversation targets or target categories.
- [ ] It includes a decision rule for job focus vs product focus vs hybrid.
- [ ] It avoids making large product bets before discovery.

## Blocked by

- CRI-008
- CRI-017

## CRI-020: Decide whether to build Notion/dashboard layer

Type: HITL

## Parent

`career-readiness-system-prd.md`

## What to build

After the local manual workflow has been used, decide whether a Notion dashboard, local docs, or lightweight app would make the system easier to run.

This is a decision issue, not a build issue.

## Acceptance criteria

- [ ] Manual workflow has been used for at least 2 weeks.
- [ ] Pain points are listed.
- [ ] Dashboard benefits are compared against maintenance cost.
- [ ] Decision is recorded: keep Markdown, build Notion, build lightweight local app, or defer.
- [ ] If dashboard is approved, a new PRD or issue set is created for it.
- [ ] If deferred, the reason and revisit date are recorded.

## Blocked by

- CRI-012
- CRI-017
- CRI-018

