# Codex Interviewer Workflow

Current as of 2026-06-02.

Purpose: operating workflow for Codex-assisted interview preparation. This prepares future practice sessions; it must not run or fake the live diagnostic interview deferred to GitHub issue #12.

Default answer structure:

```text
Problem -> Constraint -> Decision -> Tradeoff -> Result
```

Use STAR only for behavioral questions where the interviewer asks for people/process detail. Use debugging format for incident-style questions.

## Operating Rules

- Ask one interview question at a time.
- Do not invent Richard's answers.
- Do not run a diagnostic interview unless the user explicitly asks for issue #12 or live practice.
- Prefer local evidence over memory.
- Mark unsupported claims as `needs confirmation`.
- Keep public claims conservative.
- End every practice session with weak spots, improved answer draft, and artifact updates to make later.

## Source Files To Inspect First

Default career context:
- `master-career-inventory.md`
- `positioning-v1.md`
- `cv-draft.md`
- `behavioral-story-bank.md`

RDrive DataBridge:
- `experience-story-bank.md`
- `rdrive-databridge-case-study.md`
- `stakeholder-communication-lessons.md`
- `rdrive-databridge-code-evidence.md` when code-backed detail is needed

RefineBridge:
- `refinebridge-case-study.md`
- RefineBridge repo only when the user provides or confirms the path

Roadmap/control:
- `github-issue-map.md`
- `handoff-career-readiness-orchestrator.md`
- `career-readiness-local-issues.md` only when lower-level CRI detail is needed

## When To Ask, Inspect, Or Defer

Ask Richard when:
- The missing fact is personal, subjective, or legally sensitive.
- Exact dates, titles, role wording, or comfort level are needed.
- A story depends on a real conversation, conflict, mistake, or emotion.
- A result needs a metric, before/after example, or permission boundary.
- RefineBridge feature status is unclear and repo inspection cannot confirm intent or public safety.

Inspect local files/repos when:
- The question asks about architecture, code structure, workflows, tests, migrations, configs, or implementation status.
- A claim can be checked against local case studies or code evidence.
- A stronger answer needs concrete implementation detail.
- The user asks for code-backed interview practice.

Defer when:
- Evidence is missing and guessing would create a false claim.
- The request would expose private RDrive/client/customer data.
- A live diagnostic interview is being implied during issue #5 work.
- Current market facts are needed and no current research has been requested or allowed.

Output phrasing for deferral:

```text
Evidence gap: I cannot safely turn this into an interview claim yet.
Needed next: [specific file/repo check or question for Richard].
Safe fallback: [bounded wording that can be used now].
```

## Session Modes

### Mode 1: Project Walkthrough

Use for:
- 30-second project intro.
- 2-minute project explanation.
- "Tell me about a complex project you owned."
- Recruiter or hiring-manager project questions.

Prompt:

```text
Use the Codex interviewer workflow.
Mode: project walkthrough.
Project: [RDrive DataBridge / RefineBridge].
Target role: [role].
Read the relevant local files first.
Ask one question at a time.
Score my answer using Problem -> Constraint -> Decision -> Tradeoff -> Result.
Do not edit files until the session ends.
```

### Mode 2: Architecture And Tradeoff Grill

Use for:
- Senior engineering judgment.
- System-design/project-defense practice.
- Tradeoff clarity.
- Failure-mode and alternative-design questions.

Prompt:

```text
Use the Codex interviewer workflow.
Mode: architecture and tradeoff grill.
Project: [project].
Target role: [role].
Inspect local docs/code before asking.
Ask one design question, wait for my answer, then score and follow up.
Push on alternatives, failure modes, operational impact, and business value.
```

### Mode 3: Behavioral Story Simulator

Use for:
- Ambiguity.
- Estimation.
- Refactoring.
- Solo ownership.
- Learning under pressure.
- Product underuse.
- Changed direction.
- Burnout/growth path.

Prompt:

```text
Use the Codex interviewer workflow.
Mode: behavioral story simulator.
Story source: behavioral-story-bank.md.
Pick one scaffold or ask me which one to practice.
Ask one behavioral question.
Score primarily on Problem -> Constraint -> Decision -> Tradeoff -> Result.
After my answer, identify missing evidence and draft a stronger version.
```

### Mode 4: Reliability / Debugging Interview

Use for:
- Failed sync/job scenarios.
- Webhook and billing failure modes.
- Provider API failures.
- Operational visibility and recovery.

Prompt:

```text
Use the Codex interviewer workflow.
Mode: reliability/debugging.
Project: [RDrive DataBridge / RefineBridge].
Inspect relevant evidence first.
Give one plausible incident scenario.
Ask me to diagnose it.
Score on risk identification, first checks, hypotheses, isolation, fix/rollback, regression prevention, and communication.
```

Debugging answer format:

```text
Symptom:
Immediate risk:
First checks:
Hypotheses:
Isolation steps:
Fix/rollback:
Regression prevention:
Communication:
```

### Mode 5: Stakeholder / Business Translation

Use for:
- Explaining technical value to non-technical people.
- Estimate defense.
- Scope cuts.
- Business-impact framing.

Prompt:

```text
Use the Codex interviewer workflow.
Mode: stakeholder/business translation.
Topic: [estimate / integration value / reliability / product workflow].
Ask one manager-style question.
After my answer, rewrite it for a developer manager and a business stakeholder.
Keep claims evidence-safe.
```

### Mode 6: Code-Backed Interview

Use for:
- Repo-aware explanations.
- Correcting memory against code.
- Technical deep dives grounded in implementation.

Prompt:

```text
Use the Codex interviewer workflow.
Mode: code-backed interview.
Project repo: [path].
Read docs first, then inspect only relevant code.
Pick one real implementation choice and ask me to explain it.
If my answer conflicts with code, show the evidence and correct the answer.
Track weak spots but do not edit files until the session ends.
```

## Scoring Rubric

Score each answer 0-4.

```text
0 = missing, confused, unsafe, or not answerable from evidence yet
1 = partial answer; unclear, rambling, or mostly unsupported
2 = basically correct but weak structure, weak result, or missing tradeoff
3 = solid interview answer with clear problem, decision, tradeoff, and result
4 = strong senior answer: concise, evidence-backed, business-aware, technically accurate, and clear about tradeoffs/failure modes
```

Score dimensions:
- Clarity.
- Technical accuracy.
- Evidence support.
- Business impact.
- Tradeoff awareness.
- Failure-mode awareness.
- Concision.
- Ownership without overclaiming.
- Privacy/claim safety.

Scoring output:

```text
Score:
Reason:
Strongest part:
Weakest part:
Missing evidence:
One follow-up question:
Stronger answer draft:
```

## Output Template

Use at the end of any real practice session:

```text
Session:
Date:
Project:
Mode:
Target role:

Questions asked:
- ...

Scores:
- Q1:
- Q2:
- Q3:

Best answer draft:
Problem:
Constraint:
Decision:
Tradeoff:
Result:

Weak spots:
- ...

Missing evidence:
- ...

Claim/privacy risks:
- ...

Recommended artifact updates:
- behavioral-story-bank.md:
- experience-story-bank.md:
- project case study:
- learning/practice log:

Next practice:
- ...
```

## Privacy Boundaries

Never include publicly:
- Raw RDrive screenshots.
- Live system URLs.
- Client/project names, IDs, usernames, roles, account details, credentials, tenant data, or customer document metadata.
- Private commercial terms or internal stakeholder conflict details.

Avoid unsupported claims:
- SharePoint implementation.
- 4Projects implementation.
- Sales, marketing, adoption, revenue, user count, or traction claims.
- Formal employee status unless confirmed.
- Team lead, hiring, or management authority unless confirmed.
- RefineBridge production/customer/billing/provider implementation status unless repo or Richard confirms it.

Safe public framing:
- RDrive DataBridge as a configurable two-way integration platform.
- Implemented providers limited to Aconex, Azure Blob Storage, Autodesk, and Asite.
- Long-term independent developer/contractor-style work for Snagr/RDrive.
- RefineBridge as a modern .NET/Nuxt/PostgreSQL product/SaaS proof point, with implementation details verified before use.

## Readiness Checklist Before A Live Session

- Target role selected for the session.
- Project selected: RDrive DataBridge or RefineBridge.
- Session mode selected.
- Relevant local files read.
- Claim boundaries reviewed.
- Story scaffold selected or question bank selected.
- Missing-info checklist checked.
- User confirms this is a live practice session, not issue #5 framework work.
- Output destination decided: no edits until session ends unless the user asks.

## Missing-Info Checklist

Ask or verify before turning placeholders into final answers:
- Exact Snagr/RDrive date range.
- Preferred public role/title wording.
- Formal employment vs independent/contractor wording.
- Safe location/timezone wording.
- Whether any safe metrics exist.
- Which RDrive screenshots can be redacted.
- Which RDrive providers beyond Aconex, Azure Blob Storage, Autodesk, and Asite are truly implemented, if any.
- One concrete DataBridge origin story.
- One concrete stakeholder estimation story.
- One concrete refactor example.
- One collaboration/feedback example.
- One Vue/Vuetify learning-under-pressure example.
- RefineBridge repo path.
- RefineBridge implemented vs planned feature list.
- RefineBridge canonical workflow and target user.
- RefineBridge changed-direction/product-underuse evidence.
- Burnout/growth-path wording Richard is comfortable saying out loud.

## Recommended Order For Issue #12 Diagnostic Interview

Issue #12 should run the first live diagnostic interview after this framework is reviewed.

Recommended order:
1. Start with RDrive DataBridge 30-second walkthrough to anchor the strongest commercial case study.
2. Ask one follow-up on Form Events or Synchronization.
3. Ask one estimation/stakeholder question using the Autodesk complexity story.
4. Ask one solo ownership/team-readiness question.
5. Ask one RefineBridge modern-stack question, but keep implementation claims cautious.
6. End with burnout/growth path only if Richard is comfortable and has selected the preferred wording.
7. Produce the session output template.
8. Update story scaffolds only after Richard's real answers exist.

Do not do in issue #12's first diagnostic:
- Drill every story.
- Turn RefineBridge into a traction story.
- Ask deeply personal burnout questions without consent.
- Publish or sanitize screenshots during the session.
- Close issue #5 retroactively from inside the diagnostic.

## Initial Question Bank

Behavioral:
- Tell me about a time requirements were ambiguous.
- Tell me about a time you had to estimate uncertain work.
- Tell me about a time you refactored a system while it was still growing.
- Tell me about a time you worked mostly alone and how you managed risk.
- Tell me about a time you learned a new technology under delivery pressure.
- Tell me about a time a product or feature did not get the adoption you expected.
- Tell me about a time you changed product direction.
- Tell me about burnout or a difficult career decision.

RDrive DataBridge:
- Explain RDrive DataBridge in 30 seconds.
- Explain Form Events from RDrive event to provider upload.
- Explain Synchronization from provider document library to RDrive folder hierarchy.
- Why were Form Events and Synchronization separate but composable?
- How did the system evolve from Aconex-specific to reusable?
- What made Autodesk harder than expected?
- What would you design differently now?

RefineBridge:
- Explain RefineBridge without overclaiming traction.
- Why use .NET, Nuxt/Vue 3, and PostgreSQL?
- Which workflow is the safest public demo story?
- What feature status needs repo confirmation?
- How do billing, webhooks, credits, background jobs, and admin views shape the architecture?
- How do you decide between building more infrastructure and talking to users?

Stakeholder/business:
- How would you explain a two-month provider estimate to a developer manager?
- How would you explain the same estimate to a business stakeholder?
- What scope cut would you offer if the business needed value sooner?
- What manual work or operational risk did DataBridge reduce?

Reliability/debugging:
- An RDrive DataBridge sync created folders but missed some documents. How would you investigate?
- A provider session expires halfway through a background job. What should happen?
- A webhook or job runs twice. How do you prevent duplicate side effects?
- A provider changes download behavior late in implementation. How do you manage scope and communication?

## Artifact Update Rules

After a real session:
- Update `behavioral-story-bank.md` only with Richard's real answers or confirmed facts.
- Update project case studies when a stronger explanation emerges.
- Add weak spots to the future practice log/tracker once issue #6 creates it.
- Keep speculative notes labeled.
- Do not mark GitHub issues complete, close issues, or commit unless the user explicitly asks.
