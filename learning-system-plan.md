# Learning System Plan

Current as of 2026-05-31.

Purpose: find weak spots, work them systematically, and avoid turning preparation into passive course collecting.

## Current Decision

Do not build a full Notion dashboard yet.

First build the operating model:

- What skills matter.
- How weak spots are detected.
- What actions improve each skill.
- What resources belong to each skill.
- How progress is logged.
- What evidence proves progress.

Once this is stable, a Notion dashboard becomes useful. Before that, it risks becoming organisation work instead of preparation.

The existing conversation notes are seed material, not final doctrine. Use them to generate experiments, question banks, resources, and practice loops. Keep anything that improves real interview/product confidence; discard anything that becomes busywork.

## Design Principle

This system should behave like a feedback loop:

```text
Diagnose weak spot
  -> pick one focused practice action
  -> produce an artifact
  -> get feedback or self-score
  -> update weak-spot score
  -> choose the next action
```

The dashboard, if built later, should only make that loop easier to run.

## North Star

Build optionality:

- Explain past work clearly.
- Pass practical .NET/full-stack/SaaS interviews.
- Present architecture and tradeoffs calmly.
- Keep RefineBridge moving as proof of product ability.
- Get outside feedback instead of preparing alone.

## Learning Trees

### 1. Direction And Market Calibration

Skill: know which roles to target and what the market actually asks for.

Subskills:

- Target role definition.
- Seniority calibration.
- Repeated requirement extraction.
- Compensation and offer expectations.
- Deciding when to apply versus keep preparing.

Actions:

- Collect 30 job ads for .NET/full-stack/SaaS/integrations/backend roles.
- Extract repeated requirements into `must have`, `nice to have`, and `ignore for now`.
- Book 3 feedback calls with engineers/managers/founders.
- Write a target-role matrix.

Evidence:

- `target-role-matrix.md`
- 30 saved role links.
- 3 feedback notes.
- Clear target role list.

### 2. Story, Communication, And Business Impact

Skill: explain your experience in language employers and business people understand.

Subskills:

- 30-second intro.
- RDrive DataBridge explanation.
- RefineBridge explanation.
- STAR stories.
- Business-impact bullets.
- Stakeholder/estimation communication.
- Non-standard Snagr work-history framing.

Actions:

- Record 2-5 minute answers.
- Rewrite technical bullets into business-impact bullets.
- Practice explaining one feature at product, engineering, and stakeholder levels.
- Use the standard answer shape: `Problem -> Constraint -> Decision -> Tradeoff -> Result`.
- Get mentor/peer feedback on clarity.

Evidence:

- 8 polished STAR stories.
- 20 business-impact bullets.
- Recorded answers with improved second versions.
- Resume/LinkedIn draft.

### 3. Practical Interview Coding

Skill: solve realistic coding/debugging tasks while explaining your thinking.

Subskills:

- Basic DSA baseline: arrays, maps, sets, sorting, binary search, simple recursion, basic trees.
- Practical .NET API tasks.
- TypeScript/Vue/Nuxt tasks.
- Debugging broken code.
- Talking while coding.
- Testing what you write.

Actions:

- 2-3 short coding sessions per week.
- Keep LeetCode/NeetCode light and pattern-based.
- Add practical drills: endpoint, validation, query, webhook handler, background job, bug fix.
- Explain every solution aloud.

Evidence:

- 30-40 simple problems solved or reviewed deeply.
- 12 practical drills.
- 2 mock coding interviews.
- Notes on recurring mistakes.

### 4. System Design And Architecture

Skill: explain production systems, tradeoffs, and failure modes using your own projects.

Subskills:

- Requirements and constraints.
- API design.
- Data modeling.
- Background jobs.
- Integrations and external API failures.
- Idempotency, retries, rate limits.
- Auth/security boundaries.
- Billing/webhook state.
- Modular monolith and DDD-informed design.

Actions:

- Use RefineBridge as the main modern case study.
- Use RDrive DataBridge as the commercial integration-system case study.
- Write short ADRs.
- Practice 30-45 minute system-design explanations.

Evidence:

- RefineBridge architecture diagram.
- RDrive DataBridge architecture diagram.
- 10 short ADRs.
- 4 recorded system-design walkthroughs.
- Feedback from at least one experienced engineer.

### 5. Production .NET/SaaS Engineering

Skill: sharpen the technical surface target roles will care about.

Subskills:

- ASP.NET Core APIs.
- EF Core/Postgres.
- Background jobs.
- Webhooks.
- SaaS account/auth boundaries.
- Deployment and configuration.
- Logging and operational visibility.
- Frontend workflows in Nuxt/Vue 3.

Actions:

- Pick one subsystem per week.
- Review the implementation.
- Improve, test, or document one thing.
- Write one interview-ready explanation.

Evidence:

- Subsystem notes.
- Improved tests or implementation.
- Case studies for billing, credits, BYOK, background sync, auth, admin, integrations.

### 6. Testing, Debugging, And Reliability

Skill: show mature engineering habits, not just feature output.

Subskills:

- Unit tests.
- Integration tests.
- E2E/browser tests.
- Debugging method.
- Runbooks.
- Incident stories.
- Observability: logs, metrics, correlation IDs.

Actions:

- Turn 3 real bugs into interview stories.
- Write "how I would debug this in production" runbooks.
- Add or document tests around risky flows.
- Practice diagnosis out loud.

Evidence:

- 3 debugging stories.
- 3 runbooks.
- Test strategy notes.
- One mock debugging interview.

### 7. Product, SaaS, Sales, And Customer Discovery

Skill: keep RefineBridge tied to market reality.

Subskills:

- Customer discovery.
- Demo calls.
- Offer design.
- Objection handling.
- Pricing/positioning.
- Avoiding build-only mode.

Actions:

- Use The Mom Test style questions.
- Talk to 20 target users/agencies over time.
- Track exact words, pains, objections, current workflow, urgency, and budget.
- Rewrite RefineBridge positioning from real language.

Evidence:

- Discovery notes.
- Objection log.
- 3 offer versions.
- Demo script.
- Decision on product, consulting bridge, job search, or hybrid.

### 8. Network, Mentorship, And Feedback

Skill: stop calibrating alone.

Subskills:

- Asking specific mentor questions.
- Getting resume/profile feedback.
- Getting system-design feedback.
- Mock interviews.
- Community participation without distraction.

Actions:

- Book ADPList/mentor calls.
- Ask for narrow reviews, not vague mentorship.
- Join one .NET/software community and one founder/product community at most.
- Do one feedback action per week.

Evidence:

- Feedback notes.
- Mock interview reports.
- Updated resume/story artifacts.
- List of recurring concerns from other people.

### 9. AI-Assisted Engineering And Interview Practice

Skill: use AI as leverage for code, diagnosis, writing, and interview reps.

Subskills:

- Repo-aware code review.
- Test ideas.
- Architecture critique.
- Interview answer critique.
- Prompt reuse.
- Later: custom interview-practice assistant.

Actions:

- Save useful prompts/workflows.
- Have AI challenge one explanation per week.
- Use AI to generate practice questions from RefineBridge/RDrive DataBridge.

Evidence:

- Saved prompt/workflow library.
- Improved answers.
- Later: `interview-practice-skill-spec.md`.

## Weak-Spot Discovery

Use a simple score per subskill.

```text
0 = I do not know this / no reps.
1 = I understand it when reading, but cannot explain or do it cleanly.
2 = I can explain/do it slowly with notes.
3 = I can explain/do it without notes in a relaxed setting.
4 = I can handle it under interview pressure and have evidence/feedback.
```

Priority is highest when:

- The market asks for it often.
- Your score is 0-2.
- It makes you anxious.
- You have weak evidence.
- It blocks interviews, RefineBridge, or confidence.

Do not guess weak spots only from feelings. Use diagnostics:

- Record yourself.
- Do mocks.
- Ask mentors.
- Compare against job ads.
- Try practical drills.
- Review actual code.

## Practice Log

Track minutes, but only when paired with output.

Minimum log fields:

- Date.
- Learning tree.
- Subskill.
- Minutes.
- Activity type: study, build, explain, mock, rewrite, outreach, review.
- Resource used.
- Artifact produced.
- Confidence before/after.
- Next action.

Good log entry:

```text
2026-06-03
Tree: Story/Communication
Subskill: RDrive 30-second explanation
Minutes: 25
Activity: recorded answer + rewrite
Artifact: recording v2 + improved script
Confidence: 2 -> 3
Next: get feedback from mentor
```

Bad log entry:

```text
Watched videos for 2 hours.
```

## Future Notion Dashboard

Build this only after the workflow has been used manually for 2-4 weeks.

### Dashboard Sections

Home:

- This week's focus.
- High-level progress by learning tree.
- Top 5 weak spots.
- Practice minutes this week.
- Artifacts due.
- Next feedback action.

Learning Trees database:

- Tree.
- Subskill.
- Current score.
- Target score.
- Priority.
- Status.
- Primary resource.
- Next action.
- Linked artifacts.
- Linked practice logs.

Practice Log database:

- Date.
- Minutes.
- Tree/subskill.
- Activity type.
- Resource.
- Artifact.
- Confidence before/after.
- Notes.

Resources database:

- Resource name.
- Category.
- Cost.
- Link.
- Status: not started, active, paused, done.
- Why this resource.
- Artifact it should produce.

Artifacts database:

- Artifact name.
- Type: case study, ADR, mock report, recording, resume bullet, drill, runbook.
- Related tree.
- Status.
- Feedback received.
- Next revision.

Weak Spots database:

- Weak spot.
- Evidence.
- Severity.
- Related tree.
- Next diagnostic.
- Next practice action.
- Date rechecked.

Weekly Review:

- Minutes by tree.
- Artifacts produced.
- Feedback received.
- Weak spots improved.
- What to stop.
- Next week's focus.

## First Diagnostic Sprint

Do this before committing to a large roadmap.

Duration: 2 weeks.

Goal: find the real weak spots.

Actions:

- Collect 15-30 target job ads.
- Record 6 answers:
  - 30-second intro.
  - RDrive DataBridge explanation.
  - RefineBridge explanation.
  - One architecture/tradeoff answer.
  - One debugging/reliability answer.
  - One stakeholder/estimation answer.
- Do 4 practical coding/debugging drills.
- Write 5 business-impact bullets.
- Book 1 mentor/feedback call.
- Score every learning tree from 0-4.

Output:

- Top 5 weak spots.
- Top 3 strengths.
- 4-week focus plan.
- Decision on whether to start building the Notion dashboard.

## Current Best Next Step

Do the diagnostic sprint first.

The likely weak spots are already visible:

- Concise verbal explanation.
- Interview pressure.
- Business-impact framing.
- External feedback/network.
- Architecture explanation with concrete examples.

But the diagnostic sprint will separate real gaps from vague anxiety.
