# Developer Career Resource Map

Current as of 2026-05-30.

This is a resource map for building optionality: practical job readiness, stronger communication, SaaS/product skill, and enough network/feedback to stop working in isolation.

Bias: practical .NET/SaaS/product engineering roles first. Keep LeetCode-style prep light unless target companies explicitly require it.

## How To Use This

Do not collect resources. Use one primary resource per subcategory, then produce an artifact:

- A case study.
- A recorded explanation.
- A mock interview.
- A rewritten resume bullet.
- A small practical coding drill.
- A customer discovery script.
- A mentor feedback note.

If a resource does not lead to an artifact or rep, pause it.

## Parent Categories

| Parent category | What it develops | Main proof |
| --- | --- | --- |
| 1. Direction and market calibration | Knowing what roles to target and what the market values | Target-role matrix |
| 2. Practical interview performance | Passing realistic interviews without over-optimizing for algorithms | Mock feedback and drills |
| 3. System design and architecture | Explaining production systems, tradeoffs, and failure modes | RefineBridge and RDrive DataBridge case studies |
| 4. Production .NET/SaaS engineering | Sharpening the technical surface employers actually ask about | Improved project subsystems and notes |
| 5. Testing, debugging, and reliability | Showing mature engineering habits | Tests, runbooks, debugging stories |
| 6. Security, auth, and SaaS boundaries | Handling trust, access, tenancy, and abuse risk | Security/auth case study |
| 7. Communication and business impact | Explaining why work matters | Business-impact story bank |
| 8. SaaS, sales, and customer discovery | Building RefineBridge without guessing | Discovery notes and offer tests |
| 9. Networking and mentorship | Getting feedback and opportunities | Mentor calls and community reps |
| 10. AI-assisted engineering | Using AI as leverage, not theatre | Repeatable AI workflows |

## 1. Direction And Market Calibration

Goal: avoid preparing for an imaginary job market.

| Subcategory | Resources | What to do |
| --- | --- | --- |
| Target role definition | LinkedIn/Wellfound/remote job ads, company career pages | Collect 30 roles: .NET full-stack, SaaS/product engineer, integrations engineer, backend/platform engineer. Mark repeated requirements. |
| Seniority calibration | ADPList, MentorCruise, Codementor | Ask 3 people: "Where would you place me given RDrive DataBridge, RefineBridge, solo ownership, and limited formal team/interview exposure?" |
| Compensation/negotiation | Patrick McKenzie salary negotiation essays, levels.fyi where relevant | Write compensation target bands and negotiation principles before interviews. |
| Role fit decision | Your own RefineBridge roadmap | Decide whether each role supports stability, energy, remote work, and SaaS runway. |

Primary actions:

- Build `target-role-matrix.md`.
- Save 30 role links.
- Extract repeated requirements into "must have", "nice to have", "ignore for now".
- Talk to 3 mentors/reviewers.

Best resources:

- Free: ADPList mentor calls, job ads, Patrick McKenzie essays.
- Paid: MentorCruise or Codementor for targeted review.

## 2. Practical Interview Performance

Goal: become comfortable in interviews without turning the whole plan into LeetCode grinding.

| Subcategory | Resources | What to develop | Actions |
| --- | --- | --- | --- |
| Interview mechanics | Cracking the Coding Interview, interviewing.io blog/content, Exponent examples | Knowing format, pacing, expectations | Write a recruiter-screen script and technical-screen checklist. |
| Mock interviews | interviewing.io, Pramp, peers, Codementor | Performing under observation | Do 1 rough mock early, then 1 every 2-3 weeks. |
| Coding baseline | NeetCode roadmap, Exercism C# track | Basic data structures and problem talk-through | Keep to arrays, maps, sets, sorting, binary search, simple recursion, basic trees. |
| Practical coding | .NET API drills, TypeScript drills, take-home-style tasks | Realistic feature building | Build 12 small tasks: endpoint, validation, query, background job, webhook handler, bug fix. |
| Debugging interview skill | Existing RefineBridge/RDrive DataBridge bugs, broken sample apps | Investigating methodically | Practice "read logs, reproduce, isolate, hypothesize, test, fix, regression test." |

Recommended balance:

- 70% practical coding/debugging/design.
- 20% mock interview reps.
- 10% DSA baseline.

Avoid:

- Dynamic programming.
- Graph-heavy prep.
- 150+ problem grind.
- FAANG-specific preparation unless you decide that is the target.

## 3. System Design And Architecture

Goal: explain systems like someone who has owned production tradeoffs.

| Subcategory | Free resources | Paid/structured resources | Actions |
| --- | --- | --- | --- |
| General concepts | System Design Primer, ByteByteGo System Design 101, Hello Interview | DesignGurus/Grokking, Educative | Study APIs, DBs, caching, queues, load balancing, rate limits, reliability. Map every concept to RefineBridge and RDrive DataBridge. |
| .NET architecture | Microsoft .NET Architecture Guides, Microsoft eShop sample | Dometrain, Pluralsight, Milan Jovanovic courses/newsletter | Compare both projects with reference architectures; note what is intentionally simpler. |
| Architecture decisions | ADR examples, Martin Fowler articles | Mentor/code review | Write 10 short ADRs across RefineBridge and RDrive DataBridge choices. |
| Interview presentation | Hello Interview, DesignGurus, interviewing.io mocks | Paid mock/system design session | Practice a 45-minute system design explanation for each major project. |

Best GitHub/repos:

- `donnemartin/system-design-primer`
- `ByteByteGoHq/system-design-101`
- Microsoft `eShop`
- Jason Taylor `CleanArchitecture`

RefineBridge case studies to write:

- Billing/webhooks/access state.
- Credit/BYOK cost-control model.
- Background sync pipeline.
- CRM/source integration reliability.
- Auth/account/tenant model.
- Admin/moderation and abuse prevention.

RDrive DataBridge case studies to write:

- Configurable document/data integration pipeline.
- Aconex upload and metadata mapping workflow.
- Azure Blob storage sync.
- Autodesk and Asite integration differences.
- Bi-directional file sync back into RDrive project hierarchy.
- Evolving architecture as four integrations were added over several years.

## 4. Production .NET/SaaS Engineering

Goal: strengthen the exact technical areas your target roles will value.

| Subcategory | Resources | What to develop | Actions |
| --- | --- | --- | --- |
| ASP.NET Core APIs | Microsoft Learn ASP.NET Core docs | Routing, validation, auth, DI, middleware, filters, error handling | Review one API area weekly and improve one endpoint or note one tradeoff. |
| EF Core/Postgres/data modeling | Microsoft EF Core docs, PostgreSQL docs | Queries, indexes, transactions, migrations, concurrency | Write one data-modeling case study from RefineBridge. |
| Background jobs | Hangfire docs, Microsoft hosted services docs | Retries, idempotency, job status, failure recovery | Write "how sync jobs run and fail" explanations for RefineBridge and RDrive DataBridge. |
| Billing/webhooks | Lemon Squeezy docs, Stripe docs for general webhook patterns | State machines, idempotency, event ordering, access control | Write billing-state diagram and failure cases. |
| Integrations | WorkOS docs, GHL/Outscraper docs, API docs generally | OAuth/API keys, rate limits, retries, mapping, audit logs | Write integration failure-mode checklist. |
| Frontend product UI | Nuxt docs, Vue docs, Frontend Masters/Vue Mastery | State, forms, data fetching, auth flows, error states | Audit one user workflow end-to-end. |

YouTubers/newsletters worth sampling:

- Milan Jovanovic: .NET architecture, clean architecture, modular monoliths, pragmatic backend design.
- Nick Chapsas/Dometrain: modern C#/.NET, performance, libraries, practical courses.
- IAmTimCorey: approachable C#/.NET explanations.
- Raw Coding: .NET internals and practical backend topics.
- Microsoft .NET channel: official ecosystem updates.

Rule:

- Watch only when solving a real weakness. Then apply it to RefineBridge or RDrive DataBridge that week.

## 5. Testing, Debugging, Reliability

Goal: show mature engineering, not just feature output.

| Subcategory | Resources | What to develop | Actions |
| --- | --- | --- | --- |
| Unit/integration tests | Microsoft ASP.NET Core integration testing docs, xUnit docs | Test seams, fixtures, database tests, API tests | Add or document one test strategy per subsystem. |
| E2E/browser testing | Playwright docs | User-flow verification | Pick 3 critical flows: signup/billing, bridge setup, sync run. |
| Load/performance testing | k6 docs, BenchmarkDotNet docs | Throughput, latency, bottlenecks, measurement | Run one small load test or benchmark on a realistic endpoint/job. |
| Observability | OpenTelemetry docs, Microsoft logging docs | Logs, metrics, traces, correlation IDs | Write a "how I would debug production sync failure" runbook. |
| Incident/debug stories | Your own bug history | Reproduction, isolation, fix, regression tests | Turn 3 bugs from either RefineBridge or RDrive DataBridge into interview stories. |

Interview angle:

> Reliability stories are often stronger than shiny feature stories because they prove ownership.

## 6. Security, Auth, And SaaS Boundaries

Goal: talk credibly about trust, access, tenancy, and abuse risk.

| Subcategory | Resources | What to develop | Actions |
| --- | --- | --- | --- |
| Web/app risks | OWASP Top 10, OWASP API Security Top 10 | Injection, broken auth, access control, SSRF, logging | Map Top 10 risks to RefineBridge. |
| ASP.NET auth | Microsoft ASP.NET Core security docs | AuthN/AuthZ, policies, cookies/tokens, claims | Explain your auth model and authorization boundaries. |
| Identity/SaaS auth | WorkOS docs | Organizations, roles, SSO/SAML concepts, lifecycle | Write auth/tenant/account case study. |
| Secrets/API keys | Cloud provider docs, 12-factor app | Secret storage, rotation, BYOK risks | Write BYOK threat model. |
| Billing/security overlap | Stripe/Lemon Squeezy webhook docs | Signature verification, replay, idempotency | Explain webhook trust and failure handling. |

Deliverables:

- `refinebridge-security-case-study.md`
- `byok-threat-model.md`

## 7. Communication And Business Impact

Goal: stop sounding like "I completed tasks"; sound like someone who understands cost, risk, revenue, and users.

| Subcategory | Resources | What to develop | Actions |
| --- | --- | --- | --- |
| Business impact translation | Hayk-style public content, Patrick McKenzie essays, HBR-style business writing | Turning features into value | Rewrite 20 bullets using cost/risk/time/revenue/friction language across both major projects. |
| Structured answers | STAR/CAR formats, Manager Tools behavioral prep, Exponent examples | Concise stories | Build 8 STAR stories from RefineBridge and RDrive DataBridge. |
| Executive communication | Pyramid Principle, Think Fast Talk Smart | Answer-first, concise reasoning | Practice 2-minute answers: conclusion first, then evidence. |
| Speaking confidence | Think Fast Talk Smart, Toastmasters, recordings | Clear verbal reps | Record one answer per week; critique for rambling and jargon. |
| Technical writing | RefineBridge/RDrive DataBridge case studies, ADRs | Clear written artifacts | Publish private case studies first; public later if useful. |

Business-impact template:

```text
Problem: [business/user/technical pain]
Constraint: [what made it non-trivial]
Decision: [what you chose to build/change]
Tradeoff: [what you accepted, rejected, simplified, or deferred]
Result: [risk reduced, workflow improved, cost controlled, revenue protected, support burden reduced]
```

Practice prompts:

- Why did this feature matter?
- What could have gone wrong?
- What tradeoff did you make?
- What would a non-technical stakeholder care about?
- How would you explain it in 60 seconds?

## 8. SaaS, Sales, And Customer Discovery

Goal: keep RefineBridge moving toward market evidence, not just internal polish.

| Subcategory | Resources | What to develop | Actions |
| --- | --- | --- | --- |
| Customer discovery | The Mom Test, YC Startup School | Asking non-leading questions | Talk to 20 target users/agencies. Track pains, current workflow, urgency, budget, objections. |
| Offer design | Alex Hormozi $100M Offers, Brennan Dunn | Packaging value clearly | Write 3 versions of the RefineBridge offer. |
| Consulting/pricing | Jonathan Stark, Brennan Dunn, Patrick McKenzie | Value pricing, avoiding hourly commodity positioning | Draft consulting bridge offers related to integrations/automation. |
| SaaS founder context | Indie Hackers, MicroConf, YC library | Patterns and cautionary tales | Join one community only; post one specific question/update per week. |
| Demo/sales calls | Gong/Lenny-style SaaS sales content, founder demos | Discovery before pitching | Create call script and objection log. |

Actions:

- Create `customer-discovery-notes.md`.
- Do 20 conversations before making large product bets.
- Track exact words users use.
- Convert repeated pain into landing-page/resume/business-impact language.

## 9. Networking And Mentorship

Goal: stop preparing alone.

| Subcategory | Resources | What to do |
| --- | --- | --- |
| Free mentorship | ADPList | Book 3 calls: senior engineer, engineering manager, founder/product person. |
| Paid targeted feedback | MentorCruise, Codementor | Pay for specific reviews: resume, system design, codebase, mock interview. |
| .NET community | .NET Discords, .NET Thailand, Microsoft events, local/regional meetups | Lurk briefly, then ask one concrete question or share one artifact. |
| Founder/product community | Indie Hackers, MicroConf, relevant LinkedIn/X circles | One community only at first. Post specific progress, not vague motivation. |
| Interview practice network | Pramp, peers, interviewing.io | Create recurring mock/interview feedback reps. |

Good mentor request:

> Can you review how I am presenting RDrive DataBridge and RefineBridge as senior/full-stack integration/SaaS experience and point out what would concern you in an interview?

Bad mentor request:

> Can you mentor me?

## 10. AI-Assisted Engineering

Goal: use AI to increase engineering output and communication quality.

| Subcategory | Resources | What to develop | Actions |
| --- | --- | --- | --- |
| Prompting/workflow | OpenAI docs, Anthropic docs, GitHub Copilot docs | Clear task framing, review loops, context control | Save prompts that produce useful code review, tests, and explanations. |
| Codebase agents | Codex, repo-aware assistants, MCP docs | Let tools inspect real code safely | Build repeatable workflows: bug diagnosis, test generation, architecture review. |
| AI product basics | OpenAI/Anthropic docs, RAG articles, MCP docs | Model limits, retrieval, tool use, evals, cost | Build small interview-practice assistant later. |
| AI communication coach | Your own transcripts and story bank | Answer critique, clearer wording | Have AI challenge your explanations and score for clarity/business impact. |

Deliverable:

- `interview-practice-skill-spec.md`

Later skill idea:

- Reads RefineBridge/RDrive DataBridge project context.
- Picks a design choice.
- Asks you to explain it.
- Pushes on tradeoffs, failure modes, business value, and alternatives.
- Saves improved answers to the story bank.

## Priority Stack

### Start Now

1. Target-role matrix from 30 job ads.
2. Experience story bank with 8 stories across RDrive DataBridge and RefineBridge.
3. System-design case studies for RDrive DataBridge and RefineBridge.
4. 12 practical interview drills.
5. 3 mentor/feedback calls.

### Add After 4-6 Weeks

1. Paid mock interview.
2. Resume/LinkedIn review.
3. System-design review with mentor.
4. Customer discovery calls.
5. One founder or .NET community.

### Delay

1. Expensive cohort programs.
2. Multiple paid courses at once.
3. Heavy LeetCode grind.
4. Public content/personal brand work before your private story bank is solid.

## Resource Comparison Shortlist

| Need | Best free/cheap first | Paid only if needed |
| --- | --- | --- |
| Learn system design basics | System Design Primer, ByteByteGo 101, Hello Interview | DesignGurus/Educative |
| Learn .NET architecture | Microsoft .NET architecture guides, eShop, Milan Jovanovic free content | Dometrain, Pluralsight, Milan courses |
| Practice interviews | Pramp, peers, recorded self-practice | interviewing.io, Codementor |
| Improve coding confidence | Exercism, practical drills, NeetCode basics | NeetCode premium, targeted tutor |
| Improve business communication | Patrick McKenzie, Think Fast Talk Smart, your own rewrites | Exponent, coach/mentor |
| Learn customer discovery | The Mom Test, YC content | founder coach only after real calls |
| Learn pricing/consulting | Jonathan Stark, Brennan Dunn, Patrick McKenzie | Double Your Freelancing paid material |
| Build network | ADPList, communities, local meetups | MentorCruise |

## Source Links

- System Design Primer: https://github.com/donnemartin/system-design-primer
- ByteByteGo System Design 101: https://github.com/ByteByteGoHq/system-design-101
- Microsoft .NET Architecture Guides: https://learn.microsoft.com/en-us/dotnet/architecture/
- Microsoft ASP.NET Core integration testing: https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests
- Docker Getting Started: https://docs.docker.com/get-started/
- OWASP Top 10: https://owasp.org/www-project-top-ten/
- Nuxt Docs: https://nuxt.com/docs/getting-started/introduction
- Hangfire Docs: https://docs.hangfire.io/en/latest/
- NeetCode Roadmap: https://neetcode.io/roadmap
- ADPList Software Engineering Mentors: https://adplist.org/mentors/expertise/software-engineering
- The Mom Test: https://www.momtestbook.com/
- Jonathan Stark: https://jonathanstark.com/
- Brennan Dunn / Double Your Freelancing: https://doubleyourfreelancing.com/
- Patrick McKenzie greatest hits: https://www.kalzumeus.com/greatest-hits/
- Think Fast Talk Smart: https://www.fastersmarter.io/
- OpenAI Prompt Engineering: https://platform.openai.com/docs/guides/prompt-engineering
