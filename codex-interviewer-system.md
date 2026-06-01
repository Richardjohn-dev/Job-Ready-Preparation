# Codex Interviewer System

Current as of 2026-05-31.

Purpose: use Codex as a repo-aware interviewer that can inspect your projects, ask realistic questions, expose weak spots, and turn answers into better interview stories.

This should become the active practice layer on top of the roadmap.

This is a v0 design, not a rigid process. The question patterns and answer shapes are starting points pulled from earlier conversations. Keep refining them based on what produces better answers, clearer thinking, and more confidence under pressure.

## Core Idea

Instead of only studying generic interview material, use your real projects as the source of questions.

Codex can:

- Read the current project directory.
- Inspect code, docs, tests, migrations, configs, and architecture notes.
- Ask questions based on real implementation choices.
- Simulate interviewer pressure.
- Score your answers.
- Suggest a stronger answer.
- Save weak spots and improved stories back into this roadmap.

The point is not to memorize perfect answers. The point is to build the muscle of explaining real engineering decisions clearly.

## Session Types

### 1. Project Walkthrough Interview

Goal: explain a project at different levels.

Use for:

- 30-second intro.
- 2-minute project overview.
- Product/business explanation.
- Technical architecture walkthrough.
- "Tell me about a complex project you owned."

Codex behavior:

- Read relevant docs/code first.
- Ask one question at a time.
- Push for business impact and clarity.
- Stop rambling.
- Produce a tighter answer.

Example questions:

- What problem does this product solve?
- Who is the user?
- What workflow existed before this?
- What are the main system components?
- What did you personally own?
- What was technically hardest?
- What would you redesign now?

### 2. Architecture And Tradeoff Grill

Goal: defend design decisions like a senior engineer.

Use for:

- System design interviews.
- Architecture review practice.
- Mentor/code review prep.
- Finding fuzzy areas.

Codex behavior:

- Inspect the codebase or notes.
- Ask one design question at a time.
- Follow up until the tradeoff is clear.
- Ask about failure modes, alternatives, and business impact.
- Provide a recommended answer after your attempt.

Example questions:

- Why did you choose Hangfire instead of running this work inside HTTP requests?
- Why a modular monolith instead of microservices?
- Why PostgreSQL for core data?
- Where does idempotency matter?
- Which operations need auditability?
- What happens if a provider API is down for 2 hours?
- What happens if the same webhook arrives twice?
- What parts of the system need strong transactional consistency?
- What parts can be eventually consistent?
- Which data should never be logged?
- Where are the account/tenant boundaries enforced?
- What is the riskiest coupling in this subsystem?
- What would you extract first if the system grew?

### 3. Behavioral / Story Simulator

Goal: build clear stories for common behavioral questions.

Use for:

- Recruiter screens.
- Behavioral interviews.
- Engineering manager rounds.
- Explaining solo work without sounding isolated or apologetic.

Codex behavior:

- Ask a common behavioral question.
- Let you answer.
- Score primarily for `Problem -> Constraint -> Decision -> Tradeoff -> Result`.
- Use STAR/CAR only when the interviewer explicitly asks for a people/process story.
- Push for clearer result, tradeoff, conflict, or learning.
- Save improved version to story bank.

Example questions:

- Tell me about a time you changed product direction.
- Tell me about a time requirements were ambiguous.
- Tell me about a time you had to estimate uncertain work.
- Tell me about a time you disagreed with a stakeholder.
- Tell me about a time you refactored a system while it was still growing.
- Tell me about a time you handled a production risk.
- Tell me about a time you learned a new technology under delivery pressure.
- Tell me about a time a project did not get the adoption you expected.
- Tell me about a time you worked mostly alone and how you managed risk.
- Tell me about burnout or a difficult career decision.

### 4. Reliability / Debugging Interview

Goal: practice mature debugging and operational thinking.

Use for:

- "How would you debug this?"
- Production incident stories.
- Reliability/system design interviews.
- Showing ownership beyond feature work.

Codex behavior:

- Pick a real subsystem.
- Invent a plausible production failure.
- Ask you to diagnose it.
- Push on logs, reproduction, isolation, rollback, data repair, and regression tests.

Example questions:

- A sync job is marked successful but no records appear in GoHighLevel. What do you check?
- A Lemon Squeezy webhook failed halfway through. What state can be inconsistent?
- A customer says their credits were consumed but the provider task failed. What now?
- A Hangfire job retries repeatedly and creates duplicates. How do you prevent that?
- A provider starts rate-limiting imports. How should the system degrade?
- An RDrive DataBridge sync created folders but missed some documents. How would you investigate?
- Autodesk changes download behavior late in integration. How do you manage scope and risk?

### 5. Business / Stakeholder Interview

Goal: translate engineering work into business value.

Use for:

- Hiring manager interviews.
- Product/startup roles.
- SaaS demos.
- Consulting positioning.

Codex behavior:

- Ask what a business person would care about.
- Push for cost, risk, revenue, time, support burden, compliance, and user workflow.
- Rewrite technical answers into impact language.

Example questions:

- Why did this feature matter commercially?
- What risk did it reduce?
- What manual work did it remove?
- What would happen if this failed silently?
- How would you explain this to a non-technical manager?
- How would you justify spending two months on a provider integration?
- What scope cut would you offer if the business needed something sooner?

### 6. Code-Backed Interview

Goal: make Codex ask questions from actual code, not memory.

Use for:

- RefineBridge.
- RDrive DataBridge.
- Any future portfolio/project repo.

Codex behavior:

- Read project docs first.
- Search code for modules, jobs, webhooks, auth, billing, sync, tests.
- Pick one real implementation choice.
- Ask you to explain it.
- If you answer incorrectly, show the relevant code and correct the model.

Example prompt:

```text
Use the Codex interviewer workflow.
Project: F:\Projects\Repos\Private\Scraper-To-CRM
Mode: architecture grill
Target role: senior .NET/full-stack SaaS engineer
Read the relevant docs/code first.
Ask one question at a time.
After I answer, score it and give a stronger version.
Track weak spots but do not edit files until the session ends.
```

## Recommended Session Flow

Each session should be short.

Default: 25-45 minutes.

Flow:

1. Pick session type.
2. Pick project: RefineBridge or RDrive DataBridge.
3. Codex inspects relevant context.
4. Codex asks one question.
5. You answer naturally.
6. Codex scores answer.
7. Codex asks one follow-up.
8. Codex gives recommended answer.
9. Repeat 3-5 questions.
10. End with weak spots and next practice.

## Scoring Rubric

Score each answer 0-4.

```text
0 = missing / confused / not answerable yet
1 = technically partial, unclear, or too rambling
2 = basically correct but weak structure or missing tradeoffs
3 = solid interview answer with clear problem, decision, and result
4 = strong senior answer: concise, business-aware, technically accurate, tradeoffs and failure modes included
```

Score dimensions:

- Clarity.
- Technical accuracy.
- Business impact.
- Tradeoff awareness.
- Failure-mode awareness.
- Concision.
- Ownership.
- Evidence from real project.

## Answer Shape

For project/design questions:

```text
Problem:
Constraint:
Decision:
Tradeoff:
Result:
```

Optional additions only when useful:

```text
Failure mode:
What I would improve now:
```

For behavioral questions when STAR is useful:

```text
Situation:
Task:
Action:
Result:
Learning:
```

For debugging questions:

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

## Initial Question Bank

### RefineBridge

Architecture:

- Why Hangfire?
- Why not run provider syncs in the request lifecycle?
- Why Nuxt/Vue 3 for the frontend?
- Why .NET for the backend?
- Why PostgreSQL?
- Why a modular monolith?
- Where are the module boundaries?
- What does "DDD-informed" mean in this codebase?
- Where do you use strong domain types instead of primitives?
- What would you split out first if the system grew?

Billing and credits:

- How do Lemon Squeezy webhooks affect account access?
- What happens if a billing webhook is delayed or duplicated?
- Why have managed credits and BYOK?
- How do credits protect provider costs?
- What should happen if a task fails after credits are reserved or consumed?
- What needs auditability in the billing/credit flow?

Integrations:

- How does Outscraper data flow into GoHighLevel?
- Where do mapping, tagging, pipeline assignment, and retries live?
- How do you handle rate limits?
- How do you avoid duplicate CRM records?
- What should be logged for support?
- What should not be logged for security/privacy?

Security and tenancy:

- Where are account boundaries enforced?
- What can an admin do that a normal user cannot?
- How are external API keys/secrets protected?
- What are the abuse risks?
- How would you threat-model BYOK?

Operations:

- What are the key production failure modes?
- What would you monitor first?
- How would you debug a failed sync?
- What runbooks should exist?
- What backup/restore risk matters most?

Product direction:

- Tell me about a time you changed product direction in RefineBridge.
- What did you learn from moving from a SaaS template toward a specific product?
- What feature did you delay or cut?
- What did customer/market uncertainty change?
- How do you decide between building infrastructure and talking to users?

### RDrive DataBridge

Architecture:

- How did the system evolve from an Aconex uploader into a generic pipeline?
- What concepts became reusable?
- What remained vendor-specific?
- Why were Form Events and Synchronization separate but composable?
- Where did strategies or vendor capability models help?
- What would you design differently now?

Form Events:

- Explain the flow from RDrive/Azure form event to provider upload.
- How did form/status mapping work?
- How did users configure destination rules?
- What metadata was extracted or mapped?
- What could fail silently if not handled?

Synchronization:

- Explain provider-to-RDrive synchronization.
- How did synchronization locations work?
- How did metadata become folder hierarchy?
- How did users filter provider documents?
- What happened with thousands of documents?

Provider complexity:

- Why was "just implement the interface" an oversimplification?
- What made Autodesk harder late in the project?
- How did chunked downloads affect scope?
- How did folder permissions affect implementation?
- How should unknown provider behavior affect estimates?

Stakeholder communication:

- How would you explain a two-month estimate to a developer manager?
- How would you explain it to a business stakeholder?
- What scope cuts could you offer?
- What did you learn from solo ownership?

## Session Output Template

At the end of a session, Codex should produce:

```text
Session:
Date:
Project:
Mode:
Questions asked:

Scores:
- Question 1:
- Question 2:
- Question 3:

Top weak spots:
- ...

Best improved answer:
...

Next practice:
- ...

Artifacts to update:
- experience-story-bank.md
- learning-system-plan.md
- project-specific case study
```

## Dashboard Fit

When this becomes a Notion dashboard, add these databases:

Interview Sessions:

- Date.
- Project.
- Mode.
- Duration.
- Score average.
- Weak spots.
- Linked questions.
- Linked artifacts.

Question Bank:

- Question.
- Project.
- Category.
- Difficulty.
- Last asked.
- Current answer score.
- Improved answer link.

Weak Spots:

- Weak spot.
- Evidence.
- Severity.
- Related questions.
- Next drill.
- Recheck date.

Answer Library:

- Question.
- Draft answer.
- Improved answer.
- Source project.
- STAR/design/debug format.
- Feedback.

## First 10 Sessions

Use this order:

1. RDrive DataBridge 30-second/project walkthrough.
2. RefineBridge 30-second/project walkthrough.
3. RefineBridge Hangfire/background jobs architecture grill.
4. RDrive Form Events explanation drill.
5. RDrive Synchronization explanation drill.
6. RefineBridge billing/webhook/credits reliability grill.
7. Behavioral: changed product direction.
8. Behavioral: ambiguous requirements and estimation.
9. Debugging: failed sync/job incident.
10. System design: RefineBridge end-to-end architecture.

## Rule

Every interview session must produce one artifact:

- A better answer.
- A weak-spot note.
- A case-study bullet.
- An ADR.
- A runbook.
- A practice-log entry.

No passive sessions.
