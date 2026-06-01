# Career Readiness Orchestrator Handoff

Current as of 2026-06-01.

Purpose: preserve the current goal, context, issue workflow, and review protocol so a fresh Codex session can continue without re-discovering the whole conversation.

This file is a handoff, not the source of truth for every detail. Use the referenced artifacts for the full PRD, backlog, story bank, resources, and learning plans.

## Current Goal

The user wants a practical, local-first system for becoming employable/interview-ready while preserving long-term optionality through RefineBridge, consulting/freelance skill, and future SaaS income.

The real goal is not "get any job" or "ignore jobs and build SaaS." The real goal is resilience:

- Get interview-visible.
- Get interview-capable.
- Explain existing work clearly.
- Build a professional network and feedback loop.
- Keep RefineBridge as a long-term asset.
- Avoid dependence on one informal company/client/income source again.

## User Context

The user is a .NET/full-stack developer with real solo ownership experience but little formal interview exposure.

Important background:

- Worked for Snagr/RDrive over a long period in a non-standard independent/family-friend arrangement.
- Worked from England and Thailand.
- Maintained legacy VB.NET frontend/backend code before RDrive DataBridge.
- Built/owned RDrive DataBridge over roughly 3-4 years.
- RDrive DataBridge connected RDrive with Aconex, Azure Blob Storage, Autodesk, and Asite.
- SharePoint and 4Projects were discussed/requested as future integrations; do not claim they were implemented unless evidence later confirms it.
- RDrive DataBridge had two main halves:
  - Form Events: RDrive form/status events pushed files/metadata to external providers.
  - Synchronization: external provider document libraries were pulled into RDrive with metadata-driven folder structures.
- The user can still access the live product and has screenshots, but raw screenshots should not be shared publicly without redaction.
- The user has a current product/project, RefineBridge, built with a more modern .NET/Nuxt/Vue 3/Postgres/SaaS style.
- RefineBridge should be used as the modern stack/product case study.
- RDrive DataBridge should be used as the long-term commercial integration-platform case study.

Key personal/career context:

- User has never done a formal job interview.
- User has no current CV.
- LinkedIn needs updating.
- User has very little network and has mostly worked alone.
- User wants stability but does not want to depend fully on one company again.
- User sees SaaS as long-term optionality, not a reason to avoid job readiness.

## Main Strategy

Proceed outside-in:

1. Make the user interview-visible.
2. Make the user able to explain real work.
3. Diagnose weak spots with realistic practice.
4. Improve skills through artifacts and feedback.
5. Only build a Notion/dashboard layer after the manual workflow proves useful.

Do not start with a polished dashboard. Do not start with heavy LeetCode. Do not start by buying expensive coaching.

## Source Artifacts

Primary planning artifacts:

- `career-readiness-system-prd.md` - central PRD for the local career readiness system.
- `career-readiness-local-issues.md` - local issue backlog, CRI-001 to CRI-020.
- `modern-dotnet-interview-readiness-map.md` - skill map for current .NET/full-stack interview readiness.
- `learning-system-plan.md` - weak-spot scoring, practice loop, future dashboard plan.
- `interview-and-options-roadmap.md` - broader 6-month optionality roadmap.
- `resource-map.md` - resource categories, free/paid resources, and resource-use rules.
- `hayk-style-curriculum.md` - reverse-engineered senior-dev/interview curriculum inspired by Hayk-style public material.
- `codex-interviewer-system.md` - design for repo-aware interview practice.

Experience artifacts:

- `experience-story-bank.md` - main RDrive DataBridge and RefineBridge story material.
- `rdrive-databridge-explanation-cheatsheet.md` - short explanations for RDrive DataBridge.
- `rdrive-databridge-code-evidence.md` - code-backed RDrive DataBridge evidence from `F:\Projects\SnagR\RDrive-Aconex-Integrator`.
- `stakeholder-communication-lessons.md` - estimation and invisible-integration-complexity lessons.

Raw conversation notes:

- `convo1.txt` - prior discussion on BGO/CodeToCEO, sales/consulting resources, speaking/networking confidence, interview prep, optionality, SaaS vs job.
- `convo2.txt` - mentorship/community options, Hayk Simonyan research, and senior-dev/job-impact curriculum extraction.

## Current Backlog

The active local backlog is in `career-readiness-local-issues.md`.

Current order:

1. CRI-001 - Define target role and positioning v1.
2. CRI-002 - Build master career inventory and evidence boundaries.
3. CRI-003 - Draft sendable CV v1.
4. CRI-004 - Draft LinkedIn profile v1.
5. CRI-005 - Create target-role matrix v1.
6. CRI-006 - Create application tracker and outreach scripts.
7. CRI-007 - Package RDrive DataBridge case study v1.
8. CRI-008 - Package RefineBridge case study v1.
9. CRI-009 - Build behavioral and stakeholder story bank v1.
10. CRI-010 - Create Codex interviewer workflow v1.
11. CRI-011 - Run first diagnostic interview session.
12. CRI-012 - Create weak-spot tracker and practice log.
13. CRI-013 - Create practical technical drill pack v1.
14. CRI-014 - Create system-design practice pack v1.
15. CRI-015 - Create reliability and security interview pack v1.
16. CRI-016 - Create feedback and mentorship workflow v1.
17. CRI-017 - Create first 30-day operating plan.
18. CRI-018 - Run first small market test.
19. CRI-019 - Create RefineBridge customer-discovery track.
20. CRI-020 - Decide whether to build Notion/dashboard layer.

The next issue is CRI-001 unless the user explicitly chooses another.

## Orchestrator Workflow

The user wants this conversation to act as the orchestrator.

When the user asks for "the next issue":

1. Read `career-readiness-local-issues.md`.
2. Identify the next unsatisfied issue in dependency order.
3. Produce a prompt for a fresh Codex conversation.
4. Before the prompt, include recommended model and reasoning effort.
5. Do not merely paste the local issue text.
6. Add the context, guardrails, expected output, relevant files, and verification requirements the issue needs.
7. Decide whether the issue is an execution task, an exploration task, or a mixed task.
8. If the issue needs user judgment, role research, market research, personal facts, or strategic clarification, the worker prompt must explicitly say to research/explore with the user first rather than forcing a finished artifact immediately.
9. Include final response requirements for the worker agent:
   - concise summary
   - bullet points
   - files changed
   - verification/tests run
   - manual verification instructions for the human
10. Make clear that tests/automated checks should prove the bulk of the work where possible.

Not every issue is "build this now." Many issues are likely to require discovery first. The orchestrator should choose the right mode:

- Exploration-first: clarify goals, research current market/resources, compare options, ask focused questions, then propose the artifact shape.
- Build-first: enough context exists; create/update the local artifact directly.
- Mixed: produce a draft with placeholders, then list questions that need human input.

When in doubt, prefer a short exploration loop before producing durable career material. This is especially true for target roles, CV/LinkedIn positioning, compensation, location/timezone strategy, mentor choices, Notion/dashboard design, and anything using current market information.

When the user returns and says "review please":

1. Inspect the current working diff.
2. Compare the diff to the relevant issue and to the prompt that was given.
3. Check acceptance criteria.
4. Check guardrails, especially claim boundaries, privacy, overbuilding, and unsupported assertions.
5. Run reasonable validation commands for the type of artifact.
6. If the work misses the brief, provide a course-correction prompt for the worker agent.
7. If the work is good, reply exactly enough for the user to pass back:

```text
issue CRI-XXX is satisfied, ready to commit and close the issue
```

If issues are later migrated to GitHub, replace `CRI-XXX` with the GitHub issue number while preserving the same review logic.

## Completion Ownership

The orchestrator thread owns completion decisions.

Worker agents may:

- edit local artifacts
- report what they changed
- say what they believe is complete
- list verification and manual checks
- flag open questions

Worker agents should not:

- mark local issues as complete
- edit the backlog status to "done"
- declare an issue closed as the final source of truth
- commit changes
- publish anything externally

The user should return to this orchestrator thread with `review please`. The orchestrator reviews the diff against the issue and either:

- approves with `issue CRI-XXX is satisfied, ready to commit and close the issue`
- or provides a course-correction prompt for the worker agent

Only after orchestrator approval should the user treat the issue as complete.

## Worker Prompt Requirements

Every worker prompt should include:

- Recommended model and reasoning effort before the copy/paste prompt.
- Issue ID and title.
- Parent PRD/backlog paths.
- Relevant context files to read first.
- Output files expected.
- Guardrails and non-goals.
- Acceptance criteria to satisfy.
- Automated verification instructions where possible.
- Manual smoke-test instructions to include in the worker's final response.
- Instruction to keep work local unless explicitly asked otherwise.
- Instruction not to publish, commit, or close anything.
- Instruction not to use unsupported public claims.
- Instruction to ask/research first when the issue depends on personal judgment, current market information, or unclear strategy.
- Instruction to use placeholders only for small missing facts, not for major positioning decisions that need user input.

Prompt mode guidance:

- For artifact-production tasks, ask the worker to create/update the file and flag open questions.
- For strategic tasks, ask the worker to start by reviewing sources, surfacing options/tradeoffs, and asking concise questions before finalizing.
- For research tasks, require current research where information may have changed, and require source links in the output.
- For future dashboard/Notion tasks, ask the worker to design around the proven workflow, not imagined productivity features.

## Model Selection Guidance

Default to the cheapest/smallest model that can do the issue well. Use higher models only when the task needs judgment, current research synthesis, or careful review across many files.

Recommended pattern:

- Simple local Markdown synthesis/scaffolding: `GPT-5.3-Codex-Spark`, reasoning `medium` or `high`.
- Dense career/story/positioning writing: `GPT-5.4`, reasoning `high`.
- Current market research, target-role strategy, CV/LinkedIn positioning, or ambiguous human-judgment tasks: `GPT-5.4` or `GPT-5.5`, reasoning `high`.
- Difficult review, course correction, or high-stakes final positioning: `GPT-5.5`, reasoning `high` or `xhigh`.
- Routine formatting or tracker-template work: `GPT-5.3-Codex-Spark`, reasoning `medium`.

Avoid `xhigh` for simple artifact generation. Save it for ambiguity, final reviews, and decisions where a bad direction would waste time.

Default worker final response requirement:

```text
When done, give a concise summary with bullet points. Include:
- files changed
- what was completed
- verification/tests run
- manual verification steps for the human
- any open questions or placeholders
```

## Review Criteria

For every issue review, check:

- Does the artifact exist?
- Does it satisfy the issue acceptance criteria?
- Does it use the user's actual context rather than generic career advice?
- Does it avoid overclaiming?
- Does it preserve RDrive confidentiality boundaries?
- Does it use the standard answer structure where appropriate?
- Does it avoid passive-resource collecting?
- Does it create a usable artifact, not just planning noise?
- Does it respect local-first workflow?
- Does it avoid starting the Notion/dashboard/app too early?

For docs/workflow issues, automated validation may include:

- `Test-Path` for expected files.
- `rg` for required sections/phrases.
- line/heading checks.
- checking no accidental sensitive strings or unsupported claims are introduced.
- checking links/paths are plausible.

For code-backed issues later, require proper build/test commands in the relevant repo. Do not accept "manual only" when automated tests can cover the bulk of behavior.

## Core Communication Framework

For project, design, and business-impact answers, default to:

```text
Problem -> Constraint -> Decision -> Tradeoff -> Result
```

Optional additions:

- Alternatives considered.
- Failure mode.
- What I would improve now.
- Business impact.

Use STAR only when a behavioral people/process question calls for it.

## Strong Current Positioning

Candidate positioning:

> Full-stack .NET/Nuxt engineer with real ownership of integration-heavy SaaS and document/data workflow systems, now packaging that experience into a more conventional hiring story.

Shorter pattern:

> I build configurable integration systems that connect external platforms, move documents/data reliably, and turn messy business workflows into software.

RefineBridge pattern:

> I build reliable SaaS workflows where billing, credits, third-party APIs, background jobs, and customer-facing dashboards all need to work together.

Snagr/RDrive safe employment framing:

> Long-term independent developer/contractor for Snagr/RDrive, owning integration-heavy product work across RDrive and external enterprise platforms.

## Important Claim Boundaries

Use confidently:

- Built and owned major parts of RDrive DataBridge.
- Worked long-term for Snagr/RDrive in an independent developer/contractor style.
- Delivered core integrations for Aconex, Azure Blob Storage, Autodesk, and Asite.
- Built Form Events and Synchronization-style workflows.
- Built/configured admin UI, background operations, provider credentials/options, mappings, and sync status concepts as supported by notes/evidence.
- Refactored from Aconex-specific uploader toward configurable vendor pipeline.

Use cautiously:

- "Main engineer behind the platform" is acceptable where context supports it, but avoid implying sole company-wide product ownership beyond engineering.
- Public product page validates product positioning, not necessarily user adoption or every listed connector.

Do not claim unless later evidence confirms:

- Implemented SharePoint.
- Implemented 4Projects.
- Owned sales/marketing.
- Controlled client adoption.
- Had many users.
- Formal employment status if the arrangement was informal.

Privacy:

- Do not publish raw RDrive screenshots.
- Do not expose client names, IDs, usernames, roles, or live-system access details.
- Use sanitized descriptions for public-facing artifacts.

## Learning Areas To Preserve

Do not lose these areas while working through the backlog:

- Hiring funnel: CV, LinkedIn, target roles, applications, outreach, tracker.
- Interview mechanics: recruiter screen, behavioral, project walkthrough, coding, system design.
- Practical .NET: ASP.NET Core, EF Core/Postgres, background jobs, webhooks, validation, auth, testing.
- Architecture: modular monolith, DDD-informed boundaries, idempotency, retries, auditability, observability, tradeoffs.
- Integrations: external APIs, auth, rate limits, metadata mapping, folder hierarchies, provider quirks.
- Reliability: debugging, runbooks, partial failure, retries, job state, logs, support visibility.
- Security: auth/account boundaries, secrets/API keys, webhook trust, OWASP API risks, PII/logging.
- Frontend: Nuxt/Vue 3, TypeScript, forms, state, auth flows, loading/error states.
- Communication: concise explanation, business impact, stakeholder language, estimation under uncertainty.
- Networking/mentorship: ADPList, MentorCruise/Codementor, .NET community, founder/SaaS community.
- Sales/customer discovery: The Mom Test, Jonathan Stark/Brennan Dunn/patio11-style thinking, RefineBridge user conversations.
- AI-assisted practice: Codex as repo-aware interviewer, reviewer, and weak-spot tracker.

## Potential Missing Or Underweighted Items

The current PRD/backlog covers the major themes, but future work should watch these areas:

- CV and LinkedIn need personal facts later: exact dates, location preference, contact info, links, education, citizenship/right-to-work constraints, and preferred salary/rate.
- Role targeting needs current web research when executed; do not rely on stale assumptions.
- Timezone/location strategy matters because user is in Thailand and may target UK, Europe, remote worldwide, or Thailand-friendly remote.
- Portfolio/GitHub public visibility has not been fully planned. Some projects may be private, so public proof may need sanitized case studies rather than code.
- Compensation/rate strategy is mentioned but not yet a concrete artifact.
- Interview logistics are not yet modeled: calendar availability, camera/audio setup, remote interview environment, coding setup, and note-taking.
- Teamwork/collaboration concerns need careful story handling because user has worked mostly solo.
- Gaps in formal team process may need explicit mitigation stories: code review, testing discipline, feedback-seeking, documentation, and willingness to work in a team.
- Burnout/growth-path story should be honest but not negative.
- RefineBridge customer-discovery track should not drift into more building without user conversations.
- Speaking confidence needs reps, not only resources: recorded answers, mock calls, mentor calls, and possibly Toastmasters-style practice.
- Some issues should be treated as collaborative discovery sessions, not implementation tickets. The user expects back-and-forth where needed.
- A Notion tracker is likely useful later, but should come after the workflow shape is validated manually.

## Notion/Dashboard Timing

The user is interested in a Notion tracker eventually. Do not build it too early.

Recommended trigger:

- Build the first Notion/dashboard version after the manual Markdown workflow has been used for 2-4 weeks, or after the first diagnostic sprint plus at least one market-feedback loop.

Minimum evidence before building:

- CV/LinkedIn/target-role artifacts exist.
- At least a few practice-log entries exist.
- At least one Codex interview session has been run.
- Weak spots have been scored and revised.
- The user has enough repeated fields to know what a dashboard should track.
- Pain points in the Markdown workflow are visible.

Likely dashboard shape:

- Home view: this week's focus, top weak spots, next actions.
- Learning trees/subskills.
- Practice log.
- Weak spots.
- Resources.
- Artifacts.
- Interview sessions/question bank/answer library.
- Applications and market feedback.
- Mentor/feedback log.
- Weekly review.

Avoid building a dashboard to feel organized. Build it only when it reduces friction in an already-running system.

## Suggested Skills For Future Sessions

Use these skills when relevant:

- `to-issues` only if the backlog needs to be split further.
- `handoff` when compacting or transferring context.
- `grill-me` for live interview/grilling sessions.
- `grill-with-docs` if interview practice should update docs as answers improve.
- `notion:*` skills only if the user explicitly asks to create/use Notion.
- `browser:control-in-app-browser` only for local app/frontend verification.

## Current Status

Completed:

- Central PRD created.
- Local issue backlog created.
- CRI-001 positioning artifact created and approved.
- RDrive DataBridge story and evidence captured.
- Resource map captured.
- Hayk-style curriculum captured.
- Modern .NET interview readiness map captured.
- Codex interviewer system designed.

Not yet completed:

- CV draft.
- LinkedIn draft.
- Target-role matrix.
- Application tracker.
- First diagnostic interview session.
- Weak-spot tracker/practice log.
- First market test.

Recommended next orchestration action:

- Review CRI-003 when the worker completes `cv-draft.md`.
