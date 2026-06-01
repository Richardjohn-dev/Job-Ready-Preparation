# Hayk-Style Senior Developer Curriculum

Current as of 2026-05-30.

This is not a recommendation to buy Dev Mastery. It is a reverse-engineered curriculum from Hayk Simonyan's public writing, course pages, and positioning.

## Core Thesis

The repeated message is:

> Companies pay more for engineers who can design systems, make tradeoffs, communicate business impact, and position their experience clearly. Coding alone is not the differentiator.

For your situation, this is more relevant than heavy LeetCode grinding.

## What He Appears To Teach

### 1. Technical Foundation Audit

Purpose: find gaps that a senior/full-stack engineer is expected to own.

Topics:

- Stack depth: .NET, Nuxt/Vue, TypeScript, PostgreSQL, deployment, background jobs.
- Clean code and design patterns where they solve real problems.
- Engineering principles: SOLID, DRY, KISS, cohesion, coupling, boundaries.
- Testing: unit, integration, end-to-end, performance/load testing.
- Debugging and failure investigation.

Your application:

- Audit RefineBridge and RDrive DataBridge by subsystem.
- For each subsystem, write what you understand confidently, what is fuzzy, and what would fail under pressure.

Deliverable:

- `technical-gap-audit.md`

### 2. Production Architecture And System Design

Purpose: learn to explain how systems work, scale, fail, and recover.

Topics:

- Single-server setup and request flow.
- DNS, HTTP/HTTPS, TCP/UDP, WebSockets.
- API design: REST, GraphQL, gRPC, contracts, status codes, versioning, error handling.
- Database selection: SQL, NoSQL, Redis/key-value, object storage.
- Transactions, ACID, consistency, isolation, concurrency.
- Caching and CDNs.
- Reverse proxies and load balancers.
- Health checks, redundancy, single points of failure.
- Background jobs, queues, async workflows.
- Replication, sharding, read/write scaling.
- Monitoring, logging, alerting.
- CI/CD and production deployment.

Your application:

- Use RefineBridge and RDrive DataBridge as the main case studies.
- Explain one subsystem per week: billing, credits, sync jobs, auth, integrations, admin, deployment, document metadata mapping, and bi-directional file sync.

Deliverable:

- `refinebridge-system-design-case-study.md`

### 3. Architectural Decision-Making

Purpose: sound senior by showing judgment, not by naming tools.

Practice every design choice with:

1. Problem
2. Constraint
3. Decision
4. Tradeoff
5. Result

Optional follow-ups:

- Alternatives considered
- Failure mode
- Business impact

Examples:

- Why Hangfire/background processing instead of request-bound sync execution?
- Why PostgreSQL for core data?
- Why BYOK plus managed credits?
- Why webhook-driven billing state?
- Why admin approval?
- Why current deployment setup?
- Why a configurable pipeline instead of hardcoded per-customer document workflows?
- Why the RDrive DataBridge architecture had to evolve as Aconex, Azure Blob, Autodesk, and Asite were added?

Deliverable:

- 10 architectural decision records, short format.

### 4. Business Impact Communication

Purpose: translate "I built/fixed X" into "I reduced risk/cost/friction or increased reliability/revenue."

Template:

```text
Problem: [business/user/technical pain]
Constraint: [what made it non-trivial]
Decision: [what you chose to build/change]
Tradeoff: [what you accepted, rejected, simplified, or deferred]
Result: [risk reduced, workflow improved, cost controlled, revenue protected, support burden reduced]
```

Weak:

> I added background jobs.

Stronger:

> I moved long-running CRM/source syncs out of the request lifecycle using background jobs, so user-facing requests stayed responsive while integrations could retry and report status reliably.

Deliverable:

- 20 business-impact bullets from RefineBridge and RDrive DataBridge.

### 5. Interview Performance Without LeetCode Grind

Purpose: prepare for practical senior/full-stack roles, not algorithm-heavy big-tech loops.

Do:

- Practical coding exercises in .NET/TypeScript.
- Debugging exercises.
- API design exercises.
- Database/query/modeling exercises.
- Take-home style feature slices.
- System design explanations.
- Behavioral/project storytelling.

Keep only a small DSA baseline:

- Arrays/lists, dictionaries/maps, sets.
- Sorting/searching.
- Basic recursion.
- Trees at recognition level.
- Big-O vocabulary.

Skip for now:

- Months of LeetCode grinding.
- Dynamic programming.
- Graph-heavy interview prep.
- FAANG-specific optimization unless target roles require it.

Deliverable:

- 12 practical interview drills.

### 6. Positioning And Market Readiness

Purpose: make the market understand your value before the call.

Topics:

- LinkedIn/resume story, not tool list.
- Senior/full-stack positioning.
- Remote/SaaS/product engineering positioning.
- Recruiter call narrative.
- Salary/offer confidence.
- Avoiding weak signals such as desperation positioning.

Possible positioning:

> Full-stack .NET/Nuxt developer building production SaaS systems with billing, background jobs, third-party integrations, admin workflows, and CRM automation.

Sharper positioning:

> I build reliable SaaS workflows where billing, credits, third-party APIs, background jobs, and customer-facing dashboards all need to work together.

Deliverable:

- Resume bullets, LinkedIn summary, and 30-second intro.

### 7. AI As A Practical Edge

Purpose: use AI as production leverage, not hype.

Topics:

- AI-assisted development workflow.
- Prompting for engineering tasks.
- Using agents with repo context.
- RAG basics.
- MCP/tool integrations.
- AI feature design with failure modes and cost control.

Your application:

- Use AI to inspect RefineBridge/RDrive DataBridge notes, generate test ideas, review architecture, and rehearse interview answers.
- Later, build an interview-practice skill that asks about your own project decisions.

Deliverable:

- Small internal AI-assisted interview coach prototype.

## Suggested 12-Week Version

### Weeks 1-2: Audit And Position

- Write technical gap audit.
- Write 30-second intro.
- Rewrite 10 feature bullets into business-impact bullets.
- Pick target role types: practical .NET/full-stack/SaaS roles first.

### Weeks 3-4: System Foundations

- Study/request flow, APIs, databases, caching, load balancing, async jobs.
- Map each concept to RefineBridge and RDrive DataBridge.
- Explain one subsystem aloud twice per week.

### Weeks 5-6: RefineBridge Case Studies

- Billing/webhooks case study.
- Credit/BYOK case study.
- Background jobs/sync reliability case study.
- Auth/account/tenant model case study.
- RDrive DataBridge configurable pipeline case study.
- RDrive DataBridge enterprise integration evolution case study.

### Weeks 7-8: Practical Interview Drills

- Build or modify small .NET API feature.
- Debug a broken integration.
- Design database tables/indexes for a feature.
- Explain tradeoffs while coding.

### Weeks 9-10: Mock Interviews And Feedback

- One system-design mock using RefineBridge.
- One behavioral/project mock.
- One practical coding/debugging mock.
- Get feedback on clarity, concision, and seniority.

### Weeks 11-12: Market Package

- Resume and LinkedIn.
- Portfolio/project case studies.
- Recruiter screen script.
- Salary expectations and negotiation notes.
- Decide whether to start applications, continue SaaS push, or do both.

## Weekly Practice Loop

Minimum loop:

- 1 system-design explanation.
- 1 practical coding/debugging drill.
- 2 business-impact rewrites.
- 1 recorded interview answer.
- 1 mentor/peer/external feedback action.

## Source Notes

Public sources reviewed:

- Hayk Simonyan Medium profile and recent article list.
- Dev Mastery landing page.
- Senior Software Engineer Roadmap 2026.
- System Design Explained article/course summaries.
- Udemy course page for System Design for Beginners.
- Skool listing for Dev Mastery price signal.
- LinkedIn public profile/posts.
