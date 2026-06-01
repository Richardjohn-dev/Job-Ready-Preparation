# Interview And Options Roadmap

Current as of 2026-05-30.

## North Star

Build optionality.

The goal is not "job instead of SaaS" or "SaaS instead of job." The goal is to become harder to knock off balance:

- Able to interview without panic.
- Able to explain technical work in business terms.
- Able to use RefineBridge as evidence of senior/full-stack ability.
- Able to build SaaS/customer/outreach skill without betting everything on it.
- Able to develop a small network outside solo work.

## Current Read

Strong assets:

- Real SaaS/product experience, not tutorial work.
- Multi-year commercial integration-platform experience from RDrive DataBridge.
- Public product-page validation: RDrive has a dedicated RDrive Data Bridge page describing the product as a central push/pull data integration platform.
- Solo ownership of ambiguous business requests from Snagr Software, including delivery across Aconex, Azure Blob Storage, Autodesk, and Asite.
- Full-stack .NET/Nuxt/Postgres architecture experience.
- Clear technical progression: first large SPA/Vue/Vuetify product on DataBridge, now Nuxt/Vue 3 with .NET, PostgreSQL, modular monolith structure, and DDD-ish boundaries in RefineBridge.
- Auth, billing, webhooks, background jobs, integrations, admin flows, deployment, and operational concerns.
- Enough runway to prepare strategically.
- Clear awareness that high-ticket coaching often repackages learnable skills.

Likely gaps:

- Formal interview mechanics.
- Talking while coding.
- Turning solo project work into concise interview stories.
- Explaining business impact instead of only technical implementation.
- Making invisible engineering complexity visible to stakeholders before estimates cause friction.
- System-design presentation under time pressure.
- Explaining architecture without buzzwords: modular monolith, DDD-ish boundaries, and functional design need concrete examples from RefineBridge.
- Network, mentors, and external feedback loops.
- Sales/discovery reps with actual customers or agencies.
- Framing the non-standard Snagr work history clearly without sounding apologetic.

## Time Split

Default weekly split:

| Area | Share | Why |
| --- | ---: | --- |
| RefineBridge/product/customer work | 45% | Long-term owned asset and strongest proof of ability. |
| Interview/job readiness | 30% | Insurance, confidence, and near-term income optionality. |
| Communication/business/sales skill | 15% | Helps interviews, SaaS demos, consulting, and networking. |
| Network/mentorship | 10% | Reduces isolation and creates feedback/opportunities. |

Adjustments:

- If actively applying: job readiness goes to 40%, RefineBridge drops to 35%.
- If RefineBridge gets strong traction: product/customer work goes to 60%, interview readiness stays at maintenance level.
- If confidence is low: increase mocks and speaking practice before adding more courses.

## Six-Month Roadmap

### Phase 1: Foundation And Positioning, Weeks 1-4

Outcome: understand the interview game and define your professional story.

- Write a one-paragraph positioning statement.
- Create 6-8 RefineBridge case-study bullets.
- Learn basic interview flow: recruiter screen, technical screen, coding round, system design, behavioral, offer.
- Start NeetCode-style pattern practice, mostly easy problems.
- Record 5-minute explanations of RefineBridge features.
- Book 1-2 mentor or peer feedback calls.

Definition of done:

- You can explain "what I build" in 30 seconds.
- You can explain 3 RefineBridge or RDrive DataBridge features as business outcomes.
- You have started solving problems out loud, even awkwardly.

### Phase 2: Technical Interview Basics, Weeks 5-8

Outcome: remove fear around coding interviews.

- Practice arrays, hash maps, two pointers, sliding window, stacks, queues, binary search, trees basics.
- Do 3-4 coding problems per week.
- For each problem, practice: clarify, propose approach, code, test, discuss complexity.
- Start one practical .NET exercise per week.
- Draft 4 STAR stories from RefineBridge and RDrive DataBridge.

Definition of done:

- 30-40 total problems solved or reviewed deeply.
- You can talk through simple problems without going silent.
- You have 4 stories ready: technical challenge, failure/risk, tradeoff, ownership.

### Phase 3: System Design From Your Own Work, Weeks 9-12

Outcome: turn RefineBridge into your main system-design training ground.

- Create a high-level RefineBridge architecture diagram.
- Practice explaining requirements, constraints, data model, async work, retries, idempotency, rate limits, security, billing, and failure modes.
- Do one 30-45 minute system-design explanation each week.
- Rewrite resume/LinkedIn around outcomes and ownership.
- Do first mock interview, even if rough.

Definition of done:

- You can whiteboard RefineBridge or RDrive DataBridge from memory.
- You can explain why key tradeoffs were made.
- You have a resume/profile draft that sounds commercially useful, not just technical.

### Phase 4: Feedback And Calibration, Weeks 13-16

Outcome: get outside signal.

- Do 2-4 mock interviews.
- Get resume/profile reviewed by someone who hires or mentors engineers.
- Do 2-3 customer/agency discovery calls for RefineBridge.
- Start light applications or recruiter conversations if the job path feels active.
- Continue coding practice at maintenance pace.

Definition of done:

- You know your top 3 interview weaknesses from real feedback.
- You have heard real objections or interest from target users.
- You know whether job search, SaaS, or consulting deserves more time next.

### Phase 5: Active Market Reps, Weeks 17-24

Outcome: enter the market from a position of practice, not panic.

- Apply selectively to .NET/full-stack/SaaS/product engineering roles.
- Keep 5-10 interview processes moving if actively searching.
- Continue RefineBridge outreach and demos.
- Do one mock or real interview debrief each week.
- Start salary/offer prep before offers appear.

Definition of done:

- You are either interviewing seriously, validating RefineBridge seriously, or both.
- You can explain your experience clearly under pressure.
- You have enough data to choose: job, consulting bridge, SaaS push, or hybrid.

## Weekly Operating Rhythm

Minimum useful week:

- 3 coding interview sessions.
- 1 RefineBridge or RDrive DataBridge case-study/portfolio improvement.
- 1 business-impact rewrite.
- 1 outreach/networking action.
- 1 recorded explanation or mock answer.

Example week:

| Day | Main work |
| --- | --- |
| Monday | Coding pattern practice + explain solution out loud. |
| Tuesday | RefineBridge product/customer work. |
| Wednesday | System-design practice using RefineBridge. |
| Thursday | Resume/story/business-impact rewrite. |
| Friday | Networking, mentor call, or mock interview. |
| Saturday | RefineBridge build/outreach block. |
| Sunday | Weekly review and next-week priorities. |

## Communication Framework

Use this when explaining any project, feature, bug, or architecture choice:

1. Problem: what business/user/technical problem existed?
2. Constraint: what made it non-trivial?
3. Decision: what did you choose to design or implement?
4. Tradeoff: what did that decision cost, simplify, or rule out?
5. Result: what risk, cost, time, friction, revenue, or support burden changed?

Weak answer:

> I fixed a billing bug.

Stronger answer:

> I fixed a billing-state issue where provider cancellations could leave access out of sync with payment state. The business risk was either giving unpaid access or blocking paying users. I tightened webhook-driven state transitions and added tests around cancellation and upgrade flows.

## Experience Story Bank

Use both major projects:

- RDrive DataBridge: long-term commercial integration-platform ownership.
- RefineBridge: current SaaS/product ownership and modern stack.

Supporting note:

- `rdrive-databridge-code-evidence.md` captures concrete code-backed details from `F:\Projects\SnagR\RDrive-Aconex-Integrator`.
- `rdrive-databridge-explanation-cheatsheet.md` captures the short spoken explanation to rehearse.
- `stakeholder-communication-lessons.md` captures the estimation/hidden-complexity lesson from working solo.

The pattern:

> You build configurable integration systems that connect external platforms, move documents/data reliably, and turn messy business workflows into software.

For RDrive DataBridge specifically:

> Form Events pushed RDrive form packages out to providers. Synchronization pulled existing provider document libraries back into RDrive and organized them with metadata-driven folder paths.

They could also be composed:

> Upload matching forms to provider folder `XYZ`, then scheduled-sync `XYZ` back into a selected RDrive project every few hours.

## RefineBridge Story Bank

Initial stories to prepare:

- Billing and Lemon Squeezy webhooks: revenue access, state sync, cancellation risk.
- Credit system: provider-cost control, onboarding friction, monetization.
- BYOK feature: premium feature design, user flexibility, margin protection.
- Hangfire/background jobs: long-running sync reliability outside request lifecycle.
- Outscraper to GoHighLevel integration: customer workflow automation.
- Admin approval/moderation: abuse prevention and infrastructure protection.
- Backup/restore/deployment: operational risk reduction.
- Auth/tenant/account model: security, ownership, and SaaS account boundaries.

## RDrive DataBridge Story Bank

Initial stories to prepare:

- Configurable integration pipeline: business users define document/data sync rules.
- Aconex integration: document upload, metadata mapping, status-driven workflow.
- Azure Blob integration: storage sync and file movement.
- Autodesk integration: platform-specific API adaptation.
- Asite integration: adding a new destination after architecture had already evolved.
- Form Events: RDrive form/status events pushed files and metadata out to providers.
- Synchronization: external provider documents synced back into RDrive project hierarchy.
- Dynamic synchronization locations: provider metadata used to create RDrive folder paths.
- Composable workflow: event upload to provider folder plus scheduled synchronization back into RDrive.
- Metadata extraction/mapping: attached PDF metadata applied to destination uploads.
- Evolving architecture: moving from one integration to a reusable pattern across four platforms.
- Solo ownership: receiving broad business requests and turning them into shipped systems.
- Burnout/growth-path lesson: why you now want optionality, network, and fallback paths.

## Resource Stack

Use cheap/free first. Pay only when you need feedback, not motivation.

Interview mechanics and coding:

- NeetCode roadmap for pattern-based coding practice.
- Cracking the Coding Interview for process and fundamentals.
- interviewing.io later for realistic mock interviews.

System design:

- DesignGurus/Grokking-style material for interview framing.
- Your own RefineBridge architecture as the main case study.

Business/sales/consulting:

- Jonathan Stark for value pricing and escaping hourly commodity thinking.
- Brennan Dunn/Double Your Freelancing for positioning, proposals, and freelancing.
- Patrick McKenzie/patio11 for software business, salary negotiation, and consulting essays.
- The Mom Test for customer discovery.

Mentorship/network:

- ADPList for free career perspective calls.
- MentorCruise or Codementor for paid targeted feedback.
- One founder/SaaS community only at first.
- One .NET/software community only at first.

Avoid for now:

- High-ticket identity-transformation cohorts.
- More than one paid course at once.
- Passive binge-watching without producing an artifact.
- FAANG-style grind as the main plan unless that becomes the explicit target.

## Paid Help Filter

Pay only if the offer gives direct feedback on your actual bottleneck.

Good paid help:

- Mock interviews with detailed feedback.
- Resume/LinkedIn review from someone who hires engineers.
- System-design review of RefineBridge.
- Mentor who understands .NET/SaaS/product engineering.
- Sales/discovery coach who reviews your actual calls/scripts.

Bad paid help:

- Generic "become senior" motivation.
- Vague community access.
- Secret-framework promises.
- No public price and high-pressure sales call.
- Advice that ignores your existing SaaS/product work.

## Future Skill Idea

Later, build an interview-practice assistant that does this:

- Reads a project/codebase.
- Picks one design choice.
- Asks you to explain it.
- Pushes on tradeoffs, failure modes, business impact, and alternatives.
- Scores the answer on clarity, seniority, business relevance, and concision.
- Saves improved answer versions into a story bank.

Do this after the basic roadmap and story bank exist. The skill will be much better if it has your actual positioning, project stories, and target roles to train against.
